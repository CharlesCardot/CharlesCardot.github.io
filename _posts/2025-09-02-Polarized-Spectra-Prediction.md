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
function generateTag(length = 8) {
  const chars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789';
  let tag = '';
  for (let i = 0; i < length; i++) {
    tag += chars.charAt(Math.floor(Math.random() * chars.length));
  }
  return tag;
}

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

    const tag = generateTag();
    const ntfyMessage = `🔖 Tag: ${tag}\n📦 File received: ${filename}\n\n${content}`;

    try {
      const res = await fetch("https://ntfy.sh/polarized-xes-upload", {
        method: "POST",
        headers: { "Content-Type": "text/plain" },
        body: ntfyMessage
      });

      if (!res.ok) {
        throw new Error("ntfy error: " + res.statusText);
      }

      document.getElementById("output").textContent = `✅ File sent with tag ${tag}! Waiting for response...`;

      // Start SSE listener for response
      listenForResponse(tag);
    } catch (err) {
      document.getElementById("output").textContent = "❌ Error: " + err.message;
    }
  };

  reader.onerror = function() {
    document.getElementById("output").textContent = "❌ Failed to read file.";
  };

  reader.readAsText(file);
});

function listenForResponse(tag) {
  const source = new EventSource("https://ntfy.sh/polarized-xes-response/sse");

  source.addEventListener("message", function(event) {
    const message = event.data;

    if (message.includes(`Tag: ${tag}`)) {
      document.getElementById("output").textContent = `📬 Response for tag ${tag}:\n\n${message}`;
      source.close();  // Stop listening after receiving the match
    }
  });

  source.addEventListener("error", function(err) {
    console.error("❌ SSE error:", err);
    source.close();
  });
}
</script>
