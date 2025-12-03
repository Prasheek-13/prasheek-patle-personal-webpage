<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Prasheek Patle - Personal Webpage</title>

   
    <link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css" />

    <style>
        body {
            font-family: 'Poppins', sans-serif;
            margin: 0;
            padding: 0;
            background: linear-gradient(135deg, #6dd5fa, #ffffff91);
            color: #333;
        }
        header {
            background: linear-gradient(135deg, #1e3c72, #2a5298);
            color: white;
            text-align: center;
            padding: 60px 20px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
        }
        section {
            background: rgba(255,255,255,0.85);
            margin: 25px auto;
            padding: 25px;
            max-width: 850px;
            border-radius: 15px;
            backdrop-filter: blur(6px);
            box-shadow: 0 4px 20px rgba(0,0,0,0.15);
            transition: transform 0.3s ease;
        }
        section:hover {
            transform: translateY(-5px);
        }
        h2 {
            color: #1e3c72;
            border-left: 5px solid #1e3c72;
            padding-left: 10px;
        }
        ul {
            line-height: 1.8;
        }
        a {
            color: #1e3c72;
            font-weight: bold;
            text-decoration: none;
        }
        a:hover {
            text-decoration: underline;
        }
        footer {
            text-align: center;
            padding: 25px;
            background: linear-gradient(135deg, #1e3c72, #2a5298);
            color: white;
            margin-top: 50px;
            font-size: 14px;
            letter-spacing: 1px;
        }
        #map {
            height: 350px;
            border-radius: 12px;
            margin-top: 15px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.3);
        }
        #weatherBox img {
            width: 50px;
            vertical-align: middle;
        }
    </style>
</head>
<body>

<header>
    <img src="images/WhatsApp Image 2025-07-19 at 17.07.41_0402a885.jpg" 
         alt="an image of Prasheek" 
         style="width:100px;height:auto;border-radius:50px;box-shadow:0 4px 10px rgba(0,0,0,0.3);" />
    <h1>Prasheek Patle</h1>
    <p> • Average chill & smart guy  • Engineering aspirant   </p>
    <p>• Beginner web developer</p>
    <p><strong>Roll No:</strong> CE25B082</p>
</header>

<section>
    <h2>ABOUT ME</h2>
    <p>
        Hi! I'm <strong>Prasheek Patle</strong>, a motivated and focused student who loves learning new things and improving 
        every single day. I enjoy technology, logical thinking, and creativity. I'm passionate about personal growth and 
        always prefer smart work over unnecessary hard work. I pick things quickly and like keeping life balanced and peaceful.
    </p>
</section>

<section>
    <h2>HOBBIES</h2>
    <ul>
        <li>Coding & Technology</li>
        <li>Music</li>
        <li>Travelling</li>
        <li>Fitness / Gym</li>
        <li>Learning new skills</li>
    </ul>
</section>

<section>
    <h2>GOALS</h2>
    <ul>
        <li>Build a successful and stable career in the tech/engineering field.</li>
        <li>Become financially independent and support my family.</li>
        <li>Keep improving continuously in skills, discipline, and knowledge.</li>
        <li>Start a business or side-venture in future.</li>
    </ul>
</section>


<section id="weather-section">
    <h2>WEATHER IN MY CITY</h2>
    <div id="weatherBox" style="
        padding: 20px;
        background: #ffffffd8;
        border-radius: 15px;
        box-shadow: 0 4px 10px rgba(0,0,0,0.15);
        font-size: 18px;">
        
    </div>
</section>


<section id="map-section">
    <h2>MY CITY ON MAP</h2>
    <div id="map"></div>
</section>

<section>
    <h2>CONTACT ME</h2>
    <p>You can reach me at: <a href="mailto:ce25b082@smail.iitm.ac.in">ce25b082@smail.iitm.ac.in</a></p>
</section>

<footer>
    <p>© 2025 Prasheek Patle</p>
</footer>


<script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>

<script>

const apiKey = "f0f800f9ba144bc59c3102102250312";  // <-- PUT YOUR API KEY HERE
const city = "balaghat";  // <-- REPLACE WITH YOUR CITY

async function loadWeather() {
    const url = `https://api.weatherapi.com/v1/current.json?key=${apiKey}&q=${city}`;

    try {
        let response = await fetch(url);
        let data = await response.json();

        document.getElementById("weatherBox").innerHTML = `
            <strong>City:</strong> ${data.location.name} <br>
            <strong>Temperature:</strong> ${data.current.temp_c}°C <br>
            <strong>Condition:</strong> ${data.current.condition.text} <br>
            <img src="https:${data.current.condition.icon}">
        `;
    } 
    catch (error) {
        document.getElementById("weatherBox").innerHTML = 
            "<strong>Error:</strong> Unable to load weather!";
    }
}

loadWeather();


var latitude = 21.8129;  
var longitude = 80.1838; 

var map = L.map('map').setView([latitude, longitude], 12);

L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    maxZoom: 19,
}).addTo(map);

L.marker([latitude, longitude]).addTo(map)
    .bindPopup("Balaghat")
    .openPopup();

</script>

</body>
</html>
