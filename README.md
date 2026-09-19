<!DOCTYPE html>
<html lang="el">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Greece Weather</title>

<style>
*{
    box-sizing:border-box;
}

body{
    margin:0;
    font-family:Arial,Helvetica,sans-serif;
    background:linear-gradient(180deg,#071a35,#0b2b52 55%,#071a35);
    color:white;
    min-height:100vh;
}

header{
    text-align:center;
    padding:25px 15px 15px;
}

.logo{
    font-size:30px;
    font-weight:bold;
}

.subtitle{
    color:#a9c9eb;
    margin-top:6px;
}

/* SEARCH */

.search-area{
    width:94%;
    max-width:850px;
    margin:15px auto;
    position:relative;
}

.search-box{
    display:flex;
    gap:8px;
}

.search-box input{
    flex:1;
    padding:15px 17px;
    border:none;
    border-radius:14px;
    font-size:17px;
    outline:none;
    background:#ffffff;
    color:#12233a;
}

.search-box button{
    border:none;
    border-radius:14px;
    padding:0 22px;
    font-size:16px;
    font-weight:bold;
    cursor:pointer;
    background:#3b9cff;
    color:white;
}

.search-box button:active{
    transform:scale(.97);
}

.results{
    position:absolute;
    top:62px;
    left:0;
    right:0;
    z-index:20;
    background:#102b4c;
    border-radius:12px;
    overflow:hidden;
    box-shadow:0 8px 25px rgba(0,0,0,.35);
}

.result{
    padding:13px 16px;
    border-bottom:1px solid rgba(255,255,255,.08);
    cursor:pointer;
}

.result:hover{
    background:#17416d;
}

.result-name{
    font-weight:bold;
}

.result-country{
    font-size:13px;
    color:#a9c9eb;
    margin-top:3px;
}

/* LOCATION */

.location{
    text-align:center;
    margin:25px auto 15px;
}

.location h1{
    margin:0;
    font-size:30px;
}

.country{
    margin-top:5px;
    color:#a9c9eb;
    font-size:17px;
}

/* CURRENT */

.current{
    width:94%;
    max-width:900px;
    margin:20px auto;
    padding:22px;
    border-radius:22px;
    background:rgba(255,255,255,.08);
    backdrop-filter:blur(10px);
    text-align:center;
}

.current-temp{
    font-size:58px;
    font-weight:bold;
}

.current-condition{
    font-size:21px;
    margin-top:3px;
}

.current-details{
    display:flex;
    justify-content:center;
    gap:25px;
    flex-wrap:wrap;
    margin-top:20px;
    color:#c8ddf4;
}

/* FORECAST */

.forecast-title{
    width:94%;
    max-width:1100px;
    margin:30px auto 15px;
    font-size:22px;
    font-weight:bold;
}

.forecast{
    width:94%;
    max-width:1100px;
    margin:auto;
    display:grid;
    grid-template-columns:repeat(4,1fr);
    gap:12px;
}

.day{
    background:rgba(255,255,255,.08);
    border:1px solid rgba(255,255,255,.07);
    border-radius:17px;
    padding:16px 10px;
    text-align:center;
    cursor:pointer;
    transition:.2s;
}

.day:hover{
    background:rgba(255,255,255,.14);
    transform:translateY(-2px);
}

.day.selected{
    border:2px solid #53aaff;
    background:rgba(55,150,255,.16);
}

.day-name{
    font-weight:bold;
    font-size:16px;
}

.day-date{
    color:#9ebddd;
    font-size:13px;
    margin-top:4px;
}

.icon{
    font-size:42px;
    margin:12px 0;
}

.temps{
    font-size:19px;
}

.max{
    font-weight:bold;
}

.min{
    color:#a9c9eb;
    margin-left:7px;
}

.precip{
    margin-top:9px;
    color:#b9dbfa;
    font-size:14px;
}

.wind{
    margin-top:7px;
    font-size:14px;
    color:#c8ddf4;
}

/* DETAILS */

.details{
    width:94%;
    max-width:1100px;
    margin:25px auto 40px;
    background:rgba(255,255,255,.08);
    border-radius:20px;
    padding:20px;
    display:none;
}

.details h2{
    margin-top:0;
}

.hourly{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(105px,1fr));
    gap:9px;
}

.hour{
    background:rgba(0,0,0,.16);
    border-radius:13px;
    padding:12px 6px;
    text-align:center;
}

.hour-time{
    color:#a9c9eb;
    font-size:13px;
}

.hour-icon{
    font-size:28px;
    margin:7px 0;
}

.hour-temp{
    font-size:17px;
    font-weight:bold;
}

.hour-wind{
    margin-top:5px;
    font-size:13px;
    color:#c4d9ef;
}

.error{
    width:94%;
    max-width:800px;
    margin:20px auto;
    background:#6d2630;
    padding:15px;
    border-radius:12px;
    text-align:center;
    display:none;
}

.loading{
    text-align:center;
    padding:25px;
    color:#a9c9eb;
}

/* 4 / 4 / 4 / 3 */

@media(max-width:800px){
    .forecast{
        grid-template-columns:repeat(2,1fr);
    }
}

@media(max-width:480px){
    .forecast{
        grid-template-columns:repeat(2,1fr);
        gap:8px;
    }

    .day{
        padding:13px 6px;
    }

    .icon{
        font-size:35px;
    }

    .current-temp{
        font-size:48px;
    }

    .search-box button{
        padding:0 15px;
    }
}
</style>
</head>

<body>

<header>
    <div class="logo">🌦️ Greece Weather</div>
    <div class="subtitle">
        15ήμερη πρόγνωση με πολλαπλά προγνωστικά μοντέλα
    </div>
</header>

<div class="search-area">

    <div class="search-box">
        <input
            id="searchInput"
            type="text"
            placeholder="Αναζήτησε περιοχή σε όλο τον κόσμο..."
            autocomplete="off"
        >

        <button onclick="searchLocation()">Αναζήτηση</button>
    </div>

    <div id="results" class="results"></div>

</div>

<div id="error" class="error"></div>

<div id="location" class="location">
    <h1 id="placeName">Θεσσαλονίκη</h1>
    <div id="countryName" class="country">Ελλάδα</div>
</div>

<div id="current" class="current">
    <div class="loading">Φόρτωση δεδομένων...</div>
</div>

<div class="forecast-title">
    15ήμερη πρόγνωση
</div>

<div id="forecast" class="forecast">
</div>

<div id="details" class="details">
</div>

<script>

/* =========================================================
   ΡΥΘΜΙΣΕΙΣ
========================================================= */

let currentLocation = {
    name:"Θεσσαλονίκη",
    country:"Ελλάδα",
    latitude:40.6401,
    longitude:22.9444
};

let forecastData = null;


/* =========================================================
   DEFAULT CITIES
========================================================= */

const greekCities = [
    {
        name:"Αθήνα",
        country:"Ελλάδα",
        latitude:37.9838,
        longitude:23.7275
    },
    {
        name:"Θεσσαλονίκη",
        country:"Ελλάδα",
        latitude:40.6401,
        longitude:22.9444
    },
    {
        name:"Πάτρα",
        country:"Ελλάδα",
        latitude:38.2466,
        longitude:21.7346
    },
    {
        name:"Ηράκλειο",
        country:"Ελλάδα",
        latitude:35.3387,
        longitude:25.1442
    },
    {
        name:"Λάρισα",
        country:"Ελλάδα",
        latitude:39.6390,
        longitude:22.4191
    },
    {
        name:"Βόλος",
        country:"Ελλάδα",
        latitude:39.3610,
        longitude:22.9425
    },
    {
        name:"Ιωάννινα",
        country:"Ελλάδα",
        latitude:39.6650,
        longitude:20.8537
    },
    {
        name:"Καβάλα",
        country:"Ελλάδα",
        latitude:40.9396,
        longitude:24.4018
    }
];


/* =========================================================
   WEATHER ICONS
========================================================= */

function weatherIcon(code,isDay=true){

    if(code === 0)
        return isDay ? "☀️" : "🌙";

    if(code === 1)
        return isDay ? "🌤️" : "🌙";

    if(code === 2)
        return isDay ? "⛅" : "☁️🌙";

    if(code === 3)
        return "☁️";

    if(code === 45 || code === 48)
        return "🌫️";

    if(code >= 51 && code <= 57)
        return "🌦️";

    if(code >= 61 && code <= 67)
        return "🌧️";

    if(code >= 71 && code <= 77)
        return "🌨️";

    if(code >= 80 && code <= 82)
        return "🌦️";

    if(code >= 85 && code <= 86)
        return "🌨️";

    if(code >= 95)
        return "⛈️";

    return "🌤️";
}


function weatherText(code){

    if(code===0) return "Αίθριος";
    if(code===1) return "Κυρίως αίθριος";
    if(code===2) return "Λίγες νεφώσεις";
    if(code===3) return "Συννεφιά";
    if(code===45 || code===48) return "Ομίχλη";
    if(code>=51 && code<=57) return "Ψιλόβροχο";
    if(code>=61 && code<=67) return "Βροχή";
    if(code>=71 && code<=77) return "Χιονόπτωση";
    if(code>=80 && code<=82) return "Μπόρες";
    if(code>=85 && code<=86) return "Χιονομπόρες";
    if(code>=95) return "Καταιγίδα";

    return "Άγνωστο";
}


/* =========================================================
   WIND DIRECTION
========================================================= */

function windDirection(degrees){

    const directions = [
        "Β",
        "ΒΑ",
        "Α",
        "ΝΑ",
        "Ν",
        "ΝΔ",
        "Δ",
        "ΒΔ"
    ];

    return directions[
        Math.round(degrees / 45) % 8
    ];
}


/* =========================================================
   SEARCH WORLDWIDE
========================================================= */

async function searchLocation(){

    const input =
        document.getElementById("searchInput").value.trim();

    if(!input) return;

    const results =
        document.getElementById("results");

    results.innerHTML =
        '<div class="result">Αναζήτηση...</div>';

    try{

        const url =
            "https://geocoding-api.open-meteo.com/v1/search" +
            "?name=" + encodeURIComponent(input) +
            "&count=8" +
            "&language=el" +
            "&format=json";

        const response = await fetch(url);

        if(!response.ok)
            throw new Error();

        const data = await response.json();

        results.innerHTML = "";

        if(!data.results || data.results.length === 0){

            showError(
                "Δεν βρέθηκε περιοχή με αυτό το όνομα."
            );

            return;
        }

        data.results.forEach(place => {

            const div = document.createElement("div");

            div.className = "result";

            div.innerHTML = `
                <div class="result-name">
                    ${escapeHTML(place.name)}
                </div>

                <div class="result-country">
                    ${escapeHTML(place.country || "")}
                    ${place.admin1 ? " • " + escapeHTML(place.admin1) : ""}
                </div>
            `;

            div.onclick = () => {

                results.innerHTML = "";

                loadWeather({
                    name:place.name,
                    country:place.country || "",
                    latitude:place.latitude,
                    longitude:place.longitude
                });

            };

            results.appendChild(div);

        });

    }catch(error){

        showError(
            "Δεν ήταν δυνατή η αναζήτηση. Έλεγξε τη σύνδεσή σου."
        );

    }

}


/* =========================================================
   LOAD WEATHER
========================================================= */

async function loadWeather(location){

    hideError();

    currentLocation = location;

    document.getElementById("placeName").textContent =
        location.name;

    document.getElementById("countryName").textContent =
        location.country;

    document.getElementById("current").innerHTML =
        '<div class="loading">Φόρτωση πραγματικών δεδομένων...</div>';

    document.getElementById("forecast").innerHTML =
        '<div class="loading">Φόρτωση 15ήμερου...</div>';

    document.getElementById("details").style.display = "none";

    try{

        /*
        -------------------------------------------------------
        ECMWF IFS
        -------------------------------------------------------
        */

        const ecmwfURL =
            "https://api.open-meteo.com/v1/forecast" +

            "?latitude=" + location.latitude +

            "&longitude=" + location.longitude +

            "&hourly=" +
            "temperature_2m," +
            "precipitation_probability," +
            "precipitation," +
            "weather_code," +
            "wind_speed_10m," +
            "wind_direction_10m," +
            "is_day" +

            "&daily=" +
            "weather_code," +
            "temperature_2m_max," +
            "temperature_2m_min," +
            "precipitation_probability_max," +
            "precipitation_sum," +
            "wind_speed_10m_max," +
            "wind_direction_10m_dominant" +

            "&forecast_days=15" +

            "&timezone=auto" +

            "&models=ecmwf_ifs025";


        /*
        -------------------------------------------------------
        NOAA GFS
        -------------------------------------------------------
        */

        const gfsURL =
            "https://api.open-meteo.com/v1/gfs" +

            "?latitude=" + location.latitude +

            "&longitude=" + location.longitude +

            "&hourly=" +
            "temperature_2m," +
            "precipitation_probability," +
            "precipitation," +
            "weather_code," +
            "wind_speed_10m," +
            "wind_direction_10m," +
            "is_day" +

            "&daily=" +
            "weather_code," +
            "temperature_2m_max," +
            "temperature_2m_min," +
            "precipitation_probability_max," +
            "precipitation_sum," +
            "wind_speed_10m_max," +
            "wind_direction_10m_dominant" +

            "&forecast_days=15" +

            "&timezone=auto";


        const [ecmwfResponse,gfsResponse] =
            await Promise.all([
                fetch(ecmwfURL),
                fetch(gfsURL)
            ]);


        if(!ecmwfResponse.ok || !gfsResponse.ok)
            throw new Error();


        const ecmwf =
            await ecmwfResponse.json();

        const gfs =
            await gfsResponse.json();


        forecastData = combineModels(
            ecmwf,
            gfs
        );


        renderCurrent(forecastData);

        renderForecast(forecastData);


    }catch(error){

        console.error(error);

        showError(
            "Δεν ήταν δυνατή η φόρτωση των καιρικών δεδομένων."
        );

        document.getElementById("current").innerHTML =
            '<div class="loading">Σφάλμα φόρτωσης δεδομένων.</div>';

    }

}


/* =========================================================
   COMBINE ECMWF + GFS
========================================================= */

function average(a,b){

    if(a == null && b == null)
        return null;

    if(a == null)
        return b;

    if(b == null)
        return a;

    return (a+b)/2;
}


function combineModels(ecmwf,gfs){

    const daily = [];

    const days =
        Math.min(
            ecmwf.daily.time.length,
            gfs.daily.time.length,
            15
        );


    for(let i=0;i<days;i++){

        /*
        Μέσος όρος ECMWF + GFS.
        */

        const max =
            average(
                ecmwf.daily.temperature_2m_max[i],
                gfs.daily.temperature_2m_max[i]
            );

        const min =
            average(
                ecmwf.daily.temperature_2m_min[i],
                gfs.daily.temperature_2m_min[i]
            );

        const precip =
            Math.round(
                average(
                    ecmwf.daily.precipitation_probability_max[i],
                    gfs.daily.precipitation_probability_max[i]
                )
            );


        /*
        Χρησιμοποιούμε τον κωδικό του ECMWF
        όταν υπάρχει.
        */

        const code =
            ecmwf.daily.weather_code[i] ??
            gfs.daily.weather_code[i];


        const wind =
            average(
                ecmwf.daily.wind_speed_10m_max[i],
                gfs.daily.wind_speed_10m_max[i]
            );


        const windDir =
            ecmwf.daily.wind_direction_10m_dominant[i] ??
            gfs.daily.wind_direction_10m_dominant[i];


        daily.push({

            date:ecmwf.daily.time[i],

            max:Math.round(max),

            min:Math.round(min),

            precip:precip,

            code:code,

            wind:Math.round(wind),

            windDir:windDirection(windDir)

        });

    }


    /*
    Ωριαία δεδομένα.
    */

    const hourly = [];

    const hours =
        Math.min(
            ecmwf.hourly.time.length,
            gfs.hourly.time.length
        );


    for(let i=0;i<hours;i++){

        hourly.push({

            time:ecmwf.hourly.time[i],

            temp:
                average(
                    ecmwf.hourly.temperature_2m[i],
                    gfs.hourly.temperature_2m[i]
                ),

            precip:
                Math.round(
                    average(
                        ecmwf.hourly.precipitation_probability[i],
                        gfs.hourly.precipitation_probability[i]
                    )
                ),

            rain:
                average(
                    ecmwf.hourly.precipitation[i],
                    gfs.hourly.precipitation[i]
                ),

            code:
                ecmwf.hourly.weather_code[i] ??
                gfs.hourly.weather_code[i],

            wind:
                average(
                    ecmwf.hourly.wind_speed_10m[i],
                    gfs.hourly.wind_speed_10m[i]
                ),

            windDir:
                windDirection(
                    ecmwf.hourly.wind_direction_10m[i] ??
                    gfs.hourly.wind_direction_10m[i]
                ),

            isDay:
                ecmwf.hourly.is_day[i]

        });

    }


    return {
        daily:daily,
        hourly:hourly
    };

}


/* =========================================================
   CURRENT WEATHER
========================================================= */

function renderCurrent(data){

    const now =
        new Date();

    let nearest =
        data.hourly[0];

    let bestDiff =
        Infinity;


    data.hourly.forEach(hour => {

        const diff =
            Math.abs(
                new Date(hour.time) - now
            );

        if(diff < bestDiff){

            bestDiff = diff;

            nearest = hour;

        }

    });


    const icon =
        weatherIcon(
            nearest.code,
            nearest.isDay
        );


    const text =
        weatherText(nearest.code);


    document.getElementById("current").innerHTML = `

        <div class="current-temp">
            ${Math.round(nearest.temp)}°
        </div>

        <div class="current-condition">
            ${icon} ${text}
        </div>

        <div class="current-details">

            <span>
                🌧️ Υετός:
                ${nearest.precip}%
            </span>

            <span>
                💨 Άνεμος:
                ${Math.round(nearest.wind)} km/h
                ${nearest.windDir}
            </span>

        </div>
    `;

}


/* =========================================================
   15 DAYS
========================================================= */

function renderForecast(data){

    const container =
        document.getElementById("forecast");

    container.innerHTML = "";


    data.daily.forEach((day,index) => {

        const date =
            new Date(day.date + "T12:00:00");


        const dayName =
            date.toLocaleDateString(
                "el-GR",
                {weekday:"long"}
            );


        const dateText =
            date.toLocaleDateString(
                "el-GR",
                {
                    day:"numeric",
                    month:"short"
                }
            );


        /*
        ΥΕΤΟΣ:
        30% και πάνω -> emoji υετού.
        Κάτω από 30% -> δεν βάζουμε emoji βροχής.
        */

        let precipitationText =
            `💧 ${day.precip}%`;

        if(day.precip >= 30){

            precipitationText =
                `🌧️ ${day.precip}%`;

        }


        const div =
            document.createElement("div");

        div.className = "day";

        div.innerHTML = `

            <div class="day-name">
                ${dayName}
            </div>

            <div class="day-date">
                ${dateText}
            </div>

            <div class="icon">
                ${weatherIcon(day.code,true)}
            </div>

            <div class="temps">
                <span class="max">
                    ${day.max}°
                </span>

                <span class="min">
                    ${day.min}°
                </span>
            </div>

            <div class="precip">
                ${precipitationText}
            </div>

            <div class="wind">
                💨 ${day.wind} km/h ${day.windDir}
            </div>

        `;


        div.onclick = () => {

            document
                .querySelectorAll(".day")
                .forEach(x =>
                    x.classList.remove("selected")
                );

            div.classList.add("selected");

            showDayDetails(index);

        };


        container.appendChild(div);

    });

}


/* =========================================================
   SELECTED DAY HOURLY
========================================================= */

function showDayDetails(dayIndex){

    const day =
        forecastData.daily[dayIndex];

    const details =
        document.getElementById("details");


    const dateStart =
        day.date;


    const hours =
        forecastData.hourly.filter(hour =>
            hour.time.startsWith(dateStart)
        );


    let html = `

        <h2>
            ${new Date(
                day.date + "T12:00:00"
            ).toLocaleDateString(
                "el-GR",
                {
                    weekday:"long",
                    day:"numeric",
                    month:"long"
                }
            )}
        </h2>

        <div class="hourly">
    `;


    hours.forEach(hour => {

        const time =
            hour.time.substring(11,16);


        let precipIcon = "";

        if(hour.precip >= 30){

            precipIcon = "🌧️";

        }


        html += `

            <div class="hour">

                <div class="hour-time">
                    ${time}
                </div>

                <div class="hour-icon">
                    ${weatherIcon(
                        hour.code,
                        hour.isDay
                    )}
                </div>

                <div class="hour-temp">
                    ${Math.round(hour.temp)}°
                </div>

                <div>
                    ${precipIcon}
                    ${hour.precip}%
                </div>

                <div class="hour-wind">
                    💨 ${Math.round(hour.wind)}
                    km/h
                    ${hour.windDir}
                </div>

            </div>

        `;

    });


    html += `
        </div>
    `;


    details.innerHTML = html;

    details.style.display = "block";

    details.scrollIntoView({
        behavior:"smooth",
        block:"start"
    });

}


/* =========================================================
   ERROR
========================================================= */

function showError(message){

    const error =
        document.getElementById("error");

    error.textContent = message;

    error.style.display = "block";

}


function hideError(){

    document.getElementById("error")
        .style.display = "none";

}


/* =========================================================
   BASIC HTML SAFETY
========================================================= */

function escapeHTML(text){

    return String(text)
        .replaceAll("&","&amp;")
        .replaceAll("<","&lt;")
        .replaceAll(">","&gt;")
        .replaceAll('"',"&quot;")
        .replaceAll("'","&#039;");

}


/* =========================================================
   ENTER KEY
========================================================= */

document
    .getElementById("searchInput")
    .addEventListener(
        "keydown",
        function(event){

            if(event.key === "Enter"){

                searchLocation();

            }

        }
    );


/* =========================================================
   AUTO REFRESH
   Κάθε 2 ώρες.
   ========================================================= */

setInterval(() => {

    loadWeather(currentLocation);

}, 2 * 60 * 60 * 1000);


/* =========================================================
   START
========================================================= */

loadWeather(currentLocation);

</script>

</body>
</html>
