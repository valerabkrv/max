<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>MAX Messenger</title>

  <style>
    *{
      margin:0;
      padding:0;
      box-sizing:border-box;
      font-family: Arial, sans-serif;
    }

    body{
      background:#0f172a;
      color:white;
      height:100vh;
      display:flex;
    }

    .sidebar{
      width:300px;
      background:#111827;
      border-right:1px solid #1f2937;
      display:flex;
      flex-direction:column;
    }

    .logo{
      padding:20px;
      font-size:24px;
      font-weight:bold;
      color:#38bdf8;
      border-bottom:1px solid #1f2937;
    }

    .search{
      padding:15px;
    }

    .search input{
      width:100%;
      padding:12px;
      border:none;
      border-radius:10px;
      background:#1e293b;
      color:white;
      outline:none;
    }

    .friends{
      flex:1;
      overflow-y:auto;
    }

    .friend{
      display:flex;
      align-items:center;
      gap:12px;
      padding:15px;
      cursor:pointer;
      transition:0.2s;
      border-bottom:1px solid #1f2937;
    }

    .friend:hover{
      background:#1e293b;
    }

    .avatar{
      width:50px;
      height:50px;
      border-radius:50%;
      background:#38bdf8;
      display:flex;
      align-items:center;
      justify-content:center;
      font-weight:bold;
      font-size:18px;
    }

    .friend-info h3{
      font-size:16px;
    }

    .friend-info p{
      font-size:13px;
      color:#94a3b8;
    }

    .chat{
      flex:1;
      display:flex;
      flex-direction:column;
    }

    .chat-header{
      height:80px;
      background:#111827;
      border-bottom:1px solid #1f2937;
      display:flex;
      align-items:center;
      padding:0 25px;
      gap:15px;
    }

    .messages{
      flex:1;
      padding:25px;
      overflow-y:auto;
      display:flex;
      flex-direction:column;
      gap:15px;
    }

    .message{
      max-width:400px;
      padding:15px;
      border-radius:15px;
      line-height:1.4;
    }

    .me{
      align-self:flex-end;
      background:#38bdf8;
      color:black;
    }

    .friend-msg{
      align-self:flex-start;
      background:#1e293b;
    }

    .send-box{
      padding:20px;
      background:#111827;
      border-top:1px solid #1f2937;
      display:flex;
      gap:15px;
    }

    .send-box input{
      flex:1;
      padding:15px;
      border:none;
      border-radius:12px;
      background:#1e293b;
      color:white;
      outline:none;
      font-size:15px;
    }

    .send-box button{
      padding:15px 25px;
      border:none;
      border-radius:12px;
      background:#38bdf8;
      color:black;
      font-weight:bold;
      cursor:pointer;
      transition:0.2s;
    }

    .send-box button:hover{
      opacity:0.8;
    }

    @media(max-width:700px){
      .sidebar{
        width:100px;
      }

      .friend-info{
        display:none;
      }

      .logo{
        font-size:18px;
        text-align:center;
      }
    }
  </style>
</head>

<body>

  <div class="sidebar">

    <div class="logo">
      MAX
    </div>

    <div class="search">
      <input type="text" placeholder="Поиск">
    </div>

    <div class="friends">

      <div class="friend">
        <div class="avatar">A</div>

        <div class="friend-info">
          <h3>Алексей</h3>
          <p>Привет 👋</p>
        </div>
      </div>

      <div class="friend">
        <div class="avatar">M</div>

        <div class="friend-info">
          <h3>Миша</h3>
          <p>Как дела?</p>
        </div>
      </div>

      <div class="friend">
        <div class="avatar">K</div>

        <div class="friend-info">
          <h3>Катя</h3>
          <p>Жду ответ 😊</p>
        </div>
      </div>

    </div>

  </div>

  <div class="chat">

    <div class="chat-header">

      <div class="avatar">A</div>

      <div>
        <h2>Алексей</h2>
        <p style="color:#94a3b8;">в сети</p>
      </div>

    </div>

    <div class="messages" id="messages">

      <div class="message friend-msg">
        Привет! Как дела?
      </div>

      <div class="message me">
        Всё отлично 😎
      </div>

    </div>

    <div class="send-box">

      <input
        type="text"
        id="messageInput"
        placeholder="Введите сообщение..."
      >

      <button onclick="sendMessage()">
        Отправить
      </button>

    </div>

  </div>

  <script>

    function sendMessage(){

      const input = document.getElementById("messageInput");
      const messages = document.getElementById("messages");

      if(input.value.trim() !== ""){

        const div = document.createElement("div");

        div.classList.add("message");
        div.classList.add("me");

        div.innerText = input.value;

        messages.appendChild(div);

        input.value = "";

        messages.scrollTop = messages.scrollHeight;
      }
    }

  </script>

</body>
</html>
