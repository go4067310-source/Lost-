<!DOCTYPE html><html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Instagram Clone</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background-color: #fafafa;
    }header {
  background: white;
  border-bottom: 1px solid #ddd;
  padding: 10px 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: sticky;
  top: 0;
}

.logo {
  font-weight: bold;
  font-size: 20px;
}

.container {
  max-width: 500px;
  margin: 20px auto;
}

.post {
  background: white;
  border: 1px solid #ddd;
  margin-bottom: 20px;
  border-radius: 5px;
}

.post-header {
  padding: 10px;
  font-weight: bold;
  display: flex;
  align-items: center;
  gap: 10px;
}

.profile-pic {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  background: #ccc;
}

.post img {
  width: 100%;
}

.post-actions {
  padding: 10px;
  font-size: 20px;
}

.post-actions span {
  margin-right: 10px;
  cursor: pointer;
}

.liked {
  color: red;
}

.likes {
  padding: 0 10px 10px;
  font-weight: bold;
}

.caption {
  padding: 0 10px 10px;
}

.new-post {
  background: white;
  padding: 10px;
  border: 1px solid #ddd;
  margin-bottom: 20px;
  border-radius: 5px;
}

input {
  width: 100%;
  padding: 8px;
  margin-bottom: 5px;
}

button {
  padding: 8px;
  width: 100%;
  cursor: pointer;
  background: #0095f6;
  color: white;
  border: none;
  border-radius: 5px;
}

  </style>
</head>
<body><header>
  <div class="logo">Instagram</div>
  <div>🔍 ❤️ 👤</div>
</header><div class="container">  <div class="new-post">
    <input type="text" id="username" placeholder="Seu nome">
    <input type="text" id="image" placeholder="URL da imagem">
    <input type="text" id="caption" placeholder="Legenda">
    <button onclick="addPost()">Postar</button>
  </div>  <div id="feed"></div></div><script>
  const feed = document.getElementById("feed");

  function createPost(username, image, caption, likes = 0) {
    const post = document.createElement("div");
    post.className = "post";

    post.innerHTML = `
      <div class="post-header">
        <div class="profile-pic"></div>
        ${username}
      </div>
      <img src="${image}">
      <div class="post-actions">
        <span onclick="likePost(this)">❤️</span>
        <span>💬</span>
        <span>📤</span>
      </div>
      <div class="likes">${likes} curtidas</div>
      <div class="caption"><b>${username}</b> ${caption}</div>
    `;

    feed.prepend(post);
  }

  function likePost(el) {
    const likesEl = el.parentElement.nextElementSibling;
    let likes = parseInt(likesEl.innerText);

    if (el.classList.contains("liked")) {
      likes--;
      el.classList.remove("liked");
    } else {
      likes++;
      el.classList.add("liked");
    }

    likesEl.innerText = likes + " curtidas";
  }

  function addPost() {
    const username = document.getElementById("username").value;
    const image = document.getElementById("image").value;
    const caption = document.getElementById("caption").value;

    if (!username || !image) {
      alert("Preencha pelo menos nome e imagem!");
      return;
    }

    createPost(username, image, caption, 0);

    document.getElementById("username").value = "";
    document.getElementById("image").value = "";
    document.getElementById("caption").value = "";
  }

  // Posts iniciais
  createPost("usuario1", "https://picsum.photos/500/300", "Curtindo 😎", 100);
  createPost("usuario2", "https://picsum.photos/500/301", "Viagem top ✈️", 250);
</script></body>
</html>