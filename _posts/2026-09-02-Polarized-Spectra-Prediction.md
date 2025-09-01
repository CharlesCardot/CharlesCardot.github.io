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
  <label for="oxidation-choice">Oxidation states:</label>
  <select id="oxidation-choice" name="oxidation-choice">
    <option value="guess">Let backend guess</option>
    <option value="define">I will define them</option>
  </select>
  
  <div id="oxidation-input-container" style="display: none; margin-top: 8px;">
    <label for="oxidation-input">Define oxidation states (e.g. Fe:3, O:-2):</label>
    <input type="text" id="oxidation-input" name="oxidation-input" placeholder="Fe:3, O:-2" style="width: 100%;">
  </div>
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

// Toggle visibility of input box
document.getElementById("oxidation-choice").addEventListener("change", function () {
  const container = document.getElementById("oxidation-input-container");
  container.style.display = this.value === "define" ? "block" : "none";
});

// Handle form submit
document.getElementById("upload-form").addEventListener("submit", async function(event) {
  event.preventDefault();

  const fileInput = document.getElementById("datafile");
  const file = fileInput.files[0];
  if (!file) {
    alert("Please choose a file first.");
    return;
  }

  const maxSizeKB = 4;
  const maxSizeBytes = maxSizeKB * 1000;
  if (file.size > maxSizeBytes) {
    document.getElementById("output").textContent = `❌ File too large (max ${maxSizeKB} Bytes).`;
    return;
  }

  const oxidationChoice = document.getElementById("oxidation-choice").value;
  let oxidationText = "guess";

  if (oxidationChoice === "define") {
    const definedStates = document.getElementById("oxidation-input").value.trim();
    oxidationText = definedStates || "define_selected_but_empty";
  }

  const reader = new FileReader();

  reader.onload = async function(e) {
    const content = e.target.result;
    const filename = file.name;

    const tag = generateTag();
    const ntfyMessage = `🔖 Tag: ${tag}\n⚙️ Oxidation states: ${oxidationText}\n📦 File received: ${filename}\n\n${content}`;

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
