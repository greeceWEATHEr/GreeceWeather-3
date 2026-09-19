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
    background:
        radial-gradient(circle at top,#123d70 0%,#071d38 42%,#03101f 100%);
    color:white;
    min-height:100vh;
}

.container{
    width:min(1450px,94%);
    margin:auto;
    padding:25px 0 50px;
}

/* HEADER */

header{
    text-align:center;
    margin-bottom:22px;
}

h1{
    margin:0;
    font-size:38px;
    font-weight:800;
}

.subtitle{
    margin-top:7px;
    color:#b9d5f2;
    font-size:15px;
}

/* SEARCH */

.search-box{
    display:flex;
    gap:10px;
    max-width:800px;
    margin:25px auto;
}

.search-box input{
    flex:1;
    padding:15px 18px;
    border:1px solid rgba(255,255,255,.15);
    border-radius:15px;
    background:rgba(255,255,255,.09);
    color:white;
    outline:none;
    font-size:16px;
}

.search-box input::placeholder{
    color:#b5c8dd;
}

.search-box button{
    padding:0 24px;
    border:none;
    border-radius:15px;
    background:#2587e8;
    color:white;
    font-size:16px;
    font-weight:bold;
    cursor:pointer;
}

.search-box button:hover{
    background:#3198f8;
}

/* LOCATION */

.location{
    text-align:center;
    margin:20px 0 24px;
}

.location-title{
    display:flex;
    align-items:center;
    justify-content:center;
    gap:10px;
    font-size:29px;
    font-weight:800;
}

.flag{
    font-size:30px;
}

.country{
    margin-top:5px;
    color:#b8cde4;
    font-size:16px;
}

/* CURRENT */

.current{
    background:linear-gradient(
        135deg,
        rgba(35,130,225,.30),
        rgba(8,38,72,.72)
    );
    border:1px solid rgba(255,255,255,.13);
    border-radius:25px;
    padding:24px;
    display:flex;
    align-items:center;
    justify-content:space-between;
    gap:25px;
    margin-bottom:25px;
    box-shadow:0 12px 35px rgba(0,0,0,.25);
}

.current-left{
    display:flex;
    align-items:center;
    gap:22px;
}

.current-icon{
    width:110px;
    height:110px;
}

.current-temp{
    font-size:60px;
    font-weight:800;
}

.current-condition{
    font-size:18px;
    color:#d4e5f6;
    margin-top:4px;
}

.current-details{
    display:grid;
    grid-template-columns:repeat(2,1fr);
    gap:10px 25px;
    color:#d3e4f5;
    font-size:15px;
}

.detail strong{
    color:white;
}

/* SECTION */

.section-title{
    font-size:23px;
    font-weight:800;
    margin:25px 0 14px;
}

/* DAILY FORECAST */

.forecast-grid{
    display:grid;

    /* ΑΚΡΙΒΩΣ 6 ΚΟΥΤΑΚΙΑ ΑΝΑ ΣΕΙΡΑ */
    grid-template-columns:repeat(6,minmax(0,1fr));

    gap:14px;
    width:100%;
}

.forecast-card{
    min-width:0;
    background:rgba(255,255,255,.075);
    border:1px solid rgba(255,255,255,.12);
    border-radius:19px;
    padding:15px 10px;
    text-align:center;
    cursor:pointer;
    transition:.2s;
    position:relative;
    overflow:hidden;
}

.forecast-card:hover{
    transform:translateY(-3px);
    background:rgba(255,255,255,.12);
    border-color:rgba(90,170,255,.65);
}

.forecast-card.selected{
    background:rgba(38,135,232,.22);
    border-color:#4da6ff;
}

.day-name{
    font-size:16px;
    font-weight:800;
}

.date{
    font-size:12px;
    color:#9fb8d2;
    margin-top:4px;
}

.weather-main-icon{
    width:70px;
    height:70px;
    margin:10px auto 4px;
}

.weather-main-icon svg{
    width:100%;
    height:100%;
}

.temp-max{
    font-size:25px;
    font-weight:800;
}

.temp-min{
    font-size:17px;
    color:#9fc0df;
    margin-top:2px;
}

.precipitation-symbol{
    width:34px;
    height:34px;
    margin:8px auto 0;
}

.precipitation-symbol svg{
    width:100%;
    height:100%;
}

.precipitation-probability{
    font-size:12px;
    color:#b7cee5;
    margin-top:3px;
}

.wind-info{
    font-size:12px;
    color:#a9c3dd;
    margin-top:9px;
}

/* PRECIPITATION ICON */

.precip-icon{
    width:100%;
    height:100%;
}

.snow-icon{
    color:#eaf7ff;
    filter:drop-shadow(0 0 4px rgba(220,245,255,.45));
}

.rain-icon{
    color:#69baff;
}

.storm-icon{
    color:#a9cfff;
}

/* HOURLY */

.hourly-container{
    margin-top:18px;
    background:rgba(255,255,255,.055);
    border:1px solid rgba(255,255,255,.11);
    border-radius:22px;
    padding:18px;
}

.hourly-title{
    font-size:19px;
    font-weight:800;
    margin-bottom:14px;
}

.hourly-scroll{
    display:flex;
    gap:10px;
    overflow-x:auto;
    padding-bottom:7px;
}

.hour-card{
    flex:0 0 112px;
    background:rgba(255,255,255,.07);
    border:1px solid rgba(255,255,255,.10);
    border-radius:15px;
    padding:12px 8px;
    text-align:center;
}

.hour-time{
    font-weight:800;
    font-size:14px;
}

.hour-icon{
    width:50px;
    height:50px;
    margin:8px auto;
}

.hour-icon svg{
    width:100%;
    height:100%;
}

.hour-temp{
    font-size:19px;
    font-weight:800;
}

.hour-rain{
    font-size:12px;
    color:#b7cee5;
    margin-top:5px;
}

.hour-wind{
    font-size:12px;
    color:#a8c4df;
    margin-top:5px;
}

/* ERROR */

.error{
    display:none;
    text-align:center;
    background:rgba(180,40,40,.18);
    border:1px solid rgba(255,100,100,.35);
    color:#ffd2d2;
    padding:13px;
    border-radius:13px;
    margin:15px auto;
    max-width:800px;
}

/* LOADING */

.loading{
    text-align:center;
    color:#b9d0e8;
    padding:25px;
}

/* RESPONSIVE */

@media(max-width:900px){
    .forecast-grid{
        grid-template-columns:repeat(3,minmax(0,1fr));
    }

    .current{
        flex-direction:column;
        text-align:center;
    }

    .current-left{
        flex-direction:column;
    }
}

@media(max-width:600px){
    .container{
        width:95%;
    }

    h1{
        font-size:30px;
    }

    .search-box{
        flex-direction:column;
    }

    .search-box button{
        padding:14px;
    }

    .forecast-grid{
        grid-template-columns:repeat(2,minmax(0,1fr));
    }

    .current-temp{
        font-size:48px;
    }

    .current-details{
        width:100%;
    }
}
</style>
</head>

<body>

<div class="container">

<header>
    <h1>🌤️ Greece Weather</h1>
    <div class="subtitle">
        15ήμερη πρόγνωση με συνδυασμό ECMWF + GFS
    </div>
</header>

<div class="search-box">
    <input
        id="searchInput"
        type="text"
        placeholder="Αναζήτησε πόλη ή περιοχή οπουδήποτε στον κόσμο..."
    >
    <button onclick="searchLocation()">Αναζήτηση</button>
</div>

<div id="error" class="error"></div>

<div id="loading" class="loading">
    Φόρτωση δεδομένων...
</div>

<div id="weatherContent" style="display:none;">

    <div class="location">
        <div class="location-title">
            <span id="locationName"></span>
            <span id="locationFlag" class="flag"></span>
        </div>
        <div id="countryName" class="country"></div>
    </div>

    <div class="current">

        <div class="current-left">

            <div id="currentIcon" class="current-icon"></div>

            <div>
                <div id="currentTemp" class="current-temp">--°</div>
                <div id="currentCondition" class="current-condition">
                    --
                </div>
            </div>

        </div>

        <div class="current-details">

            <div class="detail">
                Αίσθηση:
                <strong id="feels">--</strong>
            </div>

            <div class="detail">
                Υγρασία:
                <strong id="humidity">--</strong>
            </div>

            <div class="detail">
                Άνεμος:
                <strong id="wind">--</strong>
            </div>

            <div class="detail">
                Κατεύθυνση:
                <strong id="windDir">--</strong>
            </div>

            <div class="detail">
                Ανατολή:
                <strong id="sunrise">--</strong>
            </div>

            <div class="detail">
                Δύση:
                <strong id="sunset">--</strong>
            </div>

        </div>

    </div>

    <div class="section-title">
        15ήμερη πρόγνωση
    </div>

    <div id="forecastGrid" class="forecast-grid"></div>

    <div id="hourlyContainer" class="hourly-container">
        <div id="hourlyTitle" class="hourly-title">
            Ωριαία πρόγνωση
        </div>

        <div id="hourlyScroll" class="hourly-scroll"></div>
    </div>

</div>

</div>

<script>

/* =========================================================
   ΒΑΣΙΚΕΣ ΡΥΘΜΙΣΕΙΣ
========================================================= */

let currentLocation = null;
let currentWeather = null;


/* =========================================================
   ΗΜΕΡΕΣ
========================================================= */

const dayNames = [
    "Κυριακή",
    "Δευτέρα",
    "Τρίτη",
    "Τετάρτη",
    "Πέμπτη",
    "Παρασκευή",
    "Σάββατο"
];


/* =========================================================
   WMO WEATHER CODES
========================================================= */

function weatherDescription(code){

    const map = {

        0:"Καθαρός ουρανός",
        1:"Κυρίως αίθριος",
        2:"Λίγες νεφώσεις",
        3:"Συννεφιά",

        45:"Ομίχλη",
        48:"Παγωμένη ομίχλη",

        51:"Ασθενής ψιχάλα",
        53:"Ψιχάλα",
        55:"Ισχυρή ψιχάλα",

        56:"Παγωμένη ψιχάλα",
        57:"Ισχυρή παγωμένη ψιχάλα",

        61:"Ασθενής βροχή",
        63:"Βροχή",
        65:"Ισχυρή βροχή",

        66:"Παγωμένη βροχή",
        67:"Ισχυρή παγωμένη βροχή",

        71:"Ασθενής χιονόπτωση",
        73:"Χιονόπτωση",
        75:"Ισχυρή χιονόπτωση",
        77:"Χιονοκόκκοι",

        80:"Ασθενείς μπόρες",
        81:"Μπόρες",
        82:"Ισχυρές μπόρες",

        85:"Ασθενείς χιονομπόρες",
        86:"Ισχυρές χιονομπόρες",

        95:"Καταιγίδα",
        96:"Καταιγίδα με χαλάζι",
        99:"Ισχυρή καταιγίδα με χαλάζι"
    };

    return map[code] || "Άγνωστες συνθήκες";
}


/* =========================================================
   FLAG
========================================================= */

function countryFlag(code){

    if(!code) return "";

    code = code.toUpperCase();

    if(code.length !== 2) return "";

    return [...code]
        .map(c => String.fromCodePoint(127397 + c.charCodeAt(0)))
        .join("");
}


/* =========================================================
   WIND DIRECTION
========================================================= */

function windDirection(deg){

    if(deg === null || deg === undefined)
        return "--";

    const dirs = [
        "Β",
        "ΒΑ",
        "Α",
        "ΝΑ",
        "Ν",
        "ΝΔ",
        "Δ",
        "ΒΔ"
    ];

    return dirs[
        Math.round(deg / 45) % 8
    ];
}


/* =========================================================
   SVG WEATHER ICONS
   ΕΝΙΑΙΑ ΕΙΚΟΝΙΔΙΑ — ΟΧΙ ΚΟΛΛΗΜΕΝΑ EMOJIS
========================================================= */

function weatherSVG(code,isDay=true){

    const moon = `
        <circle cx="30" cy="30" r="17"
            fill="none"
            stroke="#dfeaff"
            stroke-width="4"/>
        <circle cx="37" cy="24" r="17"
            fill="#071d38"/>
    `;

    const sun = `
        <circle cx="32" cy="32" r="11"
            fill="#ffd45a"/>

        <g stroke="#ffd45a"
           stroke-width="3"
           stroke-linecap="round">

            <path d="M32 6v8"/>
            <path d="M32 50v8"/>
            <path d="M6 32h8"/>
            <path d="M50 32h8"/>

            <path d="M14 14l6 6"/>
            <path d="M44 44l6 6"/>
            <path d="M50 14l-6 6"/>
            <path d="M20 44l-6 6"/>
        </g>
    `;

    const cloud = `
        <path d="M18 45
                 C11 45 8 41 9 35
                 C10 29 15 26 21 27
                 C23 19 30 15 37 17
                 C44 18 48 23 48 30
                 C54 30 57 34 56 39
                 C55 43 52 45 47 45Z"
              fill="#dce9f5"/>
    `;

    const darkCloud = `
        <path d="M18 45
                 C11 45 8 41 9 35
                 C10 29 15 26 21 27
                 C23 19 30 15 37 17
                 C44 18 48 23 48 30
                 C54 30 57 34 56 39
                 C55 43 52 45 47 45Z"
              fill="#aab9c9"/>
    `;

    const rain = `
        <g stroke="#63b9ff"
           stroke-width="4"
           stroke-linecap="round">
            <path d="M21 50l-4 8"/>
            <path d="M33 50l-4 8"/>
            <path d="M45 50l-4 8"/>
        </g>
    `;

    /* ΠΙΟ ΡΕΑΛΙΣΤΙΚΟ ΧΙΟΝΙ */
    const snow = `
        <g stroke="#f2fbff"
           stroke-width="2.8"
           stroke-linecap="round"
           fill="none">

            <path d="M20 49v10"/>
            <path d="M15 54h10"/>
            <path d="M16.5 50.5l7 7"/>
            <path d="M23.5 50.5l-7 7"/>

            <path d="M33 49v10"/>
            <path d="M28 54h10"/>
            <path d="M29.5 50.5l7 7"/>
            <path d="M36.5 50.5l-7 7"/>

            <path d="M46 49v10"/>
            <path d="M41 54h10"/>
            <path d="M42.5 50.5l7 7"/>
            <path d="M49.5 50.5l-7 7"/>
        </g>
    `;

    const lightning = `
        <path d="M34 43l-8 11h7l-4 9 12-15h-7z"
              fill="#ffe45e"/>
    `;


    /* ΚΑΘΑΡΗ ΗΜΕΡΑ */

    if(code === 0){

        return `
        <svg viewBox="0 0 64 64">
            ${isDay ? sun : moon}
        </svg>`;
    }


    /* ΛΙΓΕΣ ΝΕΦΩΣΕΙΣ */

    if(code === 1 || code === 2){

        return `
        <svg viewBox="0 0 64 64">

            ${isDay ? sun : moon}

            <path d="M19 48
                     C12 48 9 44 10 39
                     C11 34 15 32 21 33
                     C23 27 29 24 35 26
                     C41 27 44 32 44 37
                     C49 37 53 40 52 44
                     C51 47 48 48 44 48Z"
                  fill="#cbd9e7"/>

        </svg>`;
    }


    /* ΠΛΗΡΗΣ ΣΥΝΝΕΦΙΑ */

    if(code === 3){

        return `
        <svg viewBox="0 0 64 64">
            ${darkCloud}
        </svg>`;
    }


    /* ΟΜΙΧΛΗ */

    if(code === 45 || code === 48){

        return `
        <svg viewBox="0 0 64 64">

            <g stroke="#c6d4e1"
               stroke-width="4"
               stroke-linecap="round">

                <path d="M10 25h44"/>
                <path d="M7 34h50"/>
                <path d="M12 43h40"/>

            </g>

        </svg>`;
    }


    /* ΒΡΟΧΗ */

    if(
        [51,53,55,56,57,61,63,65,66,67,80,81,82]
        .includes(code)
    ){

        return `
        <svg viewBox="0 0 64 64">

            ${isDay ? sun : moon}

            ${darkCloud}

            ${rain}

        </svg>`;
    }


    /* ΧΙΟΝΙ */

    if(
        [71,73,75,77,85,86]
        .includes(code)
    ){

        return `
        <svg viewBox="0 0 64 64">

            ${isDay ? sun : moon}

            ${darkCloud}

            ${snow}

        </svg>`;
    }


    /* ΚΑΤΑΙΓΙΔΑ */

    if([95,96,99].includes(code)){

        return `
        <svg viewBox="0 0 64 64">

            ${darkCloud}

            ${rain}

            ${lightning}

        </svg>`;
    }


    return `
    <svg viewBox="0 0 64 64">
        ${isDay ? sun : moon}
    </svg>`;
}


/* =========================================================
   PRECIPITATION ICON
   ΚΡΙΣΙΜΟ:
   ΚΑΤΩ ΑΠΟ 30% -> ΚΑΝΕΝΑ ΕΙΚΟΝΙΔΙΟ ΥΕΤΟΥ
========================================================= */

function precipitationIcon(code,probability){

    /* ΑΠΟΛΥΤΟ ΟΡΙΟ 30% */

    if(
        probability === null ||
        probability === undefined ||
        Number(probability) < 30
    ){
        return "";
    }


    /* ΧΙΟΝΙ */

    if(
        [71,73,75,77,85,86]
        .includes(code)
    ){

        return `
        <svg class="precip-icon snow-icon"
             viewBox="0 0 64 64">

            <g
                fill="none"
                stroke="currentColor"
                stroke-width="3"
                stroke-linecap="round"
                stroke-linejoin="round">

                <path d="M18 8v18"/>
                <path d="M9 13l18 10"/>
                <path d="M27 13L9 23"/>

                <path d="M42 20v18"/>
                <path d="M33 25l18 10"/>
                <path d="M51 25L33 35"/>

                <path d="M29 35v20"/>
                <path d="M19 40l20 11"/>
                <path d="M39 40L19 51"/>

            </g>

            <circle
                cx="18"
                cy="8"
                r="2"
                fill="currentColor"/>

            <circle
                cx="42"
                cy="20"
                r="2"
                fill="currentColor"/>

            <circle
                cx="29"
                cy="35"
                r="2"
                fill="currentColor"/>

        </svg>`;
    }


    /* ΒΡΟΧΗ */

    if(
        [51,53,55,56,57,61,63,65,66,67,80,81,82]
        .includes(code)
    ){

        return `
        <svg class="precip-icon rain-icon"
             viewBox="0 0 64 64">

            <path
                d="M18 35
                   C10 35 7 30 9 24
                   C11 18 17 16 22 18
                   C25 11 32 8 39 11
                   C46 13 49 19 48 25
                   C54 25 57 29 56 34
                   C55 39 51 41 46 41
                   H18Z"
                fill="currentColor"/>

            <path
                d="M20 46l-4 9"
                stroke="currentColor"
                stroke-width="4"
                stroke-linecap="round"/>

            <path
                d="M32 46l-4 9"
                stroke="currentColor"
                stroke-width="4"
                stroke-linecap="round"/>

            <path
                d="M44 46l-4 9"
                stroke="currentColor"
                stroke-width="4"
                stroke-linecap="round"/>

        </svg>`;
    }


    /* ΚΑΤΑΙΓΙΔΑ */

    if([95,96,99].includes(code)){

        return `
        <svg class="precip-icon storm-icon"
             viewBox="0 0 64 64">

            <path
                d="M18 34
                   C10 34 8 29 10 23
                   C12 18 17 16 22 18
                   C25 11 33 9 39 12
                   C46 14 49 19 48 25
                   C53 25 56 29 55 34
                   C54 39 50 41 45 41
                   H18Z"
                fill="currentColor"/>

            <path
                d="M35 39l-9 14h8l-4 10 13-17h-8z"
                fill="#ffe35b"/>

        </svg>`;
    }


    /* ΟΤΙΔΗΠΟΤΕ ΑΛΛΟ -> ΚΑΝΕΝΑ */

    return "";
}


/* =========================================================
   MODEL DATA
========================================================= */

async function getModelData(lat,lon,model){

    const url =
        `https://api.open-meteo.com/v1/forecast` +
        `?latitude=${lat}` +
        `&longitude=${lon}` +
        `&timezone=auto` +
        `&forecast_days=15` +
        `&models=${model}` +

        `&current=temperature_2m,relative_humidity_2m,apparent_temperature,weather_code,wind_speed_10m,wind_direction_10m` +

        `&hourly=temperature_2m,precipitation_probability,precipitation,weather_code,wind_speed_10m,wind_direction_10m` +

        `&daily=weather_code,temperature_2m_max,temperature_2m_min,precipitation_probability_max,precipitation_sum,wind_speed_10m_max,wind_direction_10m_dominant,sunrise,sunset`;

    const response = await fetch(url);

    if(!response.ok){
        throw new Error("Weather API error");
    }

    return await response.json();
}


/* =========================================================
   AVERAGE TWO MODELS
========================================================= */

function average(a,b){

    if(a == null && b == null)
        return null;

    if(a == null)
        return a;

    if(b == null)
        return b;

    return (Number(a)+Number(b))/2;
}


/*
Δεν κάνουμε αριθμητικό μέσο όρο στους WMO weather codes,
γιατί είναι κατηγορικές τιμές και όχι θερμοκρασίες.
Χρησιμοποιούμε τον ECMWF ως βασικό condition code,
ενώ οι αριθμητικές μεταβλητές παίρνουν μέσο όρο.
*/

function mergeModels(ecmwf,gfs){

    const daily = [];

    for(let i=0;i<15;i++){

        const e = ecmwf.daily;
        const g = gfs.daily;

        daily.push({

            time:e.time[i],

            weather_code:
                e.weather_code[i] ?? g.weather_code[i],

            temperature_2m_max:
                average(
                    e.temperature_2m_max[i],
                    g.temperature_2m_max[i]
                ),

            temperature_2m_min:
                average(
                    e.temperature_2m_min[i],
                    g.temperature_2m_min[i]
                ),

            precipitation_probability_max:
                average(
                    e.precipitation_probability_max[i],
                    g.precipitation_probability_max[i]
                ),

            precipitation_sum:
                average(
                    e.precipitation_sum[i],
                    g.precipitation_sum[i]
                ),

            wind_speed_10m_max:
                average(
                    e.wind_speed_10m_max[i],
                    g.wind_speed_10m_max[i]
                ),

            wind_direction_10m_dominant:
                average(
                    e.wind_direction_10m_dominant[i],
                    g.wind_direction_10m_dominant[i]
                ),

            sunrise:e.sunrise[i],
            sunset:e.sunset[i]
        });
    }


    const hourly = [];

    for(let i=0;i<ecmwf.hourly.time.length;i++){

        hourly.push({

            time:ecmwf.hourly.time[i],

            temperature_2m:
                average(
                    ecmwf.hourly.temperature_2m[i],
                    gfs.hourly.temperature_2m[i]
                ),

            precipitation_probability:
                average(
                    ecmwf.hourly.precipitation_probability[i],
                    gfs.hourly.precipitation_probability[i]
                ),

            precipitation:
                average(
                    ecmwf.hourly.precipitation[i],
                    gfs.hourly.precipitation[i]
                ),

            weather_code:
                ecmwf.hourly.weather_code[i],

            wind_speed_10m:
                average(
                    ecmwf.hourly.wind_speed_10m[i],
                    gfs.hourly.wind_speed_10m[i]
                ),

            wind_direction_10m:
                average(
                    ecmwf.hourly.wind_direction_10m[i],
                    gfs.hourly.wind_direction_10m[i]
                )
        });
    }


    return {
        daily,
        hourly,

        current:{

            temperature_2m:
                average(
                    ecmwf.current.temperature_2m,
                    gfs.current.temperature_2m
                ),

            relative_humidity_2m:
                average(
                    ecmwf.current.relative_humidity_2m,
                    gfs.current.relative_humidity_2m
                ),

            apparent_temperature:
                average(
                    ecmwf.current.apparent_temperature,
                    gfs.current.apparent_temperature
                ),

            weather_code:
                ecmwf.current.weather_code,

            wind_speed_10m:
                average(
                    ecmwf.current.wind_speed_10m,
                    gfs.current.wind_speed_10m
                ),

            wind_direction_10m:
                average(
                    ecmwf.current.wind_direction_10m,
                    gfs.current.wind_direction_10m
                )
        }
    };
}


/* =========================================================
   SEARCH LOCATION
========================================================= */

async function searchLocation(){

    const input =
        document.getElementById("searchInput");

    const query =
        input.value.trim();

    if(!query){
        showError("Γράψε μια πόλη ή περιοχή.");
        return;
    }

    hideError();

    document.getElementById("loading").style.display="block";
    document.getElementById("weatherContent").style.display="none";


    try{

        const url =
            `https://geocoding-api.open-meteo.com/v1/search` +
            `?name=${encodeURIComponent(query)}` +
            `&count=8` +
            `&language=el` +
            `&format=json`;

        const response = await fetch(url);

        if(!response.ok){
            throw new Error();
        }

        const data = await response.json();

        if(!data.results || data.results.length === 0){
            throw new Error("Δεν βρέθηκε η περιοχή.");
        }


        /*
        Προτιμάμε ακριβές αποτέλεσμα.
        */

        let place = data.results.find(
            x =>
                x.name &&
                x.name.toLowerCase() === query.toLowerCase()
        );

        if(!place){
            place = data.results[0];
        }


        currentLocation = place;

        await loadWeather();

    }catch(error){

        showError(
            "Δεν βρέθηκε η περιοχή. Δοκίμασε άλλη ονομασία."
        );

        document.getElementById("loading").style.display="none";
    }
}


/* =========================================================
   LOAD WEATHER
========================================================= */

async function loadWeather(){

    if(!currentLocation)
        return;

    const lat = currentLocation.latitude;
    const lon = currentLocation.longitude;


    try{

        const [ecmwf,gfs] = await Promise.all([

            getModelData(
                lat,
                lon,
                "ecmwf_ifs025"
            ),

            getModelData(
                lat,
                lon,
                "gfs"
            )

        ]);


        currentWeather =
            mergeModels(ecmwf,gfs);


        renderLocation();
        renderCurrent();
        renderForecast();


        document.getElementById("loading").style.display="none";
        document.getElementById("weatherContent").style.display="block";


    }catch(error){

        console.error(error);

        showError(
            "Δεν ήταν δυνατή η φόρτωση των δεδομένων καιρού."
        );

        document.getElementById("loading").style.display="none";
    }
}


/* =========================================================
   LOCATION
========================================================= */

function renderLocation(){

    document.getElementById("locationName").textContent =
        currentLocation.name || "--";

    document.getElementById("countryName").textContent =
        currentLocation.country || "--";

    document.getElementById("locationFlag").textContent =
        countryFlag(currentLocation.country_code);
}


/* =========================================================
   CURRENT
========================================================= */

function renderCurrent(){

    const c = currentWeather.current;

    const now = new Date();

    const hour = now.getHours();

    const isDay =
        hour >= 7 && hour < 20;


    document.getElementById("currentTemp").textContent =
        Math.round(c.temperature_2m) + "°";


    document.getElementById("currentCondition").textContent =
        weatherDescription(c.weather_code);


    document.getElementById("feels").textContent =
        Math.round(c.apparent_temperature) + "°";


    document.getElementById("humidity").textContent =
        Math.round(c.relative_humidity_2m) + "%";


    document.getElementById("wind").textContent =
        Math.round(c.wind_speed_10m) + " km/h";


    document.getElementById("windDir").textContent =
        windDirection(c.wind_direction_10m);


    document.getElementById("currentIcon").innerHTML =
        weatherSVG(
            c.weather_code,
            isDay
        );


    const today =
        currentWeather.daily[0];

    document.getElementById("sunrise").textContent =
        today.sunrise
            ? today.sunrise.slice(11,16)
            : "--";


    document.getElementById("sunset").textContent =
        today.sunset
            ? today.sunset.slice(11,16)
            : "--";
}


/* =========================================================
   DAILY FORECAST
   ΑΚΡΙΒΩΣ 15 ΚΟΥΤΑΚΙΑ
   6 + 6 + 3
========================================================= */

function renderForecast(){

    const grid =
        document.getElementById("forecastGrid");

    grid.innerHTML="";


    currentWeather.daily.forEach(
        (day,index)=>{

            const date =
                new Date(day.time+"T12:00:00");


            const dayName =
                dayNames[date.getDay()];


            const dateText =
                date.toLocaleDateString(
                    "el-GR",
                    {
                        day:"2-digit",
                        month:"2-digit"
                    }
                );


            /*
            Κρίσιμο:
            Αν η πιθανότητα είναι κάτω από 30%,
            precipitationIcon() επιστρέφει κενό.
            */

            const precip =
                precipitationIcon(
                    day.weather_code,
                    day.precipitation_probability_max
                );


            const card =
                document.createElement("div");


            card.className =
                "forecast-card";


            card.dataset.index =
                index;


            card.innerHTML = `

                <div class="day-name">
                    ${dayName}
                </div>

                <div class="date">
                    ${dateText}
                </div>

                <div class="weather-main-icon">
                    ${weatherSVG(
                        day.weather_code,
                        true
                    )}
                </div>

                <div class="temp-max">
                    ${Math.round(
                        day.temperature_2m_max
                    )}°
                </div>

                <div class="temp-min">
                    ${Math.round(
                        day.temperature_2m_min
                    )}°
                </div>

                ${
                    precip
                    ?
                    `
                    <div class="precipitation-symbol">
                        ${precip}
                    </div>
                    `
                    :
                    ""
                }

                <div class="precipitation-probability">
                    ${Math.round(
                        day.precipitation_probability_max
                    )}%
                </div>

                <div class="wind-info">
                    ${Math.round(
                        day.wind_speed_10m_max
                    )} km/h
                    ·
                    ${windDirection(
                        day.wind_direction_10m_dominant
                    )}
                </div>
            `;


            card.addEventListener(
                "click",
                ()=>{
                    document
                        .querySelectorAll(".forecast-card")
                        .forEach(
                            x=>x.classList.remove("selected")
                        );

                    card.classList.add("selected");

                    renderHourly(index);
                }
            );


            grid.appendChild(card);
        }
    );


    /*
    Πρώτη ημέρα επιλεγμένη
    */

    const first =
        grid.querySelector(".forecast-card");

    if(first){
        first.classList.add("selected");
        renderHourly(0);
    }
}


/* =========================================================
   HOURLY FORECAST
========================================================= */

function renderHourly(dayIndex){

    const day =
        currentWeather.daily[dayIndex];


    document.getElementById("hourlyTitle").textContent =
        `Ωριαία πρόγνωση — ${dayNames[
            new Date(day.time+"T12:00:00").getDay()
        ]} ${new Date(day.time+"T12:00:00")
            .toLocaleDateString(
                "el-GR",
                {
                    day:"2-digit",
                    month:"2-digit"
                }
            )}`;


    const scroll =
        document.getElementById("hourlyScroll");

    scroll.innerHTML="";


    const hours =
        currentWeather.hourly.filter(
            h => h.time.startsWith(day.time)
        );


    hours.forEach(hour=>{

        const date =
            new Date(hour.time);


        const hourText =
            date.toLocaleTimeString(
                "el-GR",
                {
                    hour:"2-digit",
                    minute:"2-digit"
                }
            );


        const isDay =
            date.getHours() >= 7 &&
            date.getHours() < 20;


        /*
        ΚΑΙ ΕΔΩ:
        precipitationIcon() δεν βάζει
        βροχή/χιόνι κάτω από 30%.
        */

        const precip =
            precipitationIcon(
                hour.weather_code,
                hour.precipitation_probability
            );


        const card =
            document.createElement("div");

        card.className="hour-card";


        card.innerHTML = `

            <div class="hour-time">
                ${hourText}
            </div>

            <div class="hour-icon">
                ${weatherSVG(
                    hour.weather_code,
                    isDay
                )}
            </div>

            <div class="hour-temp">
                ${Math.round(
                    hour.temperature_2m
                )}°
            </div>

            ${
                precip
                ?
                `
                <div class="precipitation-symbol">
                    ${precip}
                </div>
                `
                :
                ""
            }

            <div class="hour-rain">
                ${Math.round(
                    hour.precipitation_probability
                )}%
            </div>

            <div class="hour-wind">
                ${Math.round(
                    hour.wind_speed_10m
                )} km/h
                ·
                ${windDirection(
                    hour.wind_direction_10m
                )}
            </div>

        `;


        scroll.appendChild(card);

    });
}


/* =========================================================
   ERRORS
========================================================= */

function showError(message){

    const error =
        document.getElementById("error");

    error.textContent=message;
    error.style.display="block";
}


function hideError(){

    document.getElementById("error")
        .style.display="none";
}


/* =========================================================
   ENTER ΣΤΗΝ ΑΝΑΖΗΤΗΣΗ
========================================================= */

document
    .getElementById("searchInput")
    .addEventListener(
        "keydown",
        event=>{

            if(event.key==="Enter"){
                searchLocation();
            }

        }
    );


/* =========================================================
   ΑΡΧΙΚΗ ΠΕΡΙΟΧΗ — ΘΕΣΣΑΛΟΝΙΚΗ
========================================================= */

currentLocation = {

    name:"Θεσσαλονίκη",

    latitude:40.6401,

    longitude:22.9444,

    country:"Ελλάδα",

    country_code:"GR"
};


loadWeather();


/* =========================================================
   ΑΝΑΝΕΩΣΗ
   ΚΑΘΕ 1 ΩΡΑ
   = 24 ΕΛΕΓΧΟΙ ΑΝΑ ΗΜΕΡΑ
========================================================= */

setInterval(
    ()=>{
        if(currentLocation){
            loadWeather();
        }
    },
    60 * 60 * 1000
);

</script>

</body>
</html>
