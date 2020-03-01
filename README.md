<!DOCTYPE html>
<html lang="en" dir="ltr">
  <head>
    <meta charset="utf-8">
    <title></title>
    <style>

    @keyframes slideInRight {
      from {
        transform: translate3d(100%, 0, 0);
        visibility: visible;
      }

      to {
        transform: translate3d(0, 0, 0);
      }
    }

    button.chatLauncher {
      animation-duration: 0.5s;
      transition-duration: 0.5s;
      position: fixed;
      bottom: 32px;
      right: 32px;
      z-index: 9999;
      border: 4px solid #075cc2;
      padding: 1em;
      border-radius: 8px;
      margin: 0;
      text-decoration: none;
      background-color: #ffffff;
      color: #454545;
      font-family: sans-serif;
      font-size: 1rem;
      cursor: pointer;
      text-align: left;
      -webkit-appearance: none;
      -moz-appearance: none;
      width: 264px;
      opacity: 0;
    }

    button.chatLauncher.open {
      animation-name: slideInRight;
      opacity: 1;
    }

    button.chatLauncher:hover,
    button.chatLauncher:focus {
      background-color: rgb(225, 225, 254);
      border: 4px solid #0053ba;
    }

    button.chatLauncher:focus {
      outline: 1px solid #0053ba;
      outline-offset: -4px;
    }

    </style>
  </head>
  <body>

    <button type="button" class="chatLauncher">
      <div class="button-message">Need help?</div>
    </button>

    <script src="https://web-chat.global.assistant.watson.cloud.ibm.com/loadWatsonAssistantChat.js"></script>
    <script>

    const options = {
      integrationID: "2865e717-1d18-4a95-8018-2759c0801441", // The ID of this integration.
      region: "eu-de", // The region your integration is hosted in.
      showLauncher: false
    }
    window.loadWatsonAssistantChat(options).then(function(instance){
   // Select the button element from the page.
   const button = document.querySelector('.chatLauncher');

   // Add the event listener to open your Web Chat.
   button.addEventListener('click', () => {
     instance.openWindow();
   });

   // Render the Web Chat. Nothing appears on the page, because the launcher is
   // hidden and the Web Chat window is closed by default.
   instance.render().then(() => {
     // Now that Web Chat has been rendered (but is still closed), we make the
     // custom launcher button visible.
     button.style.display = 'block';
     button.classList.add('open');
   });
 });
</script>


  </body>
</html>

