[Link to another page](./music).

# Siiiistiii

> Now This Is Epic.
>
> <audio controls> <source src="./music/SoundEls1.2.mp3" type="audio/mpeg"> Selaimesi ei tue audio-elementtiä. </audio>

<div id="music-list"></div>

<script>
async function loadMusic() {
  const user = "jusufswe";              // GitHub-käyttäjänimesi
  const repo = "asdwewewarawreegyesr325432f320r329fj321d8903ha894tg3q874t2qg826iydg876aftrg4682aytg32";             // Repositoriosi nimi
  const path = "docs/music";            // Polku musiikkikansioon

  const url = `https://api.github.com/repos/${user}/${repo}/contents/${path}`;

  const response = await fetch(url);
  const files = await response.json();

  const container = document.getElementById("music-list");

  files
    .filter(file => file.name.toLowerCase().endsWith(".mp3"))
    .forEach(file => {
      const title = file.name.replace(".mp3", "");

      const block = document.createElement("div");
      block.innerHTML = `
        <h3>${title}</h3>
        <audio controls src="${file.download_url}"></audio>
      `;

      container.appendChild(block);
    });
}

loadMusic();
</script>
