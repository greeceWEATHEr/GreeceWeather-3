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
    color:white;
    background:
        radial-gradient(circle at 50% 0%,#1761a5 0%,#0b315c 30%,#061a32 65%,#020b16 100%);
    min-height:100vh;
}

.container{
    width:94%;
    max-width:1450px;
    margin:auto;
    padding:25px 0 50px;
}

/* ================= HEADER ================= */

header{
    text-align:center;
    margin-bottom:22px;
}

h1{
    margin:0;
    font-size:40px;
    font-weight:800;
    letter-spacing:-1px;
}

.subtitle{
    margin-top:7px;
    color:#b9d8f5;
    font-size:15px;
}

/* ================= SEARCH ================= */

.search-box{
    max-width:850px;
    margin:25px auto;
    display:flex;
    gap:10px;
}

.search-box input{
    flex:1;
    height:52px;
    border-radius:15px;
    border:1px solid rgba(255,255,255,.16);
    outline:none;
    padding:0 18px;
    background:rgba(255,255,255,.10);
    color:white;
    font-size:16px;
}

.search-box input::placeholder{
    color:#b5cce4;
}

.search-box button{
    height:52px;
    border:0;
    border-radius:15px;
    padding:0 25px;
    background:linear-gradient(135deg,#1689f5,#1266c7);
    color:white;
    font-size:16px;
    font-weight:bold;
    cursor:pointer;
}

.search-box button:hover{
    filter:brightness(1.12);
}

/* ================= ERROR ================= */

.error{
    display:none;
    max-width:850px;
    margin:15px auto;
    padding:14px;
    text-align:center;
    border-radius:14px;
    background:rgba(220,50,50,.18);
    border:1px solid rgba(255,100,100,.35);
    color:#ffd4d4;
}

/* ================= LOCATION ================= */

.location{
    text-align:center;
    margin:20px 0 25px;
}

.location-title{
    display:flex;
    align-items:center;
    justify-content:center;
    gap:10px;
    font-size:30px;
    font-weight:800;
}

.flag{
    font-size:30px;
}

.country{
    margin-top:5px;
    color:#b8d0e8;
    font-size:16px;
}

/* ================= CURRENT ================= */

.current{
    display:flex;
    align-items:center;
    justify-content:space-between;
    gap:25px;

    padding:25px;

    border-radius:25px;

    background:
        linear-gradient(
            135deg,
            rgba(30,132,225,.34),
            rgba(4,31,61,.78)
        );

    border:1px solid rgba(255,255,255,.13);

    box-shadow:
        0 15px 45px rgba(0,0,0,.28);

    margin-bottom:28px;
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

.current-icon svg{
    width:100%;
    height:100%;
}

.current-temp{
    font-size:62px;
    font-weight:800;
}

.current-condition{
    color:#d3e7fa;
    font-size:18px;
    margin-top:4px;
}

.current-details{
    display:grid;
    grid-template-columns:repeat(2,1fr);
    gap:13px 30px;
    color:#c0d5e9;
}

.detail strong{
    color:white;
}

/* ================= TITLES ================= */

.section-title{
    font-size:24px;
    font-weight:800;
    margin:25px 0 15px;
}

/* ================= DAILY 6 / 6 / 3 ================= */

.forecast-grid{
    display:grid;

    /* 6 + 6 + 3 */
    grid-template-columns:
        repeat(6,minmax(0,1fr));

    gap:14px;
    width:100%;
}

.forecast-card{
    min-width:0;

    padding:15px 10px;

    text-align:center;

    border-radius:20px;

    background:
        linear-gradient(
            160deg,
            rgba(255,255,255,.105),
            rgba(255,255,255,.045)
        );

    border:1px solid rgba(255,255,255,.12);

    cursor:pointer;

    transition:
        transform .18s,
        background .18s,
        border .18s;
}

.forecast-card:hover{
    transform:translateY(-3px);
    background:rgba(40,145,235,.16);
    border-color:#48a8ff;
}

.forecast-card.selected{
    background:
        linear-gradient(
            160deg,
            rgba(30,140,245,.30),
            rgba(20,75,130,.24)
        );

    border-color:#52b0ff;
}

.day-name{
    font-size:16px;
    font-weight:800;
}

.date{
    margin-top:4px;
    color:#9fb9d4;
    font-size:12px;
}

.weather-main-icon{
    width:72px;
    height:72px;
    margin:10px auto 4px;
}

.weather-main-icon svg{
    width:100%;
    height:100%;
}

.temp-max{
    font-size:26px;
    font-weight:800;
}

.temp-min{
    font-size:17px;
    color:#9fc2e3;
    margin-top:2px;
}

.precipitation-symbol{
    width:35px;
    height:35px;
    margin:8px auto 0;
}

.precipitation-symbol svg{
    width:100%;
    height:100%;
}

.precipitation-probability{
    color:#b9d1e8;
    font-size:12px;
    margin-top:3px;
}

.wind-info{
    color:#abc4dc;
    font-size:12px;
    margin-top:9px;
}

/* ================= PRECIP ICONS ================= */

.rain-icon{
    color:#56b7ff;
}

.snow-icon{
    color:#f1fbff;

    filter:
        drop-shadow(0 0 4px rgba(230,248,255,.55));
}

.storm-icon{
    color:#9ccfff;
}

/* ================= HOURLY ================= */

.hourly-container{
    margin-top:20px;

    padding:19px;

    border-radius:23px;

    background:
        rgba(255,255,255,.055);

    border:1px solid rgba(255,255,255,.11);
}

.hourly-title{
    font-size:20px;
    font-weight:800;
    margin-bottom:15px;
}

.hourly-scroll{
    display:flex;
    gap:10px;
    overflow-x:auto;
    padding-bottom:8px;
}

.hour-card{
    flex:0 0 112px;

    padding:12px 8px;

    text-align:center;

    border-radius:16px;

    background:rgba(255,255,255,.075);
    border:1px solid rgba(255,255,255,.10);
}

.hour-time{
    font-size:14px;
    font-weight:800;
}

.hour-icon{
    width:52px;
    height:52px;
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
    color:#b9d2e9;
    font-size:12px;
    margin-top:5px;
}

.hour-wind{
    color:#aac5df;
    font-size:12px;
    margin-top:5px;
}

/* ================= LOADING ================= */

.loading{
    text-align:center;
    padding:25px;
    color:#bcd4eb;
}

/* ================= RESPONSIVE ================= */

@media(max-width:950px){

    .forecast-grid{
        grid-template-columns:
            repeat(3,minmax(0,1fr));
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

    h1{
        font-size:31px;
    }

    .search-box{
        flex-direction:column;
    }

    .search-box button{
        width:100%;
    }

    .forecast-grid{
        grid-template-columns:
            repeat(2,minmax(0,1fr));
    }

    .current-temp{
        font-size:50px;
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
15ήμερη πρόγνωση με ECMWF + GFS
</div>

</header>


<!-- SEARCH -->

<div class="search-box">

<input
    id="searchInput"
    type="text"
    placeholder="Αναζήτησε πόλη ή περιοχή οπουδήποτε στον κόσμο..."
>

<button id="searchButton">
Αναζήτηση
</button>

</div>


<div id="error" class="error"></div>


<div id="loading" class="loading">
Φόρτωση δεδομένων καιρού...
</div>


<div id="weatherContent" style="display:none;">


<!-- LOCATION -->

<div class="location">

<div class="location-title">

<span id="locationName">
--
</span>

<span
    id="locationFlag"
    class="flag">
</span>

</div>

<div
    id="countryName"
    class="country">
--
</div>

</div>


<!-- CURRENT -->

<div class="current">

<div class="current-left">

<div
    id="currentIcon"
    class="current-icon">
</div>

<div>

<div
    id="currentTemp"
    class="current-temp">
--°
</div>

<div
    id="currentCondition"
    class="current-condition">
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


<!-- DAILY -->

<div class="section-title">
15ήμερη πρόγνωση
</div>

<div
    id="forecastGrid"
    class="forecast-grid">
</div>


<!-- HOURLY -->

<div
    id="hourlyContainer"
    class="hourly-container">

<div
    id="hourlyTitle"
    class="hourly-title">
Ωριαία πρόγνωση
</div>

<div
    id="hourlyScroll"
    class="hourly-scroll">
</div>

</div>


</div>

</div>


<script>

/* =========================================================
   GLOBAL
========================================================= */

let currentLocation = null;
let currentWeather = null;


/* =========================================================
   DAY NAMES
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
   WEATHER DESCRIPTION
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

    if(!code || code.length !== 2)
        return "";

    return [...code.toUpperCase()]
        .map(
            c =>
            String.fromCodePoint(
                127397 + c.charCodeAt(0)
            )
        )
        .join("");
}


/* =========================================================
   WIND DIRECTION
========================================================= */

function windDirection(deg){

    if(
        deg === null ||
        deg === undefined ||
        Number.isNaN(Number(deg))
    ){
        return "--";
    }

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
        Math.round(Number(deg)/45) % 8
    ];
}


/* =========================================================
   SVG WEATHER
========================================================= */

function weatherSVG(code,isDay){

    const sun = `

        <circle
            cx="32"
            cy="32"
            r="11"
            fill="#ffd34f"/>

        <g
            stroke="#ffd34f"
            stroke-width="3"
            stroke-linecap="round">

            <path d="M32 5v9"/>
            <path d="M32 50v9"/>
            <path d="M5 32h9"/>
            <path d="M50 32h9"/>

            <path d="M13 13l7 7"/>
            <path d="M44 44l7 7"/>

            <path d="M51 13l-7 7"/>
            <path d="M20 44l-7 7"/>

        </g>
    `;


    const moon = `

        <circle
            cx="30"
            cy="30"
            r="18"
            fill="#e4efff"/>

        <circle
            cx="38"
            cy="23"
            r="18"
            fill="#0a2442"/>

    `;


    const cloud = `

        <path
            d="
            M17 45
            C10 45 8 40 10 35
            C11 29 16 26 22 28
            C24 20 31 16 38 18
            C45 20 48 25 48 31
            C53 31 57 35 56 40
            C55 44 51 45 46 45
            Z"

            fill="#d8e4ef"
        />
    `;


    const darkCloud = `

        <path
            d="
            M17 45
            C10 45 8 40 10 35
            C11 29 16 26 22 28
            C24 20 31 16 38 18
            C45 20 48 25 48 31
            C53 31 57 35 56 40
            C55 44 51 45 46 45
            Z"

            fill="#a9b8c8"
        />
    `;


    const rain = `

        <g
            stroke="#5dbaff"
            stroke-width="4"
            stroke-linecap="round">

            <path d="M20 49l-4 9"/>
            <path d="M32 49l-4 9"/>
            <path d="M44 49l-4 9"/>

        </g>
    `;


    /* ΡΕΑΛΙΣΤΙΚΟΤΕΡΕΣ ΝΙΦΑΔΕΣ */

    const snow = `

        <g
            stroke="#f5fcff"
            stroke-width="2.6"
            stroke-linecap="round"
            fill="none">

            <path d="M19 49v10"/>
            <path d="M14 54h10"/>
            <path d="M15.5 50.5l7 7"/>
            <path d="M22.5 50.5l-7 7"/>

            <path d="M32 49v10"/>
            <path d="M27 54h10"/>
            <path d="M28.5 50.5l7 7"/>
            <path d="M35.5 50.5l-7 7"/>

            <path d="M45 49v10"/>
            <path d="M40 54h10"/>
            <path d="M41.5 50.5l7 7"/>
            <path d="M48.5 50.5l-7 7"/>

        </g>
    `;


    const lightning = `

        <path
            d="M35 39
               L26 53
               H34
               L30 62
               L43 46
               H35
               Z"
            fill="#ffe55b"
        />

    `;


    /* ΚΑΘΑΡΟΣ */

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

            <path
                d="
                M19 48
                C12 48 9 44 10 39
                C11 34 16 32 21 33
                C23 27 29 24 35 26
                C41 27 44 32 44 37
                C49 37 53 40 52 44
                C51 47 48 48 44 48
                Z"

                fill="#cbd9e6"
            />

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

            <g
                stroke="#c6d5e2"
                stroke-width="4"
                stroke-linecap="round">

                <path d="M9 25h46"/>
                <path d="M6 34h52"/>
                <path d="M11 43h43"/>

            </g>

        </svg>`;
    }


    /* ΒΡΟΧΗ */

    if(
        [
            51,53,55,
            56,57,
            61,63,65,
            66,67,
            80,81,82
        ].includes(code)
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
        [
            71,73,75,
            77,85,86
        ].includes(code)
    ){

        return `
        <svg viewBox="0 0 64 64">

            ${isDay ? sun : moon}

            ${darkCloud}

            ${snow}

        </svg>`;
    }


    /* ΚΑΤΑΙΓΙΔΑ */

    if(
        [95,96,99].includes(code)
    ){

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
   ΥΕΤΟΣ
   30% ΚΑΙ ΠΑΝΩ ΜΟΝΟ
========================================================= */

function precipitationIcon(
    code,
    probability
){

    const p = Number(probability);

    /* 0–29% = ΤΙΠΟΤΑ */

    if(!Number.isFinite(p) || p < 30){
        return "";
    }


    /* ΧΙΟΝΙ */

    if(
        [
            71,73,75,
            77,85,86
        ].includes(code)
    ){

        return `

        <svg
            class="precip-icon snow-icon"
            viewBox="0 0 64 64">

            <g
                fill="none"
                stroke="currentColor"
                stroke-width="3"
                stroke-linecap="round">

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

        </svg>`;
    }


    /* ΒΡΟΧΗ */

    if(
        [
            51,53,55,
            56,57,
            61,63,65,
            66,67,
            80,81,82
        ].includes(code)
    ){

        return `

        <svg
            class="precip-icon rain-icon"
            viewBox="0 0 64 64">

            <path
                d="
                M18 35
                C10 35 7 30 9 24
                C11 18 17 16 22 18
                C25 11 32 8 39 11
                C46 13 49 19 48 25
                C54 25 57 29 56 34
                C55 39 51 41 46 41
                H18Z"
                fill="currentColor"
            />

            <path
                d="M20 46l-4 9"
                stroke="currentColor"
                stroke-width="4"
                stroke-linecap="round"
            />

            <path
                d="M32 46l-4 9"
                stroke="currentColor"
                stroke-width="4"
                stroke-linecap="round"
            />

            <path
                d="M44 46l-4 9"
                stroke="currentColor"
                stroke-width="4"
                stroke-linecap="round"
            />

        </svg>`;
    }


    /* ΚΑΤΑΙΓΙΔΑ */

    if(
        [95,96,99].includes(code)
    ){

        return `

        <svg
            class="precip-icon storm-icon"
            viewBox="0 0 64 64">

            <path
                d="
                M18 34
                C10 34 8 29 10 23
                C12 18 17 16 22 18
                C25 11 33 9 39 12
                C46 14 49 19 48 25
                C53 25 56 29 55 34
                C54 39 50 41 45 41
                H18Z"
                fill="currentColor"
            />

            <path
                d="
                M35 39
                L26 53
                H34
                L30 62
                L43 46
                H35Z"
                fill="#ffe35a"
            />

        </svg>`;
    }


    return "";
}


/* =========================================================
   FETCH MODEL
========================================================= */

async function fetchModel(
    latitude,
    longitude,
    model
){

    let endpoint;

    if(model === "ecmwf"){
        endpoint =
            "https://api.open-meteo.com/v1/ecmwf";
    }

    else if(model === "gfs"){
        endpoint =
            "https://api.open-meteo.com/v1/gfs";
    }

    else{
        throw new Error("Unknown model");
    }


    const params = new URLSearchParams({

        latitude:latitude,
        longitude:longitude,

        timezone:"auto",

        forecast_days:
            model === "ecmwf"
            ? "15"
            : "16",

        hourly:[
            "temperature_2m",
            "relative_humidity_2m",
            "apparent_temperature",
            "precipitation_probability",
            "precipitation",
            "weather_code",
            "wind_speed_10m",
            "wind_direction_10m"
        ].join(","),

        daily:[
            "sunrise",
            "sunset"
        ].join(",")

    });


    const response =
        await fetch(
            `${endpoint}?${params.toString()}`
        );


    if(!response.ok){

        const txt =
            await response.text();

        console.error(
            model,
            response.status,
            txt
        );

        throw new Error(
            model + " API error"
        );
    }


    const data =
        await response.json();


    if(
        !data.hourly ||
        !data.hourly.time
    ){
        throw new Error(
            model + " returned no hourly data"
        );
    }


    return data;
}


/* =========================================================
   AVERAGE
========================================================= */

function avg(a,b){

    const aa = Number(a);
    const bb = Number(b);

    if(
        Number.isFinite(aa) &&
        Number.isFinite(bb)
    ){
        return (aa+bb)/2;
    }

    if(Number.isFinite(aa))
        return aa;

    if(Number.isFinite(bb))
        return bb;

    return null;
}


/* =========================================================
   DAILY DATA FROM HOURLY
========================================================= */

function makeDaily(
    ecmwf,
    gfs
){

    const result = [];


    for(let d=0;d<15;d++){

        const eDate =
            ecmwf.hourly.time[
                d*24
            ]?.slice(0,10);


        const gDate =
            gfs.hourly.time[
                d*24
            ]?.slice(0,10);


        const date =
            eDate || gDate;


        if(!date)
            continue;


        const eHours =
            ecmwf.hourly.time
                .map((t,i)=>({
                    t,
                    i
                }))
                .filter(
                    x=>x.t.startsWith(date)
                );


        const gHours =
            gfs.hourly.time
                .map((t,i)=>({
                    t,
                    i
                }))
                .filter(
                    x=>x.t.startsWith(date)
                );


        const eTemps =
            eHours.map(
                x =>
                Number(
                    ecmwf.hourly.temperature_2m[x.i]
                )
            ).filter(Number.isFinite);


        const gTemps =
            gHours.map(
                x =>
                Number(
                    gfs.hourly.temperature_2m[x.i]
                )
            ).filter(Number.isFinite);


        const eProb =
            eHours.map(
                x =>
                Number(
                    ecmwf.hourly
                        .precipitation_probability[x.i]
                )
            ).filter(Number.isFinite);


        const gProb =
            gHours.map(
                x =>
                Number(
                    gfs.hourly
                        .precipitation_probability[x.i]
                )
            ).filter(Number.isFinite);


        const eWind =
            eHours.map(
                x =>
                Number(
                    ecmwf.hourly.wind_speed_10m[x.i]
                )
            ).filter(Number.isFinite);


        const gWind =
            gHours.map(
                x =>
                Number(
                    gfs.hourly.wind_speed_10m[x.i]
                )
            ).filter(Number.isFinite);


        const maxEProb =
            eProb.length
            ? Math.max(...eProb)
            : null;


        const maxGProb =
            gProb.length
            ? Math.max(...gProb)
            : null;


        const maxProbability =
            avg(
                maxEProb,
                maxGProb
            );


        const maxE =
            eTemps.length
            ? Math.max(...eTemps)
            : null;


        const maxG =
            gTemps.length
            ? Math.max(...gTemps)
            : null;


        const minE =
            eTemps.length
            ? Math.min(...eTemps)
            : null;


        const minG =
            gTemps.length
            ? Math.min(...gTemps)
            : null;


        const windE =
            eWind.length
            ? Math.max(...eWind)
            : null;


        const windG =
            gWind.length
            ? Math.max(...gWind)
            : null;


        /*
        Παίρνουμε τον κωδικό γύρω στις 12:00.
        */

        const noonE =
            eHours.find(
                x =>
                x.t.includes("T12:")
            );


        const noonG =
            gHours.find(
                x =>
                x.t.includes("T12:")
            );


        const code =
            noonE
            ? ecmwf.hourly.weather_code[noonE.i]
            : (
                noonG
                ? gfs.hourly.weather_code[noonG.i]
                : 0
            );


        /*
        Μέσος άνεμος.
        */

        const eWindValues =
            eHours.map(
                x =>
                Number(
                    ecmwf.hourly.wind_speed_10m[x.i]
                )
            ).filter(Number.isFinite);


        const gWindValues =
            gHours.map(
                x =>
                Number(
                    gfs.hourly.wind_speed_10m[x.i]
                )
            ).filter(Number.isFinite);


        const eWindMean =
            eWindValues.length
            ? eWindValues.reduce(
                (a,b)=>a+b,
                0
            ) / eWindValues.length
            : null;


        const gWindMean =
            gWindValues.length
            ? gWindValues.reduce(
                (a,b)=>a+b,
                0
            ) / gWindValues.length
            : null;


        const windMean =
            avg(
                eWindMean,
                gWindMean
            );


        /*
        Κυρίαρχη διεύθυνση.
        */

        const noonWindE =
            noonE
            ? ecmwf.hourly.wind_direction_10m[
                noonE.i
            ]
            : null;


        const noonWindG =
            noonG
            ? gfs.hourly.wind_direction_10m[
                noonG.i
            ]
            : null;


        const windDirectionMean =
            avg(
                noonWindE,
                noonWindG
            );


        result.push({

            date,

            max:
                avg(maxE,maxG),

            min:
                avg(minE,minG),

            precipitationProbability:
                maxProbability,

            weatherCode:
                Number(code),

            wind:
                windMean,

            windDirection:
                windDirectionMean,

            sunrise:
                ecmwf.daily?.sunrise?.[d]
                ||
                gfs.daily?.sunrise?.[d]
                ||
                null,

            sunset:
                ecmwf.daily?.sunset?.[d]
                ||
                gfs.daily?.sunset?.[d]
                ||
                null
        });
    }


    return result;
}


/* =========================================================
   HOURLY MERGE
========================================================= */

function makeHourly(
    ecmwf,
    gfs
){

    const result = [];


    const eMap = new Map();

    ecmwf.hourly.time.forEach(
        (t,i)=>{
            eMap.set(t,i);
        }
    );


    const gMap = new Map();

    gfs.hourly.time.forEach(
        (t,i)=>{
            gMap.set(t,i);
        }
    );


    for(
        const time of ecmwf.hourly.time
    ){

        if(!gMap.has(time))
            continue;


        const ei =
            eMap.get(time);

        const gi =
            gMap.get(time);


        result.push({

            time,

            temperature:
                avg(
                    ecmwf.hourly
                        .temperature_2m[ei],
                    gfs.hourly
                        .temperature_2m[gi]
                ),

            humidity:
                avg(
                    ecmwf.hourly
                        .relative_humidity_2m[ei],
                    gfs.hourly
                        .relative_humidity_2m[gi]
                ),

            apparent:
                avg(
                    ecmwf.hourly
                        .apparent_temperature[ei],
                    gfs.hourly
                        .apparent_temperature[gi]
                ),

            precipitationProbability:
                avg(
                    ecmwf.hourly
                        .precipitation_probability[ei],
                    gfs.hourly
                        .precipitation_probability[gi]
                ),

            precipitation:
                avg(
                    ecmwf.hourly
                        .precipitation[ei],
                    gfs.hourly
                        .precipitation[gi]
                ),

            weatherCode:
                Number(
                    ecmwf.hourly
                        .weather_code[ei]
                ),

            wind:
                avg(
                    ecmwf.hourly
                        .wind_speed_10m[ei],
                    gfs.hourly
                        .wind_speed_10m[gi]
                ),

            windDirection:
                avg(
                    ecmwf.hourly
                        .wind_direction_10m[ei],
                    gfs.hourly
                        .wind_direction_10m[gi]
                )
        });
    }


    return result;
}


/* =========================================================
   CURRENT
========================================================= */

function getCurrent(
    hourly
){

    const now =
        new Date();


    const localHour =
        now.getHours();


    /*
    Ψάχνουμε την τρέχουσα ώρα.
    */

    let best =
        hourly.find(
            h =>
            new Date(h.time).getHours()
            === localHour
        );


    if(!best)
        best = hourly[0];


    return best;
}


/* =========================================================
   LOAD WEATHER
========================================================= */

async function loadWeather(){

    if(!currentLocation)
        return;


    showLoading();


    try{

        const lat =
            currentLocation.latitude;

        const lon =
            currentLocation.longitude;


        /*
        ΔΥΟ ΞΕΧΩΡΙΣΤΑ API:
        ECMWF
        GFS
        */

        const [ecmwf,gfs] =
            await Promise.all([

                fetchModel(
                    lat,
                    lon,
                    "ecmwf"
                ),

                fetchModel(
                    lat,
                    lon,
                    "gfs"
                )

            ]);


        const daily =
            makeDaily(
                ecmwf,
                gfs
            );


        const hourly =
            makeHourly(
                ecmwf,
                gfs
            );


        if(
            daily.length < 15 ||
            hourly.length === 0
        ){
            throw new Error(
                "Incomplete weather data"
            );
        }


        currentWeather = {

            daily,
            hourly

        };


        renderLocation();

        renderCurrent();

        renderDaily();

        renderHourly(0);


        document
            .getElementById("loading")
            .style.display="none";


        document
            .getElementById("weatherContent")
            .style.display="block";


        hideError();


    }catch(error){

        console.error(
            "WEATHER ERROR:",
            error
        );


        document
            .getElementById("loading")
            .style.display="none";


        document
            .getElementById("weatherContent")
            .style.display="none";


        showError(
            "Δεν ήταν δυνατή η φόρτωση δεδομένων καιρού. Δοκίμασε ξανά σε λίγο."
        );
    }
}


/* =========================================================
   LOCATION RENDER
========================================================= */

function renderLocation(){

    document
        .getElementById("locationName")
        .textContent =
        currentLocation.name || "--";


    document
        .getElementById("countryName")
        .textContent =
        currentLocation.country || "--";


    document
        .getElementById("locationFlag")
        .textContent =
        countryFlag(
            currentLocation.country_code
        );
}


/* =========================================================
   CURRENT RENDER
========================================================= */

function renderCurrent(){

    const c =
        getCurrent(
            currentWeather.hourly
        );


    if(!c)
        return;


    const hour =
        new Date(c.time).getHours();


    const isDay =
        hour >= 7 &&
        hour < 20;


    document
        .getElementById("currentTemp")
        .textContent =
        Math.round(c.temperature)
        + "°";


    document
        .getElementById("currentCondition")
        .textContent =
        weatherDescription(
            c.weatherCode
        );


    document
        .getElementById("feels")
        .textContent =
        Math.round(c.apparent)
        + "°";


    document
        .getElementById("humidity")
        .textContent =
        Math.round(c.humidity)
        + "%";


    document
        .getElementById("wind")
        .textContent =
        Math.round(c.wind)
        + " km/h";


    document
        .getElementById("windDir")
        .textContent =
        windDirection(
            c.windDirection
        );


    document
        .getElementById("currentIcon")
        .innerHTML =
        weatherSVG(
            c.weatherCode,
            isDay
        );


    const today =
        currentWeather.daily[0];


    document
        .getElementById("sunrise")
        .textContent =
        today.sunrise
        ? today.sunrise.slice(11,16)
        : "--";


    document
        .getElementById("sunset")
        .textContent =
        today.sunset
        ? today.sunset.slice(11,16)
        : "--";
}


/* =========================================================
   DAILY RENDER
========================================================= */

function renderDaily(){

    const grid =
        document
            .getElementById("forecastGrid");


    grid.innerHTML="";


    currentWeather.daily
        .slice(0,15)
        .forEach(
            (day,index)=>{


                const date =
                    new Date(
                        day.date
                        + "T12:00:00"
                    );


                const dayName =
                    dayNames[
                        date.getDay()
                    ];


                const dateText =
                    date.toLocaleDateString(
                        "el-GR",
                        {
                            day:"2-digit",
                            month:"2-digit"
                        }
                    );


                /*
                ΕΔΩ ΕΦΑΡΜΟΖΕΤΑΙ ΤΟ 30%.
                */

                const precip =
                    precipitationIcon(
                        day.weatherCode,
                        day.precipitationProbability
                    );


                const card =
                    document.createElement(
                        "div"
                    );


                card.className =
                    "forecast-card";


                card.innerHTML = `

                    <div class="day-name">
                        ${dayName}
                    </div>

                    <div class="date">
                        ${dateText}
                    </div>

                    <div class="weather-main-icon">

                        ${weatherSVG(
                            day.weatherCode,
                            true
                        )}

                    </div>

                    <div class="temp-max">
                        ${Math.round(day.max)}°
                    </div>

                    <div class="temp-min">
                        ${Math.round(day.min)}°
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
                            day.precipitationProbability
                        )}%
                    </div>

                    <div class="wind-info">
                        ${Math.round(day.wind)}
                        km/h
                        ·
                        ${windDirection(
                            day.windDirection
                        )}
                    </div>

                `;


                card.addEventListener(
                    "click",
                    ()=>{

                        document
                            .querySelectorAll(
                                ".forecast-card"
                            )
                            .forEach(
                                x =>
                                x.classList
                                 .remove("selected")
                            );


                        card.classList
                            .add("selected");


                        renderHourly(index);

                    }
                );


                grid.appendChild(card);

            }
        );


    const first =
        grid.querySelector(
            ".forecast-card"
        );


    if(first){

        first.classList
            .add("selected");

    }
}


/* =========================================================
   HOURLY RENDER
========================================================= */

function renderHourly(dayIndex){

    const day =
        currentWeather.daily[dayIndex];


    if(!day)
        return;


    const titleDate =
        new Date(
            day.date
            + "T12:00:00"
        );


    document
        .getElementById("hourlyTitle")
        .textContent =
        "Ωριαία πρόγνωση — "
        +
        dayNames[
            titleDate.getDay()
        ]
        +
        " "
        +
        titleDate.toLocaleDateString(
            "el-GR",
            {
                day:"2-digit",
                month:"2-digit"
            }
        );


    const scroll =
        document
            .getElementById("hourlyScroll");


    scroll.innerHTML="";


    const hours =
        currentWeather.hourly.filter(
            h =>
            h.time.startsWith(
                day.date
            )
        );


    hours.forEach(
        hour=>{

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
            ΚΑΙ ΣΤΗΝ ΩΡΙΑΙΑ:
            κάτω από 30% δεν υπάρχει
            εικονίδιο υετού.
            */

            const precip =
                precipitationIcon(
                    hour.weatherCode,
                    hour.precipitationProbability
                );


            const card =
                document.createElement(
                    "div"
                );


            card.className =
                "hour-card";


            card.innerHTML = `

                <div class="hour-time">
                    ${hourText}
                </div>

                <div class="hour-icon">

                    ${weatherSVG(
                        hour.weatherCode,
                        isDay
                    )}

                </div>

                <div class="hour-temp">
                    ${Math.round(
                        hour.temperature
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
                        hour.precipitationProbability
                    )}%
                </div>

                <div class="hour-wind">
                    ${Math.round(
                        hour.wind
                    )}
                    km/h
                    ·
                    ${windDirection(
                        hour.windDirection
                    )}
                </div>

            `;


            scroll.appendChild(card);

        }
    );
}


/* =========================================================
   SEARCH
========================================================= */

async function searchLocation(){

    const input =
        document
            .getElementById("searchInput");


    const query =
        input.value.trim();


    if(!query){

        showError(
            "Γράψε μια πόλη ή περιοχή."
        );

        return;
    }


    showLoading();


    try{

        const url =
            "https://geocoding-api.open-meteo.com/v1/search"
            +
            "?name="
            +
            encodeURIComponent(query)
            +
            "&count=10"
            +
            "&language=el"
            +
            "&format=json";


        const response =
            await fetch(url);


        if(!response.ok)
            throw new Error();


        const data =
            await response.json();


        if(
            !data.results ||
            data.results.length === 0
        ){

            throw new Error(
                "Location not found"
            );
        }


        let place =
            data.results.find(
                x =>
                x.name &&
                x.name.toLowerCase()
                ===
                query.toLowerCase()
            );


        if(!place)
            place = data.results[0];


        currentLocation = place;


        await loadWeather();


    }catch(error){

        console.error(error);

        document
            .getElementById("loading")
            .style.display="none";


        showError(
            "Δεν βρέθηκε η περιοχή. Δοκίμασε άλλη ονομασία."
        );
    }
}


/* =========================================================
   LOADING
========================================================= */

function showLoading(){

    hideError();


    document
        .getElementById("loading")
        .style.display="block";


    document
        .getElementById("weatherContent")
        .style.display="none";
}


/* =========================================================
   ERROR
========================================================= */

function showError(message){

    const el =
        document
            .getElementById("error");


    el.textContent =
        message;


    el.style.display =
        "block";
}


function hideError(){

    document
        .getElementById("error")
        .style.display=
        "none";
}


/* =========================================================
   SEARCH BUTTON
========================================================= */

document
    .getElementById("searchButton")
    .addEventListener(
        "click",
        searchLocation
    );


document
    .getElementById("searchInput")
    .addEventListener(
        "keydown",
        event=>{

            if(event.key === "Enter"){
                searchLocation();
            }

        }
    );


/* =========================================================
   DEFAULT LOCATION
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
   AUTO REFRESH
   ΚΑΘΕ 1 ΩΡΑ
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
