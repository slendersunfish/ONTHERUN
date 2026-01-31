 <!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Latest Voice Note</title>
  <style>
    body{font-family:system-ui,-apple-system,Segoe UI,Roboto,Arial;max-width:920px;margin:40px auto;padding:0 16px;line-height:1.55}
    header{display:flex;justify-content:space-between;align-items:baseline;gap:12px;flex-wrap:wrap}
    .muted{opacity:.7;font-size:.95rem}
    a{color:inherit}
    article{margin-top:16px;padding:18px;border:1px solid rgba(255,255,255,.14);border-radius:16px}
    pre{overflow:auto;padding:12px;border-radius:12px;background:rgba(255,255,255,.06)}
    code{font-family:ui-monospace,SFMono-Regular,Menlo,Monaco,Consolas,"Liberation Mono",monospace}
  </style>
</head>
<body>
  <header>
    <h1>Latest Voice Note</h1>
    <div class="muted"><a href="../index.html">Back</a></div>
  </header>

  <div class="muted" id="meta">Loading…</div>
  <article id="content">Please wait…</article>

  <script src="https://cdn.jsdelivr.net/npm/marked/marked.min.js"></script>
  <script>
    // cache-bust so you always see the latest note
    const bust = Date.now();
    fetch('./latest.md?v=' + bust, { cache: 'no-store' })
      .then(r => r.text())
      .then(md => {
        document.getElementById('content').innerHTML = marked.parse(md);
        document.getElementById('meta').textContent = "Updated: " + new Date().toLocaleString();
      })
      .catch(() => {
        document.getElementById('content').textContent = "Could not load latest.md";
        document.getElementById('meta').textContent = "";
      });
  </script>
</body>
</html>
