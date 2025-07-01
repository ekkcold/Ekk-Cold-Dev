<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Channel & Newsletter</title>
  <style>
    body { background: #121212; color: #fff; font-family: sans-serif; padding: 20px; }
    .card { background: #1f1f1f; border-radius: 8px; padding: 20px; margin-bottom: 15px; max-width: 400px; }
    img { width: 80px; height: 80px; border-radius: 50%; }
    button { margin: 10px 5px 0 0; padding: 8px 12px; border: none; border-radius: 5px; cursor: pointer; }
    .sub-btn { background: #e74c3c; color: #fff; }
    .news-btn { background: #3498db; color: #fff; }
  </style>
</head>
<body>
  <h1>Daftar Channel + Newsletter</h1>
  <div id="channel-list"></div>

  <script>
    const newsletterIds = [
      "120363400383798698@newsletter",
      "120363418115508098@newsletter",
      "120363402321770278@newsletter",
      "120363421243132029@newsletter"
    ];

    fetch('https://raw.githubusercontent.com/FirgaDev/Firga68/main/ChannelldSettings.json')
      .then(res => res.json())
      .then(data => {
        const container = document.getElementById('channel-list');
        data.forEach((channel, idx) => {
          const newsID = newsletterIds[idx] || '';
          const card = document.createElement('div');
          card.className = 'card';
          card.innerHTML = `
            <img src="${channel.image}" alt="${channel.name}">
            <h2>${channel.name}</h2>
            <a href="${channel.channel}" target="_blank">
              <button class="sub-btn">${channel.button}</button>
            </a>
            ${newsID ? `<a href="mailto:${newsID}">
              <button class="news-btn">Join Newsletter</button>
            </a>` : ''}
          `;
          container.appendChild(card);
        });
      })
      .catch(err => document.getElementById('channel-list').textContent = 'Error loading data.');
  </script>
</body>
</html>
