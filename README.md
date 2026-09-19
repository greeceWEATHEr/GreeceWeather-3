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
    color:#fff;
    background:
        linear-gradient(
            180deg,
            #071d35 0%,
            #0a2848 45%,
            #0d3762 100%
        );
    min-height:100vh;
}

.container{
    width:min(1400px,96%);
    margin:auto;
    padding:18px 0 30px;
}

header{
    text-align:center;
    margin-bottom:18px;
}

header h1{
    margin:0;
    font-size:32px;
}

header p{
    margin:7px 0 0;
    color:#cbdcf0;
    font-size:14px;
}

.search-box{
    display:flex;
    gap:10px;
    max-width:700px;
    margin:20px auto;
}

.search-box input{
    flex:1;
    min-width:0;
    padding:14px 16px;
    border:1px solid rgba(255,255,255,.16);
    border-radius:14px;
    background:rgba(255,255,255,.09);
    color:#fff;
    outline:none;
    font-size:15px;
}

.search-box input::placeholder{
    color:#b9c9da;
}

.search-box button{
    padding:0 20px;
    border:0;
    border-radius:14px;
    background:#1976d2;
    color:#fff;
    font-weight:bold;
    cursor:pointer;
}

.search-box button:hover{
    background:#2185e5;
}

.location{
    text-align:center;
    margin:10px 0 16px;
}

.location h2{
    margin:0;
    font-size:25px;
}

.location p{
    margin:6px 0 0;
    color:#cbdcf0;
    font-size:14px;
}

.model-info{
    margin:15px auto 20px;
    padding:13px 16px;
    max-width:900px;
    border-radius:16px;
    background:rgba(255,255,255,.075);
    border:1px solid rgba(255,255,255,.11);
    text-align:center;
    box-shadow:0 8px 25px rgba(0,0,0,.12);
}

.model-info-main{
    font-size:13px;
    font-weight:bold;
}

.model-info-sub{
    margin-top:5px;
    color:#bcd0e5;
    font-size:11px;
}

.model-info-status{
    margin-top:7px;
    color:#9fd0ff;
    font-size:11px;
}

.section-title{
    margin:22px 0 12px;
    font-size:20px;
    font-weight:bold;
}

.days{
    display:grid;
    grid-template-columns:repeat(6,minmax(0,1fr));
    gap:12px;
}

.day{
    min-width:0;
    padding:14px 10px;
    border-radius:18px;
    background:rgba(255,255,255,.075);
    border:1px solid rgba(255,255,255,.10);
    box-shadow:0 7px 20px rgba(0,0,0,.12);
    cursor:pointer;
    transition:.2s ease;
    text-align:center;
}

.day:hover{
    transform:translateY(-2px);
    background:rgba(255,255,255,.11);
}

.day.selected{
    border-color:rgba(96,177,255,.85);
    background:rgba(35,116,184,.22);
    box-shadow:0 0 0 1px rgba(96,177,255,.18),
               0 8px 25px rgba(0,0,0,.18);
}

.day-name{
    font-weight:bold;
    font-size:14px;
    margin-bottom:4px;
}

.day-date{
    color:#b8cce0;
    font-size:11px;
}

.weather-icon{
    width:72px;
    height:72px;
    margin:8px auto;
    display:flex;
    justify-content:center;
    align-items:center;
}

.weather-icon svg{
    width:100%;
    height:100%;
    display:block;
}

.temps{
    margin-top:2px;
    line-height:1.25;
}

.max-temp{
    font-size:21px;
    font-weight:bold;
}

.min-temp{
    font-size:14px;
    color:#aec4da;
    margin-top:2px;
}

.precip{
    margin-top:8px;
    min-height:31px;
    font-size:11px;
    color:#c8def1;
    line-height:1.35;
}

.hourly-wrapper{
    margin-top:24px;
    padding:16px;
    border-radius:20px;
    background:rgba(255,255,255,.065);
    border:1px solid rgba(255,255,255,.10);
    box-shadow:0 8px 28px rgba(0,0,0,.14);
}

.hourly-head{
    display:flex;
    align-items:center;
    justify-content:space-between;
    gap:12px;
    margin-bottom:4px;
}

.hourly-title-wrap{
    min-width:0;
}

.hourly-title{
    font-size:20px;
    font-weight:bold;
}

.selected-day-title{
    margin-top:5px;
    color:#bcd1e5;
    font-size:13px;
}

.hourly-close{
    flex:0 0 auto;
    width:37px;
    height:37px;
    border-radius:50%;
    border:1px solid rgba(255,255,255,.16);
    background:rgba(255,255,255,.08);
    color:#fff;
    font-size:25px;
    line-height:1;
    cursor:pointer;
    display:flex;
    align-items:center;
    justify-content:center;
}

.hourly-close:hover{
    background:rgba(255,255,255,.16);
}

.hourly{
    display:flex;
    flex-direction:column;
    gap:8px;
    margin-top:14px;
}

.hour{
    display:grid;
    grid-template-columns:72px 58px 1fr 100px 105px;
    align-items:center;
    gap:10px;
    padding:10px 12px;
    border-radius:14px;
    background:rgba(255,255,255,.065);
    border:1px solid rgba(255,255,255,.07);
}

.hour-time{
    font-weight:bold;
    font-size:13px;
}

.hour-icon{
    width:44px;
    height:44px;
}

.hour-icon svg{
    width:100%;
    height:100%;
}

.hour-temp{
    font-size:17px;
    font-weight:bold;
}

.hour-details{
    font-size:11px;
    color:#bfd3e6;
    line-height:1.5;
}

.hour-wind{
    text-align:right;
    font-size:11px;
    color:#c7d9ea;
    line-height:1.5;
}

.hourly-info{
    margin-top:14px;
    padding:14px 16px;
    border-radius:16px;
    background:
        linear-gradient(
            135deg,
            rgba(35,112,178,.22),
            rgba(255,255,255,.055)
        );
    border:1px solid rgba(105,185,255,.16);
    box-shadow:0 6px 20px rgba(0,0,0,.10);
    font-size:12px;
    line-height:1.6;
}

.hourly-info-row{
    display:flex;
    gap:9px;
    align-items:flex-start;
}

.hourly-info-row + .hourly-info-row{
    margin-top:4px;
}

.hourly-info strong{
    color:#e6f3ff;
}

.hourly-info-note{
    margin-top:8px;
    padding-top:7px;
    border-top:1px solid rgba(255,255,255,.08);
    color:#9fb5c9;
    font-size:11px;
}

.loading,
.error{
    text-align:center;
    padding:30px 10px;
}

.error{
    color:#ffb5b5;
}

footer{
    text-align:center;
    color:#8fa8bf;
    font-size:11px;
    margin-top:28px;
}

/* SVG night appearance */
.night-moon{
    filter:grayscale(.35) brightness(.9);
}

@media(max-width:1000px){
    .days{
        grid-template-columns:repeat(3,minmax(0,1fr));
    }

    .hour{
        grid-template-columns:65px 52px 1fr 95px;
    }

    .hour-wind{
        display:none;
    }
}

@media(max-width:600px){
    .container{
        width:94%;
        padding-top:12px;
    }

    header h1{
        font-size:27px;
    }

    .search-box{
        flex-direction:column;
    }

    .search-box button{
        padding:13px;
    }

    .days{
        grid-template-columns:repeat(2,minmax(0,1fr));
    }

    .day{
        padding:12px 7px;
    }

    .hour{
        grid-template-columns:58px 48px 1fr;
    }

    .hour-details{
        display:none;
    }

    .hour-temp{
        text-align:right;
    }

    .hourly-wrapper{
        padding:12px;
    }
}
</style>
</head>

<body>

<div class="container">

<header>
    <h1>🇬🇷 Greece Weather</h1>
    <p>Πρόγνωση καιρού για όλη την Ελλάδα και αναζήτηση περιοχών παγκοσμίως</p>
</header>

<div class="search-box">
    <input
        id="cityInput"
        type="text"
        value="Θεσσαλονίκη"
        placeholder="Πληκτρολόγησε περιοχή..."
        autocomplete="off">
    <button id="searchBtn">🔎 Αναζήτηση</button>
</div>

<div id="location" class="location"></div>

<div class="model-info">
    <div class="model-info-main">
        📡 ECMWF IFS • NOAA GFS • DWD ICON
    </div>

    <div class="model-info-sub">
        Multi-model συνδυασμός των διαθέσιμων δεδομένων
    </div>

    <div id="modelStatus" class="model-info-status">
        ⏳ Αναμονή δεδομένων...
    </div>
</div>

<div id="forecast">
    <div class="loading">⏳ Φόρτωση πρόγνωσης...</div>
</div>

<div
    id="hourlySection"
    class="hourly-wrapper"
    style="display:none;"
>

    <div class="hourly-head">

        <div class="hourly-title-wrap">
            <div class="hourly-title">
                🕐 Ωριαία πρόγνωση
            </div>

            <div
                id="selectedDayTitle"
                class="selected-day-title">
            </div>
        </div>

        <button
            id="closeHourly"
            class="hourly-close"
            title="Κλείσιμο">
            ×
        </button>

    </div>

    <div id="hourly" class="hourly"></div>

    <div class="hourly-info">

        <div class="hourly-info-row">
            <span>📡</span>
            <div>
                <strong>Πηγή δεδομένων:</strong>
                ECMWF IFS • NOAA GFS • DWD ICON
            </div>
        </div>

        <div class="hourly-info-row">
            <span>🧮</span>
            <div>
                <strong>Συνδυασμός:</strong>
                μέσος όρος των διαθέσιμων μοντέλων
            </div>
        </div>

        <div class="hourly-info-row">
            <span>🔄</span>
            <div>
                <strong>Έλεγχος νέων δεδομένων:</strong>
                κάθε 5 λεπτά — 00, 05, 10, 15, 20...
            </div>
        </div>

        <div class="hourly-info-note">
            ℹ️ Η εφαρμογή ελέγχει την πηγή κάθε 5 λεπτά.
            Τα ίδια τα μετεωρολογικά μοντέλα όμως ανανεώνονται
            στους δικούς τους κύκλους, επομένως σε ορισμένους
            ελέγχους μπορεί να χρησιμοποιούνται τα ίδια διαθέσιμα
            δεδομένα μέχρι να δημοσιευτεί νεότερο model run.
        </div>

    </div>

</div>

<footer>
    Weather data powered by Open-Meteo • ECMWF • NOAA • DWD
</footer>

</div>

<script>

let weatherData = null;
let locationData = null;
let lastCity = "";
let refreshTimer = null;


/* =========================
   SVG WEATHER ICONS
========================= */

function svgWrap(content){
    return `
    <svg
        viewBox="0 0 100 100"
        xmlns="http://www.w3.org/2000/svg"
        aria-hidden="true">
        ${content}
    </svg>`;
}


/* ---------- DAY ICONS ---------- */

function daySVG(state){

    if(state === "clear"){
        return svgWrap(`
            <circle
                cx="50"
                cy="50"
                r="22"
                fill="#ffd84d"/>

            <g
                stroke="#ffd84d"
                stroke-width="5"
                stroke-linecap="round">

                <line x1="50" y1="10" x2="50" y2="22"/>
                <line x1="50" y1="78" x2="50" y2="90"/>
                <line x1="10" y1="50" x2="22" y2="50"/>
                <line x1="78" y1="50" x2="90" y2="50"/>

                <line x1="22" y1="22" x2="31" y2="31"/>
                <line x1="69" y1="69" x2="78" y2="78"/>
                <line x1="78" y1="22" x2="69" y2="31"/>
                <line x1="31" y1="69" x2="22" y2="78"/>
            </g>
        `);
    }


    if(state === "mostlyClear" || state === "partlyCloudy"){
        return svgWrap(`
            <circle
                cx="38"
                cy="37"
                r="17"
                fill="#ffd84d"/>

            <g
                stroke="#ffd84d"
                stroke-width="4"
                stroke-linecap="round">

                <line x1="38" y1="12" x2="38" y2="20"/>
                <line x1="38" y1="54" x2="38" y2="61"/>
                <line x1="13" y1="37" x2="21" y2="37"/>
                <line x1="55" y1="37" x2="63" y2="37"/>
            </g>

            <path
                d="M28 69
                   C28 58 36 51 47 51
                   C55 51 62 55 65 62
                   C76 61 84 68 84 77
                   C84 86 77 91 67 91
                   H31
                   C22 91 17 86 17 79
                   C17 73 21 69 28 69Z"
                fill="#dce9f4"/>
        `);
    }


    if(state === "cloudy"){
        return svgWrap(`
            <path
                d="M22 70
                   C22 59 30 52 41 52
                   C45 42 54 37 64 37
                   C78 37 87 47 87 59
                   C94 61 98 67 98 75
                   C98 85 90 91 80 91
                   H29
                   C18 91 11 84 11 76
                   C11 73 14 70 22 70Z"
                fill="#b7c7d6"/>
        `);
    }


    if(state === "rain"){
        return svgWrap(`
            <path
                d="M20 59
                   C20 48 29 41 40 41
                   C44 31 53 27 63 27
                   C76 27 85 37 85 49
                   C93 51 97 57 97 65
                   C97 75 89 81 79 81
                   H28
                   C17 81 10 74 10 66
                   C10 63 14 60 20 59Z"
                fill="#9fb3c5"/>

            <g
                stroke="#54b9ff"
                stroke-width="5"
                stroke-linecap="round">

                <line x1="30" y1="84" x2="25" y2="94"/>
                <line x1="48" y1="84" x2="43" y2="94"/>
                <line x1="66" y1="84" x2="61" y2="94"/>
                <line x1="84" y1="84" x2="79" y2="94"/>
            </g>
        `);
    }


    if(state === "snow"){
        return svgWrap(`
            <path
                d="M20 59
                   C20 48 29 41 40 41
                   C44 31 53 27 63 27
                   C76 27 85 37 85 49
                   C93 51 97 57 97 65
                   C97 75 89 81 79 81
                   H28
                   C17 81 10 74 10 66
                   C10 63 14 60 20 59Z"
                fill="#b7c7d6"/>

            <g fill="#eaf7ff">
                <circle cx="29" cy="91" r="4"/>
                <circle cx="47" cy="91" r="4"/>
                <circle cx="65" cy="91" r="4"/>
                <circle cx="83" cy="91" r="4"/>
            </g>
        `);
    }


    if(state === "storm"){
        return svgWrap(`
            <path
                d="M18 57
                   C18 46 27 39 38 39
                   C42 29 51 25 61 25
                   C75 25 84 35 84 47
                   C92 49 97 55 97 63
                   C97 73 89 80 78 80
                   H26
                   C15 80 9 73 9 65
                   C9 62 13 58 18 57Z"
                fill="#8798a9"/>

            <path
                d="M54 55
                   L43 75
                   H54
                   L48 94
                   L72 68
                   H60
                   L68 55Z"
                fill="#ffd84d"/>
        `);
    }


    return daySVG("cloudy");
}


/* ---------- NIGHT ICONS ---------- */

function nightSVG(state){

    /*
       CLEAR NIGHT
       Μόνο φεγγάρι.
    */
    if(state === "clear"){
        return svgWrap(`
            <g class="night-moon">
                <path
                    d="M67 14
                       C48 17 35 34 35 53
                       C35 73 51 88 70 88
                       C78 88 85 85 91 81
                       C80 80 69 74 63 65
                       C55 53 56 38 63 27
                       C66 22 70 18 75 15
                       C72 14 69 14 67 14Z"
                    fill="#b9c8d8"/>
            </g>
        `);
    }


    /*
       NIGHT WITH A FEW CLOUDS
       Φεγγάρι + σύννεφο ως ΕΝΑ SVG.
    */
    if(state === "fewClouds"){
        return svgWrap(`
            <g class="night-moon">
                <path
                    d="M58 10
                       C43 13 32 27 32 43
                       C32 60 45 73 62 75
                       C69 76 76 73 81 69
                       C71 68 62 63 57 55
                       C51 45 52 33 58 24
                       C60 19 64 15 68 12
                       C64 10 61 10 58 10Z"
                    fill="#9fb3c7"/>
            </g>

            <path
                d="M25 70
                   C25 61 32 55 41 55
                   C44 47 51 43 59 43
                   C69 43 76 50 77 59
                   C85 60 91 65 91 73
                   C91 81 84 86 76 86
                   H31
                   C22 86 17 81 17 75
                   C17 73 20 71 25 70Z"
                fill="#aebdcb"/>
        `);
    }


    /*
       ΠΛΗΡΩΣ ΣΥΝΝΕΦΙΑΣΜΕΝΗ ΝΥΧΤΑ
       ΧΩΡΙΣ φεγγάρι.
    */
    if(state === "manyClouds" || state === "cloudy"){
        return svgWrap(`
            <path
                d="M20 62
                   C20 51 28 44 39 44
                   C43 34 52 29 62 29
                   C75 29 84 39 84 51
                   C92 53 97 59 97 67
                   C97 77 89 84 78 84
                   H27
                   C16 84 10 77 10 69
                   C10 66 14 63 20 62Z"
                fill="#8f9eae"/>
        `);
    }


    /*
       ΒΡΟΧΗ ΤΗ ΝΥΧΤΑ
       ΧΩΡΙΣ φεγγάρι.
    */
    if(state === "rain"){
        return svgWrap(`
            <path
                d="M18 57
                   C18 46 27 39 38 39
                   C42 29 51 25 61 25
                   C74 25 84 35 84 47
                   C92 49 97 55 97 63
                   C97 73 89 80 78 80
                   H26
                   C15 80 9 73 9 65
                   C9 62 13 58 18 57Z"
                fill="#8798a9"/>

            <g
                stroke="#55baff"
                stroke-width="5"
                stroke-linecap="round">

                <line x1="27" y1="82" x2="22" y2="94"/>
                <line x1="45" y1="82" x2="40" y2="94"/>
                <line x1="63" y1="82" x2="58" y2="94"/>
                <line x1="81" y1="82" x2="76" y2="94"/>
            </g>
        `);
    }


    /*
       ΧΙΟΝΙ ΤΗ ΝΥΧΤΑ
       Πλήρως συννεφιασμένο + χιόνι.
    */
    if(state === "snow"){
        return svgWrap(`
            <path
                d="M18 57
                   C18 46 27 39 38 39
                   C42 29 51 25 61 25
                   C74 25 84 35 84 47
                   C92 49 97 55 97 63
                   C97 73 89 80 78 80
                   H26
                   C15 80 9 73 9 65
                   C9 62 13 58 18 57Z"
                fill="#8f9eae"/>

            <g fill="#e9f5ff">
                <circle cx="27" cy="89" r="4"/>
                <circle cx="45" cy="89" r="4"/>
                <circle cx="63" cy="89" r="4"/>
                <circle cx="81" cy="89" r="4"/>
            </g>
        `);
    }


    /*
       ΚΑΤΑΙΓΙΔΑ ΝΥΧΤΑ
       Χωρίς φεγγάρι.
    */
    if(state === "storm"){
        return svgWrap(`
            <path
                d="M18 57
                   C18 46 27 39 38 39
                   C42 29 51 25 61 25
                   C74 25 84 35 84 47
                   C92 49 97 55 97 63
                   C97 73 89 80 78 80
                   H26
                   C15 80 9 73 9 65
                   C9 62 13 58 18 57Z"
                fill="#737f8c"/>

            <path
                d="M53 53
                   L42 73
                   H53
                   L47 94
                   L71 66
                   H59
                   L67 53Z"
                fill="#ffd84d"/>
        `);
    }


    return nightSVG("cloudy");
}


/* =========================
   WEATHER STATE
========================= */

function getSkyState(code, isDay, precipitationProbability){

    const codeNum = Number(code || 0);
    const prob = Number(precipitationProbability || 0);

    const precipOK = prob >= 30;

    if(precipOK){

        if(
            [95,96,99].includes(codeNum)
        ){
            return "storm";
        }

        if(
            [71,73,75,77,85,86].includes(codeNum)
        ){
            return "snow";
        }

        if(
            [51,53,55,56,57,61,63,65,66,67,80,81,82].includes(codeNum)
        ){
            return "rain";
        }
    }

    if(codeNum === 0){
        return "clear";
    }

    if([1].includes(codeNum)){
        return isDay ? "mostlyClear" : "fewClouds";
    }

    if([2].includes(codeNum)){
        return "partlyCloudy";
    }

    if([3,45,48].includes(codeNum)){
        return "cloudy";
    }

    return "cloudy";
}


function weatherSVG(code,isDay,precipitationProbability){

    const state = getSkyState(
        code,
        isDay,
        precipitationProbability
    );

    return isDay
        ? daySVG(state)
        : nightSVG(state);
}


/* =========================
   WIND DIRECTION
========================= */

function windDirection(deg){

    const d = Number(deg);

    if(!Number.isFinite(d)){
        return "—";
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
        Math.round(d / 45) % 8
    ];
}


/* =========================
   COUNTRY FLAG
========================= */

function countryFlag(countryCode){

    if(!countryCode){
        return "";
    }

    const code = String(countryCode).toUpperCase();

    if(code.length !== 2){
        return "";
    }

    return [...code]
        .map(
            c => String.fromCodePoint(
                127397 + c.charCodeAt(0)
            )
        )
        .join("");
}


/* =========================
   MODEL FETCH
========================= */

async function fetchModel(
    latitude,
    longitude,
    model
){

    const params = new URLSearchParams({

        latitude,
        longitude,

        hourly:[
            "temperature_2m",
            "apparent_temperature",
            "precipitation_probability",
            "precipitation",
            "snowfall",
            "weather_code",
            "cloud_cover",
            "wind_speed_10m",
            "wind_direction_10m",
            "wind_gusts_10m"
        ].join(","),

        daily:[
            "temperature_2m_max",
            "temperature_2m_min",
            "apparent_temperature_max",
            "apparent_temperature_min",
            "precipitation_sum",
            "snowfall_sum",
            "precipitation_probability_max",
            "weather_code",
            "sunrise",
            "sunset"
        ].join(","),

        timezone:"auto",
        forecast_days:"15",
        models:model

    });

    const url =
        "https://api.open-meteo.com/v1/forecast?"
        + params.toString();

    const response = await fetch(url);

    if(!response.ok){
        throw new Error(
            `Model ${model} error`
        );
    }

    return await response.json();
}


/* =========================
   ARRAY AVERAGE
========================= */

function average(values){

    const valid = values
        .map(Number)
        .filter(v => Number.isFinite(v));

    if(!valid.length){
        return 0;
    }

    return valid.reduce(
        (a,b)=>a+b,
        0
    ) / valid.length;
}


/* =========================
   COMBINE MODELS
========================= */

function combineModels(models){

    const hourlyLength =
        models[0].hourly.time.length;

    const dailyLength =
        models[0].daily.time.length;

    const combinedHourly = {
        time: models[0].hourly.time,
        temperature_2m:[],
        apparent_temperature:[],
        precipitation_probability:[],
        precipitation:[],
        snowfall:[],
        weather_code:[],
        cloud_cover:[],
        wind_speed_10m:[],
        wind_direction_10m:[],
        wind_gusts_10m:[]
    };

    for(let i=0;i<hourlyLength;i++){

        const temp = models.map(
            m => m.hourly.temperature_2m[i]
        );

        const apparent = models.map(
            m => m.hourly.apparent_temperature[i]
        );

        const precipProb = models.map(
            m => m.hourly.precipitation_probability[i]
        );

        const precip = models.map(
            m => m.hourly.precipitation[i]
        );

        const snowfall = models.map(
            m => m.hourly.snowfall[i]
        );

        const clouds = models.map(
            m => m.hourly.cloud_cover[i]
        );

        const wind = models.map(
            m => m.hourly.wind_speed_10m[i]
        );

        const gust = models.map(
            m => m.hourly.wind_gusts_10m[i]
        );

        const windDir = models.map(
            m => m.hourly.wind_direction_10m[i]
        );

        combinedHourly.temperature_2m.push(
            average(temp)
        );

        combinedHourly.apparent_temperature.push(
            average(apparent)
        );

        const avgProb = average(precipProb);

        combinedHourly.precipitation_probability.push(
            Math.round(avgProb)
        );

        combinedHourly.precipitation.push(
            average(precip)
        );

        combinedHourly.snowfall.push(
            average(snowfall)
        );

        combinedHourly.cloud_cover.push(
            average(clouds)
        );

        combinedHourly.wind_speed_10m.push(
            average(wind)
        );

        combinedHourly.wind_gusts_10m.push(
            average(gust)
        );

        combinedHourly.wind_direction_10m.push(
            average(windDir)
        );


        /*
           Επιλέγουμε το σοβαρότερο
           weather code από τα διαθέσιμα
           μοντέλα όταν ο υετός περνάει
           το όριο του 30%.
        */

        let selectedCode = 0;
        let severity = -1;

        models.forEach(m => {

            const c =
                Number(
                    m.hourly.weather_code[i] || 0
                );

            const p =
                Number(
                    m.hourly.precipitation_probability[i] || 0
                );

            let s = 0;

            if([95,96,99].includes(c)){
                s = 6;
            }
            else if(
                [71,73,75,77,85,86].includes(c)
            ){
                s = 5;
            }
            else if(
                [65,67,82].includes(c)
            ){
                s = 4;
            }
            else if(
                [61,63,66,80,81].includes(c)
            ){
                s = 3;
            }
            else if(
                [51,53,55,56,57].includes(c)
            ){
                s = 2;
            }
            else if(c === 3){
                s = 1;
            }
            else if(c === 2){
                s = 1;
            }
            else if(c === 1){
                s = 0;
            }

            if(
                p >= 30 &&
                s > severity
            ){
                severity = s;
                selectedCode = c;
            }
        });

        /*
           Αν κανένα μοντέλο δεν δίνει
           υετό >=30%, κρατάμε τον μέσο
           ουρανό/νεφοκάλυψη.
        */

        if(severity < 0){

            const avgCloud =
                average(clouds);

            if(avgCloud >= 85){
                selectedCode = 3;
            }
            else if(avgCloud >= 55){
                selectedCode = 2;
            }
            else if(avgCloud >= 20){
                selectedCode = 1;
            }
            else{
                selectedCode = 0;
            }
        }

        combinedHourly.weather_code.push(
            selectedCode
        );
    }


    const combinedDaily = {
        time: models[0].daily.time,
        temperature_2m_max:[],
        temperature_2m_min:[],
        apparent_temperature_max:[],
        apparent_temperature_min:[],
        precipitation_sum:[],
        snowfall_sum:[],
        precipitation_probability_max:[],
        weather_code:[],
        sunrise:models[0].daily.sunrise,
        sunset:models[0].daily.sunset
    };


    for(let i=0;i<dailyLength;i++){

        combinedDaily.temperature_2m_max.push(
            average(
                models.map(
                    m => m.daily.temperature_2m_max[i]
                )
            )
        );

        combinedDaily.temperature_2m_min.push(
            average(
                models.map(
                    m => m.daily.temperature_2m_min[i]
                )
            )
        );

        combinedDaily.apparent_temperature_max.push(
            average(
                models.map(
                    m => m.daily.apparent_temperature_max[i]
                )
            )
        );

        combinedDaily.apparent_temperature_min.push(
            average(
                models.map(
                    m => m.daily.apparent_temperature_min[i]
                )
            )
        );

        combinedDaily.precipitation_sum.push(
            average(
                models.map(
                    m => m.daily.precipitation_sum[i]
                )
            )
        );

        combinedDaily.snowfall_sum.push(
            average(
                models.map(
                    m => m.daily.snowfall_sum[i]
                )
            )
        );

        const dailyProb =
            average(
                models.map(
                    m => m.daily.precipitation_probability_max[i]
                )
            );

        combinedDaily.precipitation_probability_max.push(
            Math.round(dailyProb)
        );


        let selectedCode = 0;
        let severity = -1;

        models.forEach(m => {

            const c =
                Number(
                    m.daily.weather_code[i] || 0
                );

            const p =
                Number(
                    m.daily.precipitation_probability_max[i] || 0
                );

            let s = 0;

            if([95,96,99].includes(c)){
                s = 6;
            }
            else if(
                [71,73,75,77,85,86].includes(c)
            ){
                s = 5;
            }
            else if(
                [65,67,82].includes(c)
            ){
                s = 4;
            }
            else if(
                [61,63,66,80,81].includes(c)
            ){
                s = 3;
            }
            else if(
                [51,53,55,56,57].includes(c)
            ){
                s = 2;
            }
            else if(c === 3){
                s = 1;
            }
            else if(c === 2){
                s = 1;
            }

            if(
                p >= 30 &&
                s > severity
            ){
                severity = s;
                selectedCode = c;
            }
        });


        if(
            dailyProb >= 30 &&
            severity < 0
        ){
            selectedCode = 61;
        }

        if(
            dailyProb < 30
        ){

            const avgCloud =
                average(
                    models.map(
                        m => {

                            const day =
                                m.hourly.time.findIndex(
                                    t => t.startsWith(
                                        m.daily.time[i]
                                    )
                                );

                            if(day >= 0){
                                return m.hourly.cloud_cover[day];
                            }

                            return 50;
                        }
                    )
                );

            if(avgCloud >= 85){
                selectedCode = 3;
            }
            else if(avgCloud >= 55){
                selectedCode = 2;
            }
            else if(avgCloud >= 20){
                selectedCode = 1;
            }
            else{
                selectedCode = 0;
            }
        }

        combinedDaily.weather_code.push(
            selectedCode
        );
    }


    return {
        hourly:combinedHourly,
        daily:combinedDaily
    };
}


/* =========================
   FORMAT DATE
========================= */

function formatDate(dateString){

    const date =
        new Date(
            dateString + "T12:00:00"
        );

    return date.toLocaleDateString(
        "el-GR",
        {
            day:"2-digit",
            month:"2-digit"
        }
    );
}


function dayName(dateString){

    const date =
        new Date(
            dateString + "T12:00:00"
        );

    return date.toLocaleDateString(
        "el-GR",
        {
            weekday:"long"
        }
    );
}


/* =========================
   IS DAY
========================= */

function isHourDay(
    time,
    sunrise,
    sunset
){

    const t =
        new Date(time).getTime();

    const sr =
        new Date(sunrise).getTime();

    const ss =
        new Date(sunset).getTime();

    return t >= sr && t < ss;
}


/* =========================
   RENDER DAILY
========================= */

function renderDaily(){

    const daily =
        weatherData.daily;

    let html = `
        <div class="section-title">
            📅 Πρόγνωση 15 ημερών
        </div>

        <div class="days">
    `;


    daily.time.forEach(
        (date,i) => {

            const probability =
                Number(
                    daily.precipitation_probability_max[i] || 0
                );

            const code =
                daily.weather_code[i];

            const icon =
                weatherSVG(
                    code,
                    true,
                    probability
                );

            let precipText = "";

            if(probability >= 30){

                precipText = `
                    💧 ${Number(
                        daily.precipitation_sum[i] || 0
                    ).toFixed(1)} mm
                    <br>
                    ${probability}%
                `;

            }
            else{

                precipText = `
                    ${probability}%
                `;
            }


            html += `
                <div
                    class="day"
                    data-day-index="${i}">

                    <div class="day-name">
                        ${dayName(date)}
                    </div>

                    <div class="day-date">
                        ${formatDate(date)}
                    </div>

                    <div class="weather-icon">
                        ${icon}
                    </div>

                    <div class="temps">

                        <div class="max-temp">
                            ${Math.round(
                                daily.temperature_2m_max[i]
                            )}°C
                        </div>

                        <div class="min-temp">
                            ${Math.round(
                                daily.temperature_2m_min[i]
                            )}°C
                        </div>

                    </div>

                    <div class="precip">
                        ${precipText}
                    </div>

                </div>
            `;
        }
    );


    html += `</div>`;

    document.getElementById(
        "forecast"
    ).innerHTML = html;


    document
        .querySelectorAll(".day")
        .forEach(day => {

            day.addEventListener(
                "click",
                () => {

                    document
                        .querySelectorAll(".day")
                        .forEach(
                            d => d.classList.remove("selected")
                        );

                    day.classList.add("selected");

                    const index =
                        Number(
                            day.dataset.dayIndex
                        );

                    renderHourly(index);

                }
            );
        });
}


/* =========================
   RENDER HOURLY
========================= */

function renderHourly(dayIndex){

    const hourly =
        weatherData.hourly;

    const daily =
        weatherData.daily;

    const selectedDate =
        daily.time[dayIndex];


    document.getElementById(
        "hourlySection"
    ).style.display = "block";


    document.getElementById(
        "selectedDayTitle"
    ).textContent =
        `${dayName(selectedDate)} ${formatDate(selectedDate)}`;


    let html = "";

    hourly.time.forEach(
        (time,i) => {

            if(
                !time.startsWith(selectedDate)
            ){
                return;
            }


            const date =
                new Date(time);

            const hour =
                date.toLocaleTimeString(
                    "el-GR",
                    {
                        hour:"2-digit",
                        minute:"2-digit"
                    }
                );


            const probability =
                Number(
                    hourly.precipitation_probability[i] || 0
                );


            const code =
                hourly.weather_code[i];


            const sunrise =
                daily.sunrise[dayIndex];

            const sunset =
                daily.sunset[dayIndex];


            const isDay =
                isHourDay(
                    time,
                    sunrise,
                    sunset
                );


            const icon =
                weatherSVG(
                    code,
                    isDay,
                    probability
                );


            let precipText = "";

            if(probability >= 30){

                precipText =
                    `💧 ${Number(
                        hourly.precipitation[i] || 0
                    ).toFixed(1)} mm • ${probability}%`;

            }
            else{

                precipText =
                    `${probability}%`;
            }


            html += `
                <div class="hour">

                    <div class="hour-time">
                        ${hour}
                    </div>

                    <div class="hour-icon">
                        ${icon}
                    </div>

                    <div class="hour-temp">
                        ${Math.round(
                            hourly.temperature_2m[i]
                        )}°C
                    </div>

                    <div class="hour-details">
                        ${precipText}
                    </div>

                    <div class="hour-wind">
                        💨 ${Math.round(
                            hourly.wind_speed_10m[i]
                        )} km/h
                        <br>
                        ${windDirection(
                            hourly.wind_direction_10m[i]
                        )}
                    </div>

                </div>
            `;
        }
    );


    document.getElementById(
        "hourly"
    ).innerHTML =
        html ||
        `<div class="loading">
            Δεν υπάρχουν ωριαία δεδομένα.
        </div>`;


    document.getElementById(
        "hourlySection"
    ).scrollIntoView({
        behavior:"smooth",
        block:"start"
    });
}


/* =========================
   CLOSE HOURLY
========================= */

document
    .getElementById("closeHourly")
    .addEventListener(
        "click",
        () => {

            document.getElementById(
                "hourlySection"
            ).style.display = "none";

            document
                .querySelectorAll(".day")
                .forEach(
                    d => d.classList.remove("selected")
                );
        }
    );


/* =========================
   SEARCH LOCATION
========================= */

async function searchLocation(city){

    const url =
        "https://geocoding-api.open-meteo.com/v1/search?"
        + new URLSearchParams({

            name:city,
            count:"1",
            language:"el",
            format:"json"

        });


    const response =
        await fetch(url);


    if(!response.ok){
        throw new Error(
            "Αποτυχία αναζήτησης περιοχής."
        );
    }


    const data =
        await response.json();


    if(
        !data.results ||
        !data.results.length
    ){
        throw new Error(
            "Η περιοχή δεν βρέθηκε."
        );
    }


    return data.results[0];
}


/* =========================
   MAIN SEARCH
========================= */

async function performSearch(){

    const city =
        document
            .getElementById("cityInput")
            .value
            .trim();


    if(!city){
        return;
    }


    const forecast =
        document.getElementById("forecast");


    forecast.innerHTML = `
        <div class="loading">
            ⏳ Αναζήτηση και φόρτωση πρόγνωσης...
        </div>
    `;


    document.getElementById(
        "hourlySection"
    ).style.display = "none";


    try{

        const location =
            await searchLocation(city);


        locationData =
            location;

        lastCity =
            city;


        const country =
            location.country || "";

        const flag =
            countryFlag(
                location.country_code
            );


        document.getElementById(
            "location"
        ).innerHTML = `
            <h2>
                ${location.name}
            </h2>

            <p>
                ${flag ? flag + " " : ""}
                ${country}
            </p>
        `;


        const models = [];

        const modelNames = [
            {
                id:"ecmwf_ifs025",
                name:"ECMWF IFS"
            },
            {
                id:"gfs_seamless",
                name:"NOAA GFS"
            },
            {
                id:"icon_seamless",
                name:"DWD ICON"
            }
        ];


        for(
            const model of modelNames
        ){

            try{

                const data =
                    await fetchModel(
                        location.latitude,
                        location.longitude,
                        model.id
                    );

                models.push(data);

            }
            catch(error){

                console.warn(
                    model.name,
                    error
                );
            }
        }


        if(!models.length){
            throw new Error(
                "Δεν ήταν δυνατή η λήψη δεδομένων από τα διαθέσιμα μοντέλα."
            );
        }


        weatherData =
            combineModels(models);


        renderDaily();


        const activeNames =
            models.map(
                (_,i) =>
                    modelNames
                        .find(
                            m =>
                                m.id ===
                                [
                                    "ecmwf_ifs025",
                                    "gfs_seamless",
                                    "icon_seamless"
                                ][i]
                        )?.name
            ).filter(Boolean);


        document.getElementById(
            "modelStatus"
        ).textContent =
            `✅ Ενεργά μοντέλα: ${activeNames.join(" • ")}`
            + ` • Έλεγχος κάθε 5 λεπτά`;


    }
    catch(error){

        console.error(error);

        document.getElementById(
            "forecast"
        ).innerHTML = `
            <div class="error">
                ❌ ${error.message}
            </div>
        `;

        document.getElementById(
            "modelStatus"
        ).textContent =
            "⚠️ Δεν ήταν δυνατή η ενημέρωση των δεδομένων.";

    }
    finally{

        scheduleRefresh();

    }
}


/* =========================
   EXACT 5-MINUTE REFRESH
========================= */

function scheduleRefresh(){

    if(refreshTimer){
        clearTimeout(refreshTimer);
    }


    const now =
        new Date();


    const next =
        new Date(now);


    next.setSeconds(0,0);


    const minutes =
        now.getMinutes();


    const add =
        5 - (minutes % 5);


    next.setMinutes(
        minutes + add
    );


    let delay =
        next.getTime() -
        now.getTime();


    if(delay < 1000){
        delay = 1000;
    }


    refreshTimer =
        setTimeout(
            refreshWeather,
            delay
        );
}


async function refreshWeather(){

    if(!lastCity){
        scheduleRefresh();
        return;
    }


    await performSearch();
}


/* =========================
   EVENTS
========================= */

document
    .getElementById("searchBtn")
    .addEventListener(
        "click",
        performSearch
    );


document
    .getElementById("cityInput")
    .addEventListener(
        "keydown",
        event => {

            if(event.key === "Enter"){
                performSearch();
            }

        }
    );


/* =========================
   INITIAL LOAD
========================= */

performSearch();

</script>

</body>
</html>
