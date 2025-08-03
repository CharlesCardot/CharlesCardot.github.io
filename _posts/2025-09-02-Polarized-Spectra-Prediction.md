---
layout: post
title: Predicting Polarized Dependence in X-ray Spectra
subtitle: Work in progress
thumbnail-img: /img/posts/Images_LongShortPost/GLV_example_curves.png
tags: [Python, Machine Learning, Valence-to-Core XES]
use_math: true
---

Blah blah blah

<h3>Upload your data to predict spectral anisotropy</h3>

<form id="upload-form">
  <input type="file" id="datafile" name="datafile" accept=".cif,.xyz">
  <button type="submit">Submit</button>
</form>

<pre id="output"></pre>

<script>
document.getElementById("upload-form").addEventListener("submit", async function(event) {
  event.preventDefault();

  const fileInput = document.getElementById("datafile");
  const file = fileInput.files[0];
  if (!file) {
    alert("Please choose a file first.");
    return;
  }

  const maxSizeKB = 4;
  const maxSizeBytes = maxSizeKB * 1024;
  if (file.size > maxSizeBytes) {
    document.getElementById("output").textContent = `❌ File too large (max ${maxSizeKB} KB).`;
    return;
  }

  const reader = new FileReader();

  reader.onload = async function(e) {
    const content = e.target.result;
    const filename = file.name;

    const ntfyMessage = `📦 File received: ${filename}\n\n${content}`;

    try {
      const res = await fetch("https://ntfy.sh/polarized-xes-upload", {
        method: "POST",
        headers: { "Content-Type": "text/plain" },
        body: ntfyMessage
      });

      if (!res.ok) {
        throw new Error("ntfy error: " + res.statusText);
      }

      document.getElementById("output").textContent = "✅ File sent to ntfy!";
    } catch (err) {
      document.getElementById("output").textContent = "❌ Error: " + err.message;
    }
  };

  reader.onerror = function() {
    document.getElementById("output").textContent = "❌ Failed to read file.";
  };

  reader.readAsText(file);
});
</script>