<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>Website - Code Button</title>
  <style>
    body { font-family: system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial; padding: 2rem; background:#f7f7fb; color:#222 }
    .card { background: #fff; padding: 1.5rem; border-radius: 12px; box-shadow: 0 6px 18px rgba(33,33,33,0.06); max-width:720px; margin:auto }
    h1 { margin-top:0 }
    .controls { display:flex; gap:.5rem; margin-bottom:1rem }
    button { background:#0366d6; color:white; border:0; padding:.6rem .9rem; border-radius:8px; cursor:pointer; font-weight:600 }
    button.secondary { background:#efefef; color:#111 }
    pre { background:#0b1220; color:#d6deff; padding:1rem; border-radius:8px; overflow:auto }
    .hidden { display:none }
  </style>
</head>
<body>
  <div class="card">
    <h1>button jomokers</h1>
    <p>This page includes a button that shows/hides a code snippet and a copy-to-clipboard button.</p>

    <div class="controls">
      <button id="toggleBtn">Show code</button>
      <button id="copyBtn" class="secondary">Copy code</button>
    </div>

    <pre id="codeBlock" class="hidden"><code id="codeContent">&lt;!doctype html&gt;
&lt;html&gt;
  &lt;head&gt;
    &lt;meta charset="utf-8"/&gt;
    &lt;title&gt;Hello&lt;/title&gt;
  &lt;/head&gt;
  &lt;body&gt;
    &lt;h1&gt;Hello, world!&lt;/h1&gt;
  &lt;/body&gt;
&lt;/html&gt;
</code></pre>

    <p style="margin-top:.8rem; font-size:.9rem; color:#666">Tip: To publish this page with GitHub Pages, push to the repository's default branch (main). The Pages URL will be: <code>https://Matthiuw-zero.github.io/Website-/</code> once Pages is built.</p>
  </div>

  <script>
    const toggleBtn = document.getElementById('toggleBtn');
    const copyBtn = document.getElementById('copyBtn');
    const codeBlock = document.getElementById('codeBlock');
    const codeContent = document.getElementById('codeContent');

    toggleBtn.addEventListener('click', () => {
      const hidden = codeBlock.classList.toggle('hidden');
      toggleBtn.textContent = hidden ? 'Show code' : 'Hide code';
    });

    copyBtn.addEventListener('click', async () => {
      try {
        await navigator.clipboard.writeText(codeContent.textContent);
        copyBtn.textContent = 'Copied!';
        setTimeout(() => copyBtn.textContent = 'Copy code', 1600);
      } catch (e) {
        copyBtn.textContent = 'Copy failed';
        setTimeout(() => copyBtn.textContent = 'Copy code', 1600);
      }
    });
  </script>
</body>
</html>
