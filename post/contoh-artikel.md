<!--
README singkat:
- Struktur blog Markdown
- Bisa langsung deploy ke Cloudflare Pages
- Sudah ada TOC otomatis
- Bisa tambah iklan melayang
-->

<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>{{ title }}</title>
  <meta name="description" content="{{ description }}" />
  <link rel="stylesheet" href="/style.css" />
</head>
<body>
  <header>
    <h1><a href="/">Blog Saya</a></h1>
  </header>

  <main>
    <article>
      <h1>{{ title }}</h1>
      <p><em>{{ pubDatetime }}</em></p>
      <div id="toc"></div>
      <div class="content">
        {{ content }}
      </div>
    </article>
  </main>

  <footer>
    <p>&copy; 2025 Blog Saya</p>
  </footer>

  <div id="ads-floating">
    <a href="#">Iklan Melayang</a>
  </div>

  <script>
    // TOC generator sederhana
    const content = document.querySelector('.content');
    const toc = document.querySelector('#toc');
    const headers = content.querySelectorAll('h2, h3');
    let tocHTML = '<strong>Daftar Isi:</strong><ul>';
    headers.forEach(h => {
      const id = h.textContent.replace(/\s+/g, '-').toLowerCase();
      h.id = id;
      tocHTML += `<li><a href="#${id}">${h.textContent}</a></li>`;
    });
    tocHTML += '</ul>';
    toc.innerHTML = tocHTML;
  </script>
</body>
</html>
