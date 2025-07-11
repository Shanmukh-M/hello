<!DOCTYPE html>

<html lang="en">

<head>

&nbsp; <meta charset="UTF-8" />

&nbsp; <meta name="viewport" content="width=device-width, initial-scale=1.0"/>

&nbsp; <meta name="description" content="Find the best food places near you with live ratings, suggestions, and smart chat assistant BETA."/>

&nbsp; <meta name="keywords" content="food, best restaurants, near me, Hyderabad, swiggy, zomato, local food"/>

&nbsp; <meta name="author" content="BETA Assistant" />

&nbsp; <title>Best Food Places</title>

&nbsp; <style>

&nbsp;   body {

&nbsp;     background: linear-gradient(to right, #ffe0c3, #ffb199);

&nbsp;     font-family: 'Segoe UI', sans-serif;

&nbsp;     margin: 0;

&nbsp;     padding: 0;

&nbsp;     min-height: 100vh;

&nbsp;     background-attachment: fixed;

&nbsp;     background-size: cover;

&nbsp;   }

&nbsp;   .container {

&nbsp;     max-width: 1000px;

&nbsp;     margin: auto;

&nbsp;     padding: 20px;

&nbsp;   }

&nbsp;   .card {

&nbsp;     background-color: #ffffff;

&nbsp;     border-radius: 10px;

&nbsp;     box-shadow: 0 2px 8px rgba(0,0,0,0.1);

&nbsp;     margin-bottom: 20px;

&nbsp;     padding: 15px;

&nbsp;     overflow: hidden;

&nbsp;     display: flex;

&nbsp;     align-items: center;

&nbsp;     text-decoration: none;

&nbsp;     transition: background 0.2s;

&nbsp;   }

&nbsp;   .card:hover {

&nbsp;     background: #fff7f0;

&nbsp;   }

&nbsp;   .card img {

&nbsp;     width: 80px;

&nbsp;     height: 80px;

&nbsp;     border-radius: 50%;

&nbsp;     margin-right: 15px;

&nbsp;     object-fit: cover;

&nbsp;   }

&nbsp;   .card div {

&nbsp;     font-size: 16px;

&nbsp;     color: #333;

&nbsp;   }

&nbsp;   .chat-popup {

&nbsp;     position: fixed;

&nbsp;     bottom: 90px;

&nbsp;     right: 20px;

&nbsp;     width: 300px;

&nbsp;     background: #ffffff;

&nbsp;     border-radius: 10px;

&nbsp;     box-shadow: 0 2px 10px rgba(0,0,0,0.2);

&nbsp;     display: none;

&nbsp;     flex-direction: column;

&nbsp;     z-index: 1000;

&nbsp;   }

&nbsp;   .chat-header {

&nbsp;     background-color: #ff5722;

&nbsp;     color: white;

&nbsp;     padding: 10px;

&nbsp;     font-weight: bold;

&nbsp;     border-top-left-radius: 10px;

&nbsp;     border-top-right-radius: 10px;

&nbsp;   }

&nbsp;   .chat-body {

&nbsp;     padding: 10px;

&nbsp;     max-height: 250px;

&nbsp;     overflow-y: auto;

&nbsp;   }

&nbsp;   .chat-input {

&nbsp;     display: flex;

&nbsp;     border-top: 1px solid #ddd;

&nbsp;   }

&nbsp;   .chat-input input {

&nbsp;     flex: 1;

&nbsp;     padding: 10px;

&nbsp;     border: none;

&nbsp;     outline: none;

&nbsp;   }

&nbsp;   .chat-input button {

&nbsp;     background-color: #ff5722;

&nbsp;     color: white;

&nbsp;     border: none;

&nbsp;     padding: 10px 15px;

&nbsp;     cursor: pointer;

&nbsp;   }

&nbsp;   .chat-icon {

&nbsp;     position: fixed;

&nbsp;     bottom: 20px;

&nbsp;     right: 20px;

&nbsp;     width: 60px;

&nbsp;     height: 60px;

&nbsp;     background: #ff5722;

&nbsp;     border-radius: 50%;

&nbsp;     display: flex;

&nbsp;     align-items: center;

&nbsp;     justify-content: center;

&nbsp;     color: white;

&nbsp;     font-size: 28px;

&nbsp;     cursor: pointer;

&nbsp;     z-index: 1001;

&nbsp;   }

&nbsp; </style>

</head>

<body>

&nbsp; <div class="container">

&nbsp;   <a href="https://www.zomato.com/hyderabad/spicy-adda" class="card" target="\_blank">

&nbsp;     <img src="https://b.zmtcdn.com/data/pictures/4/19784424/3d4a7e6cbcd07582dcd41e9c6a4f2bdf.jpg" alt="Spicy Adda" />

&nbsp;     <div><strong>Spicy Adda</strong><br/>Great for spicy South Indian meals</div>

&nbsp;   </a>

&nbsp;   <a href="https://www.zomato.com/hyderabad/sri-krishna-grand" class="card" target="\_blank">

&nbsp;     <img src="https://b.zmtcdn.com/data/pictures/3/19806283/13b80d66eb98f12adad64b753c6c97bb.jpg" alt="Sri Krishna Grand" />

&nbsp;     <div><strong>Krishna Grand</strong><br/>Top-rated vegetarian thalis</div>

&nbsp;   </a>

&nbsp;   <a href="https://www.zomato.com/hyderabad/dominos-pizza" class="card" target="\_blank">

&nbsp;     <img src="https://b.zmtcdn.com/data/pictures/chains/4/9054/2e5a2a8e1b7f7f0f7a4f3e9c9852d.jpg" alt="Domino's" />

&nbsp;     <div><strong>Domino's Pizza</strong><br/>Quick and easy pizza \& fast food</div>

&nbsp;   </a>

&nbsp; </div>



&nbsp; <!-- BETA Assistant -->

&nbsp; <div class="chat-icon" onclick="toggleChat()">💬</div>

&nbsp; <div class="chat-popup" id="chatPopup">

&nbsp;   <div class="chat-header">BETA - Your Food Assistant</div>

&nbsp;   <div class="chat-body" id="chatBody">

&nbsp;     <p><strong>BETA:</strong> Hi there! Need help finding the perfect place to eat in Hyderabad?</p>

&nbsp;   </div>

&nbsp;   <div class="chat-input">

&nbsp;     <input type="text" id="userInput" placeholder="Ask BETA..." />

&nbsp;     <button onclick="sendMessage()">Send</button>

&nbsp;   </div>

&nbsp; </div>

&nbsp; <audio id="notifySound" src="https://actions.google.com/sounds/v1/cartoon/wood\_plank\_flicks.ogg"></audio>



&nbsp; <script>

&nbsp;   function toggleChat() {

&nbsp;     const popup = document.getElementById('chatPopup');

&nbsp;     popup.style.display = popup.style.display === 'flex' ? 'none' : 'flex';

&nbsp;     popup.style.flexDirection = 'column';

&nbsp;   }



&nbsp;   function sendMessage() {

&nbsp;     const input = document.getElementById('userInput');

&nbsp;     const chatBody = document.getElementById('chatBody');

&nbsp;     const userMessage = input.value.trim();

&nbsp;     const msg = userMessage.toLowerCase();

&nbsp;     if (userMessage) {

&nbsp;       chatBody.innerHTML += `<p><strong>You:</strong> ${userMessage}</p>`;

&nbsp;       let reply = getBetaSuggestion(msg);

&nbsp;       setTimeout(() => {

&nbsp;         chatBody.innerHTML += `<p><strong>BETA:</strong> ${reply}</p>`;

&nbsp;         document.getElementById('notifySound').play();

&nbsp;         chatBody.scrollTop = chatBody.scrollHeight;

&nbsp;       }, 800);

&nbsp;       input.value = "";

&nbsp;       chatBody.scrollTop = chatBody.scrollHeight;

&nbsp;     }

&nbsp;   }



&nbsp;   document.getElementById("userInput").addEventListener("keypress", function(event) {

&nbsp;     if (event.key === "Enter") {

&nbsp;       event.preventDefault();

&nbsp;       sendMessage();

&nbsp;     }

&nbsp;   });



&nbsp;   function promptLocation() {

&nbsp;     const userLocation = prompt("Welcome! Please enter your city to find the best food places near you:", "Hyderabad");

&nbsp;     if (userLocation) {

&nbsp;       document.querySelectorAll('.card').forEach(card => {

&nbsp;         const currentLink = card.getAttribute('href');

&nbsp;         if (currentLink.includes("zomato.com")) {

&nbsp;           const updatedLink = currentLink.replace(/zomato\\\\.com\\\\/\[a-z\\\\-]+\\\\//i, `zomato.com/${userLocation.toLowerCase()}/`);

&nbsp;           card.setAttribute('href', updatedLink);

&nbsp;         }

&nbsp;       });

&nbsp;       const betaGreeting = document.querySelector("#chatBody p");

&nbsp;       if (betaGreeting) betaGreeting.innerHTML = `<strong>BETA:</strong> Hi there! Need help finding the perfect place to eat in ${userLocation}?`;

&nbsp;     }

&nbsp;   }



&nbsp;   window.onload = function() {

&nbsp;     promptLocation();

&nbsp;   };



&nbsp;   function getBetaSuggestion(msg) {

&nbsp;     const suggestions = \[

&nbsp;       "Craving spice? 🌶️ Check out Spicy Adda!",

&nbsp;       "Thirsty for a shake? 🥤 Roll Hub's got you covered!",

&nbsp;       "Late-night hunger? 🌙 Domino’s Pizza delivers late!",

&nbsp;       "Feeling traditional? 🍛 Sri Krishna Grand has amazing South Indian meals!",

&nbsp;       "Hungry on a budget? 💸 Try Sri Rama Tiffin Centre!",

&nbsp;       "Want something new? 🎉 Spicy Adda is the latest talk of the town!",

&nbsp;       "For a family outing, 👨‍👩‍👧‍👦 Sitara Grand has the variety you need!",

&nbsp;       "Need a quick bite? 🚀 Roll Hub has fast and tasty wraps!",

&nbsp;       "Cheese lovers alert! 🧀 Grab a pizza from Domino's!"

&nbsp;     ];

&nbsp;     if (msg.includes("biryani")) return "You must try Sitara Grand or Bamboo Biryani for delicious biryani!";

&nbsp;     if (msg.includes("veg") || msg.includes("vegetarian")) return "Sri Krishna Grand is perfect for tasty vegetarian meals.";

&nbsp;     if (msg.includes("cheap") || msg.includes("budget")) return "Sri Rama Tiffin Centre offers great food at affordable prices!";

&nbsp;     if (msg.includes("fast food")) return "Domino’s Pizza and Roll Hub are great fast food options in Hyderabad.";

&nbsp;     if (msg.includes("new")) return "Spicy Adda and Roll Hub are some of the newest popular places in town!";

&nbsp;     if (msg.includes("breakfast")) return "Try Sri Rama Tiffin Centre for hot idlis and crispy dosas.";

&nbsp;     if (msg.includes("pizza")) return "Domino’s Pizza is your go-to for delicious pizzas near you.";

&nbsp;     if (msg.includes("north indian")) return "Sitara Grand offers a rich North Indian menu with great reviews.";

&nbsp;     return suggestions\[Math.floor(Math.random() \* suggestions.length)];

&nbsp;   }

&nbsp; </script>

</body>

</html>



