<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Raafi - Lacak Lokasi</title>
<style>
    body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background: #1e1e2f; color: #f0f0f0; text-align: center; padding: 50px; }
    .container { background: #2e2e44; padding: 30px; border-radius: 15px; max-width: 500px; margin: auto; box-shadow: 0 0 20px rgba(0,0,0,0.5); }
    h2 { color: #4CAF50; }
    input { padding: 10px; margin: 10px 0; width: 80%; border-radius: 5px; border: none; }
    button { padding: 12px 20px; margin: 10px; border: none; border-radius: 8px; background: #4CAF50; color: white; cursor: pointer; font-weight: bold; transition: 0.3s; }
    button:hover { background: #45a049; transform: scale(1.05); }
    #map { margin-top: 20px; width: 100%; height: 400px; border-radius: 10px; }
    #info { margin-top: 15px; }
</style>
</head>
<body>

<div class="container" id="loginContainer">
    <h2>Raafi - Login</h2>
    <input type="text" id="username" placeholder="Username"><br>
    <input type="password" id="password" placeholder="Password"><br>
    <button onclick="login()">Login</button>
    <div id="loginMessage"></div>
</div>

<div class="container" id="locationContainer" style="display:none;">
    <h2>Raafi - Lacak Lokasi</h2>
    <p>Klik tombol di bawah untuk menampilkan lokasi Anda:</p>
    <button onclick="getLocation()">Tampilkan Lokasi</button>
    <div id="info"></div>
    <div id="map"></div>
</div>

<script>
// Username dan password default
const USERNAME = "raafi";
const PASSWORD = "raafi123";

function login() {
    const userInput = document.getElementById('username').value;
    const passInput = document.getElementById('password').value;
    const message = document.getElementById('loginMessage');

    if(userInput === USERNAME && passInput === PASSWORD){
        document.getElementById('loginContainer').style.display = "none";
        document.getElementById('locationContainer').style.display = "block";
    } else {
        message.textContent = "Username atau password salah!";
        message.style.color = "#f44336";
    }
}

function getLocation() {
    const info = document.getElementById('info');
    const mapDiv = document.getElementById('map');

    if(navigator.geolocation){
        navigator.geolocation.getCurrentPosition(showPosition, showError);
    } else {
        info.innerHTML = "Geolocation tidak didukung oleh browser Anda.";
    }

    function showPosition(position){
        const lat = position.coords.latitude;
        const lon = position.coords.longitude;
        info.innerHTML = `Latitude: ${lat} <br> Longitude: ${lon}`;

        mapDiv.innerHTML = `<iframe 
            width="100%" height="400" frameborder="0" style="border:0"
            src="https://www.google.com/maps?q=${lat},${lon}&hl=es;z=14&output=embed" allowfullscreen>
        </iframe>`;
    }

    function showError(error){
        switch(error.code){
            case error.PERMISSION_DENIED:
                info.innerHTML = "Pengguna menolak permintaan lokasi.";
                break;
            case error.POSITION_UNAVAILABLE:
                info.innerHTML = "Informasi lokasi tidak tersedia.";
                break;
            case error.TIMEOUT:
                info.innerHTML = "Permintaan lokasi habis waktu.";
                break;
            case error.UNKNOWN_ERROR:
                info.innerHTML = "Terjadi kesalahan yang tidak diketahui.";
                break;
        }
    }
}
</script>

</body>
</html>
