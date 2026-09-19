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
            #0b294b 45%,
            #0d3762 100%
        );

    min-height:100vh;
}

header{
    padding:22px 15px 16px;
    text-align:center;
    background:rgba(3,18,35,.72);
    border-bottom:1px solid rgba(255,255,255,.10);
}

header h1{
    margin:0;
    font-size:28px;
}

header p{
    margin:7px 0 0;
    opacity:.82;
    font-size:14px;
}

.container{
    width:min(1450px,94%);
    margin:20px auto 40px;
}

/* SEARCH */

.search-box{
    display:flex;
    gap:10px;
    margin-bottom:15px;
}

.search-box input{
    flex:1;
    min-width:0;
    padding:15px 16px;
    border:0;
    outline:none;
    border-radius:14px;
    font-size:16px;
    background:#fff;
    color:#14263a;
}

.search-box button{
    border:0;
    border-radius:14px;
    padding:0 23px;
    font-size:16px;
    font-weight:bold;
    cursor:pointer;
    background:#1689e8;
    color:#fff;
}

.search-box button:disabled{
    opacity:.6;
}

/* STATUS */

.status{
    min-height:24px;
    text-align:center;
    margin-bottom:12px;
    font-size:14px;
}

.error{
    color:#ffb5b5;
    font-weight:bold;
}

.loading{
    color:#9ed7ff;
}

/* LOCATION */

.location-card{
    background:rgba(255,255,255,.09);
    border:1px solid rgba(255,255,255,.10);
    border-radius:18px;
    padding:18px;
    margin-bottom:16px;
    text-align:center;
}

.location-name{
    font-size:29px;
    font-weight:bold;
}

.location-country{
    margin-top:7px;
    font-size:17px;
}

.country-flag{
    font-size:25px;
    vertical-align:-2px;
    margin-right:5px;
}

.location-admin{
    margin-top:4px;
    font-size:13px;
    opacity:.65;
}

/* CURRENT */

.current{
    display:grid;
    grid-template-columns:1.3fr 1fr;
    gap:15px;
    margin-bottom:20px;
}

.current-card{
    background:rgba(255,255,255,.09);
    border:1px solid rgba(255,255,255,.10);
    border-radius:20px;
    padding:22px;
}

.current-main{
    display:flex;
    align-items:center;
    gap:20px;
}

.current-icon{
    width:82px;
    height:82px;

    display:flex;
    align-items:center;
    justify-content:center;
}

.current-icon svg{
    width:78px;
    height:78px;
}

.current-temp{
    font-size:52px;
    font-weight:bold;
}

.current-description{
    font-size:17px;
    margin-top:4px;
    opacity:.9;
}

.current-time{
    margin-top:12px;
    opacity:.65;
    font-size:13px;
}

.details{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:10px;
}

.detail{
    background:rgba(0,0,0,.15);
    border-radius:13px;
    padding:12px;
}

.detail-label{
    font-size:12px;
    opacity:.65;
}

.detail-value{
    font-size:16px;
    font-weight:bold;
    margin-top:5px;
}

/* MODELS */

.model-info{
    background:rgba(255,255,255,.07);
    border:1px solid rgba(255,255,255,.08);
    padding:14px;
    border-radius:15px;
    margin-bottom:20px;
    text-align:center;
    font-size:13px;
    line-height:1.6;
}

.model-main{
    font-weight:bold;
    font-size:14px;
}

.model-sub{
    opacity:.65;
    margin-top:3px;
}

.model-status{
    margin-top:6px;
    font-size:12px;
    opacity:.7;
}

/* SECTION */

.section-title{
    font-size:22px;
    font-weight:bold;
    margin:22px 0 12px;
}

/* =====================================================
   15 ΗΜΕΡΕΣ
   ΥΠΟΧΡΕΩΤΙΚΑ 6 + 6 + 3
===================================================== */

.days{
    display:grid;

    grid-template-columns:
        repeat(6,minmax(0,1fr));

    gap:10px;
}

.day{
    min-width:0;

    background:rgba(255,255,255,.09);
    border:1px solid rgba(255,255,255,.09);
    border-radius:17px;

    padding:14px 10px;

    text-align:center;

    cursor:pointer;

    transition:
        transform .18s,
        background .18s,
        outline .18s;
}

.day:hover{
    transform:translateY(-2px);
    background:rgba(255,255,255,.14);
}

.day.selected{
    outline:2px solid #39a9ff;
    background:rgba(22,137,232,.20);
}

.day-name{
    font-weight:bold;
    font-size:14px;
}

.day-date{
    font-size:11px;
    opacity:.60;
    margin-top:3px;
}

.day-icon{
    height:55px;

    display:flex;
    align-items:center;
    justify-content:center;

    margin:7px 0;
}

.day-icon svg{
    width:50px;
    height:50px;
}

.day-desc{
    min-height:32px;
    font-size:12px;
    opacity:.85;
}

.temps{
    margin-top:8px;
    line-height:1.45;
}

.temp-max{
    font-size:21px;
    font-weight:bold;
}

.temp-min{
    font-size:15px;
    opacity:.65;
}

.precip{
    min-height:30px;
    margin-top:8px;
    font-size:12px;
}

.precip-line{
    font-weight:bold;
}

.precip-prob{
    margin-top:3px;
    opacity:.75;
}

/* HOURLY */

.hourly-wrapper{
    margin-top:20px;
}

.hourly{
    display:flex;
    flex-direction:column;
    gap:8px;
}

.hour{
    display:grid;

    grid-template-columns:
        70px
        55px
        1fr
        105px
        115px
        70px;

    align-items:center;
    gap:8px;

    background:rgba(255,255,255,.08);
    border-radius:13px;

    padding:10px 12px;
}

.hour-time{
    font-weight:bold;
}

.hour-icon{
    width:42px;
    height:42px;

    display:flex;
    align-items:center;
    justify-content:center;
}

.hour-icon svg{
    width:40px;
    height:40px;
}

.hour-temp{
    font-size:18px;
    font-weight:bold;
}

.hour-rain{
    font-size:13px;
}

.hour-wind{
    font-size:13px;
}

.hour-dir{
    font-size:13px;
    opacity:.8;
}

/* MOBILE */

@media(max-width:750px){

    .current{
        grid-template-columns:1fr;
    }

    /*
       Σε κινητό αλλάζει μόνο για να χωράει.
       Σε desktop παραμένει ΑΥΣΤΗΡΑ 6+6+3.
    */

    .days{
        grid-template-columns:
            repeat(3,minmax(0,1fr));
    }

    .hour{
        grid-template-columns:
            55px
            45px
            1fr
            85px;
    }

    .hour-wind,
    .hour-dir{
        display:none;
    }

}

@media(max-width:500px){

    header h1{
        font-size:23px;
    }

    .search-box{
        flex-direction:column;
    }

    .search-box button{
        height:48px;
    }

    .location-name{
        font-size:23px;
    }

    .current-main{
        gap:12px;
    }

    .current-temp{
        font-size:42px;
    }

    .days{
        grid-template-columns:
            repeat(2,minmax(0,1fr));
    }

    .hour{
        grid-template-columns:
            48px
            42px
            1fr
            75px;
    }

}

</style>

</head>


<body>

<header>

<h1>🇬🇷 Greece Weather</h1>

<p>
Πρόγνωση καιρού για όλη την Ελλάδα και αναζήτηση περιοχών παγκοσμίως
</p>

</header>


<div class="container">

<div class="search-box">

<input
    id="cityInput"
    type="text"
    value="Θεσσαλονίκη"
    placeholder="Γράψε πόλη ή περιοχή..."
    autocomplete="off"
>

<button id="searchBtn">
    🔎 Αναζήτηση
</button>

</div>


<div id="status" class="status"></div>

<div id="locationCard"></div>

<div id="current"></div>


<div class="model-info">

<div class="model-main">
📡 ECMWF IFS • NOAA GFS • DWD ICON
</div>

<div class="model-sub">
Multi-model συνδυασμός διαθέσιμων δεδομένων
</div>

<div class="model-sub">
Έλεγχος νέων δεδομένων κάθε 5 λεπτά
</div>

<div
    id="modelStatus"
    class="model-status"
>
Μοντέλα: —
</div>

<div
    id="lastUpdate"
    class="model-sub"
>
Τελευταίος έλεγχος: —
</div>

</div>


<div class="section-title">
📅 Πρόγνωση 15 ημερών
</div>

<div
    id="days"
    class="days"
></div>


<div
    id="hourlySection"
    class="hourly-wrapper"
    style="display:none;"
>

<div class="section-title">
🕐 Ωριαία πρόγνωση
</div>

<div
    id="selectedDayTitle"
    style="
        margin-bottom:10px;
        opacity:.8;
        font-size:14px;
    "
></div>

<div
    id="hourly"
    class="hourly"
></div>

</div>


<footer>
Weather data powered by Open-Meteo • ECMWF • NOAA • DWD
</footer>

</div>


<script>

/* =========================================================
   ELEMENTS
========================================================= */

const cityInput =
    document.getElementById("cityInput");

const searchBtn =
    document.getElementById("searchBtn");

const statusBox =
    document.getElementById("status");

const locationCard =
    document.getElementById("locationCard");

const currentBox =
    document.getElementById("current");

const daysBox =
    document.getElementById("days");

const hourlySection =
    document.getElementById("hourlySection");

const hourlyBox =
    document.getElementById("hourly");

const selectedDayTitle =
    document.getElementById("selectedDayTitle");

const lastUpdate =
    document.getElementById("lastUpdate");

const modelStatus =
    document.getElementById("modelStatus");


let locationData = null;
let modelData = [];
let combinedWeather = null;


/* =========================================================
   MODELS
========================================================= */

const MODELS = [

    {
        name:"ECMWF IFS",
        parameter:"ecmwf_ifs025",
        short:"ECMWF"
    },

    {
        name:"NOAA GFS",
        parameter:"gfs_seamless",
        short:"GFS"
    },

    {
        name:"DWD ICON",
        parameter:"icon_seamless",
        short:"ICON"
    }

];


/* =========================================================
   FLAG
========================================================= */

function countryFlag(code){

    if(!code)
        return "🏳️";

    code =
        String(code).toUpperCase();

    if(code.length !== 2)
        return "🏳️";

    return [...code]
        .map(
            c =>
                String.fromCodePoint(
                    127397 +
                    c.charCodeAt(0)
                )
        )
        .join("");
}


/* =========================================================
   ESCAPE
========================================================= */

function escapeHTML(value){

    return String(value)
        .replaceAll("&","&amp;")
        .replaceAll("<","&lt;")
        .replaceAll(">","&gt;")
        .replaceAll('"',"&quot;")
        .replaceAll("'","&#039;");
}


/* =========================================================
   WEATHER DESCRIPTION
========================================================= */

function weatherDescription(
    code,
    precipProbability=0,
    precipitation=0
){

    const c =
        Number(code);

    const p =
        Number(precipProbability || 0);

    const mm =
        Number(precipitation || 0);


    /*
       IMPORTANT:
       Under 30% precipitation is NOT
       described as rain/snow/storm.
    */

    if(p < 30 || mm <= 0){

        if(c === 0)
            return "Αίθριος";

        if(c === 1)
            return "Κυρίως αίθριος";

        if(c === 2)
            return "Μερική συννεφιά";

        if(c === 3)
            return "Συννεφιασμένος";

        if([45,48].includes(c))
            return "Ομίχλη";

        /*
           If the model says precipitation but
           probability is below 30%, use the
           non-precipitating sky state.
        */

        return cloudDescriptionFromCode(c);
    }


    if([51,53,55].includes(c))
        return "Ψιλόβροχο";

    if([56,57].includes(c))
        return "Παγωμένο ψιλόβροχο";

    if([61,63,65].includes(c))
        return "Βροχή";

    if([66,67].includes(c))
        return "Παγωμένη βροχή";

    if([71,73,75,77].includes(c))
        return "Χιονόπτωση";

    if([80,81,82].includes(c))
        return "Μπόρες";

    if([85,86].includes(c))
        return "Χιονομπόρες";

    if(c === 95)
        return "Καταιγίδα";

    if([96,99].includes(c))
        return "Καταιγίδα με χαλάζι";

    return cloudDescriptionFromCode(c);
}


function cloudDescriptionFromCode(code){

    const c =
        Number(code);

    if(c === 0)
        return "Αίθριος";

    if(c === 1)
        return "Κυρίως αίθριος";

    if(c === 2)
        return "Μερική συννεφιά";

    return "Συννεφιασμένος";
}


/* =========================================================
   SVG WEATHER ICON SYSTEM

   One visual icon only.

   This solves the moon + cloud requirement without
   putting two separate emoji together.
========================================================= */

function svgWrap(content){

    return `
    <svg
        viewBox="0 0 100 100"
        xmlns="http://www.w3.org/2000/svg"
        aria-hidden="true"
    >
        ${content}
    </svg>
    `;
}


/* DAY ICONS */

function daySVG(type){

    if(type === "clear"){

        return svgWrap(`
            <circle
                cx="50"
                cy="50"
                r="25"
                fill="#FFD84D"
            />
        `);

    }


    if(type === "mostlyClear"){

        return svgWrap(`
            <circle
                cx="57"
                cy="42"
                r="23"
                fill="#FFD84D"
            />

            <path
                d="M25 70
                   C20 58 29 48 41 49
                   C44 38 54 34 63 39
                   C72 39 79 46 79 56
                   C88 56 93 62 91 70
                   Z"
                fill="#dbe9f5"
            />
        `);

    }


    if(type === "partlyCloudy"){

        return svgWrap(`
            <circle
                cx="61"
                cy="39"
                r="22"
                fill="#FFD84D"
            />

            <path
                d="M22 74
                   C18 62 27 52 39 53
                   C42 42 53 37 63 42
                   C73 42 80 49 80 59
                   C89 59 94 65 92 74
                   Z"
                fill="#d9e6f2"
            />
        `);

    }


    if(type === "cloudy"){

        return svgWrap(`
            <path
                d="M19 73
                   C15 59 25 49 38 50
                   C42 39 53 34 64 40
                   C74 40 82 48 82 58
                   C91 58 96 65 93 73
                   Z"
                fill="#b9c8d6"
            />

            <path
                d="M28 75
                   C24 65 31 57 41 58
                   C45 50 54 47 62 51
                   C70 51 76 57 76 64
                   C84 64 88 69 86 75
                   Z"
                fill="#dce6ee"
            />
        `);

    }


    if(type === "rain"){

        return svgWrap(`
            <path
                d="M17 56
                   C15 44 24 35 36 36
                   C40 26 50 22 60 27
                   C70 27 78 34 78 44
                   C87 44 93 50 91 57
                   Z"
                fill="#aebdca"
            />

            <path
                d="M35 68 L29 82"
                stroke="#48a9e8"
                stroke-width="6"
                stroke-linecap="round"
            />

            <path
                d="M53 68 L47 82"
                stroke="#48a9e8"
                stroke-width="6"
                stroke-linecap="round"
            />

            <path
                d="M71 68 L65 82"
                stroke="#48a9e8"
                stroke-width="6"
                stroke-linecap="round"
            />
        `);

    }


    if(type === "snow"){

        return svgWrap(`
            <path
                d="M17 56
                   C15 44 24 35 36 36
                   C40 26 50 22 60 27
                   C70 27 78 34 78 44
                   C87 44 93 50 91 57
                   Z"
                fill="#b9c8d6"
            />

            <text
                x="30"
                y="82"
                font-size="18"
                fill="#dff4ff"
            >✦</text>

            <text
                x="47"
                y="87"
                font-size="18"
                fill="#dff4ff"
            >✦</text>

            <text
                x="64"
                y="82"
                font-size="18"
                fill="#dff4ff"
            >✦</text>
        `);

    }


    if(type === "storm"){

        return svgWrap(`
            <path
                d="M17 55
                   C15 43 24 34 36 35
                   C40 25 51 21 61 27
                   C71 27 79 34 79 44
                   C88 44 94 50 92 57
                   Z"
                fill="#8d9cab"
            />

            <path
                d="M53 57
                   L43 74
                   L52 73
                   L46 89
                   L65 67
                   L56 68
                   Z"
                fill="#FFD84D"
            />
        `);

    }


    return daySVG("clear");
}


/* =========================================================
   NIGHT ICONS
   ========================================================= */

function nightSVG(type){

    /*
       ONE unified visual icon.
       Not moon emoji + cloud emoji.
    */

    if(type === "clear"){

        return svgWrap(`
            <path
                d="M65 19
                   C49 22 39 35 41 49
                   C43 64 57 75 72 72
                   C79 71 84 68 89 63
                   C82 67 74 66 68 62
                   C57 55 53 42 58 31
                   C60 26 63 22 68 19
                   Z"
                fill="#c9dcf5"
            />
        `);

    }


    if(type === "fewClouds"){

        return svgWrap(`
            <path
                d="M62 16
                   C48 20 40 31 41 43
                   C42 51 47 58 54 61
                   C51 54 51 45 55 37
                   C58 29 63 23 69 20
                   Z"
                fill="#c9dcf5"
            />

            <path
                d="M22 73
                   C19 63 26 55 36 56
                   C39 48 48 45 56 49
                   C63 49 69 54 69 62
                   C77 62 82 67 80 73
                   Z"
                fill="#9eafc1"
            />
        `);

    }


    if(type === "manyClouds"){

        return svgWrap(`
            <path
                d="M66 17
                   C52 20 44 30 44 41
                   C44 49 48 55 55 59
                   C53 52 54 43 58 36
                   C61 28 66 22 72 19
                   Z"
                fill="#b8cce5"
            />

            <path
                d="M15 68
                   C12 55 22 46 34 47
                   C38 37 49 33 59 39
                   C68 39 76 46 76 56
                   C86 56 93 63 90 70
                   Z"
                fill="#8e9dad"
            />

            <path
                d="M28 76
                   C26 67 33 61 42 62
                   C45 55 53 52 61 56
                   C68 56 73 61 73 68
                   C80 68 84 72 82 76
                   Z"
                fill="#b9c5d0"
            />
        `);

    }


    if(type === "rain"){

        return svgWrap(`
            <path
                d="M65 16
                   C51 20 43 31 44 42
                   C44 50 49 56 55 59
                   C53 52 54 44 58 36
                   C61 28 66 22 72 19
                   Z"
                fill="#c9dcf5"
            />

            <path
                d="M17 59
                   C15 47 24 38 36 39
                   C40 29 50 25 60 30
                   C69 30 77 37 77 47
                   C86 47 92 53 90 60
                   Z"
                fill="#8f9eae"
            />

            <path
                d="M34 70 L29 83"
                stroke="#50ace8"
                stroke-width="6"
                stroke-linecap="round"
            />

            <path
                d="M52 70 L47 83"
                stroke="#50ace8"
                stroke-width="6"
                stroke-linecap="round"
            />

            <path
                d="M70 70 L65 83"
                stroke="#50ace8"
                stroke-width="6"
                stroke-linecap="round"
            />
        `);

    }


    if(type === "snow"){

        return svgWrap(`
            <path
                d="M65 16
                   C51 20 43 31 44 42
                   C44 50 49 56 55 59
                   C53 52 54 44 58 36
                   C61 28 66 22 72 19
                   Z"
                fill="#c9dcf5"
            />

            <path
                d="M17 59
                   C15 47 24 38 36 39
                   C40 29 50 25 60 30
                   C69 30 77 37 77 47
                   C86 47 92 53 90 60
                   Z"
                fill="#8f9eae"
            />

            <text
                x="30"
                y="81"
                font-size="17"
                fill="#e8f8ff"
            >✦</text>

            <text
                x="48"
                y="86"
                font-size="17"
                fill="#e8f8ff"
            >✦</text>

            <text
                x="65"
                y="81"
                font-size="17"
                fill="#e8f8ff"
            >✦</text>
        `);

    }


    if(type === "storm"){

        return svgWrap(`
            <path
                d="M65 16
                   C51 20 43 31 44 42
                   C44 50 49 56 55 59
                   C53 52 54 44 58 36
                   C61 28 66 22 72 19
                   Z"
                fill="#c9dcf5"
            />

            <path
                d="M16 58
                   C14 46 24 37 36 38
                   C40 28 50 24 60 29
                   C69 29 77 36 77 46
                   C86 46 92 52 90 59
                   Z"
                fill="#7f8e9d"
            />

            <path
                d="M53 59
                   L43 75
                   L52 74
                   L46 90
                   L65 67
                   L56 68
                   Z"
                fill="#FFD84D"
            />
        `);

    }


    return nightSVG("clear");
}


/* =========================================================
   SKY STATE
========================================================= */

function getSkyState(
    code,
    cloud,
    probability,
    precipitation,
    isDay,
    snowfall
){

    const c =
        Number(code || 0);

    const clouds =
        Number(cloud || 0);

    const prob =
        Number(probability || 0);

    const precip =
        Number(precipitation || 0);

    const snow =
        Number(snowfall || 0);


    /*
       STRICT precipitation threshold.
    */

    const hasPrecip =
        prob >= 30 &&
        (
            precip > 0 ||
            [51,53,55,
             56,57,
             61,63,65,
             66,67,
             71,73,75,77,
             80,81,82,
             85,86,
             95,96,99].includes(c)
        );


    /*
       Snow.
    */

    const hasSnow =
        hasPrecip &&
        (
            snow > 0 ||
            [71,73,75,77,85,86]
                .includes(c)
        );


    /*
       Storm.
    */

    const hasStorm =
        hasPrecip &&
        [95,96,99].includes(c);


    /*
       Rain.
    */

    const hasRain =
        hasPrecip &&
        !hasSnow &&
        !hasStorm &&
        [
            51,53,55,
            56,57,
            61,63,65,
            66,67,
            80,81,82
        ].includes(c);


    if(!isDay){

        if(hasStorm)
            return "storm";

        if(hasSnow)
            return "snow";

        if(hasRain)
            return "rain";

        /*
           Night cloud amount.
        */

        if(clouds < 25)
            return "clear";

        if(clouds < 65)
            return "fewClouds";

        return "manyClouds";
    }


    if(hasStorm)
        return "storm";

    if(hasSnow)
        return "snow";

    if(hasRain)
        return "rain";


    /*
       Day cloud classification.
    */

    if(clouds < 20)
        return "clear";

    if(clouds < 45)
        return "mostlyClear";

    if(clouds < 70)
        return "partlyCloudy";

    return "cloudy";
}


/* =========================================================
   ICON
========================================================= */

function weatherSVG(
    code,
    cloud,
    probability,
    precipitation,
    isDay,
    snowfall
){

    const state =
        getSkyState(
            code,
            cloud,
            probability,
            precipitation,
            isDay,
            snowfall
        );


    if(isDay)
        return daySVG(
            state === "fewClouds"
                ? "mostlyClear"
                : state
        );


    return nightSVG(
        state
    );
}


/* =========================================================
   AVERAGE
========================================================= */

function average(values){

    const valid =
        values.filter(
            x =>
                x !== null &&
                x !== undefined &&
                !isNaN(x)
        );

    if(!valid.length)
        return null;

    return valid.reduce(
        (sum,x) =>
            sum + Number(x),
        0
    ) / valid.length;
}


/* =========================================================
   DATE
========================================================= */

function formatDate(date){

    return new Date(
        date + "T12:00:00"
    ).toLocaleDateString(
        "el-GR",
        {
            day:"2-digit",
            month:"2-digit"
        }
    );
}


function dayName(date){

    return new Date(
        date + "T12:00:00"
    ).toLocaleDateString(
        "el-GR",
        {
            weekday:"short"
        }
    );
}


/* =========================================================
   LOCATION
========================================================= */

async function searchLocation(query){

    const url =
        "https://geocoding-api.open-meteo.com/v1/search" +
        "?name=" +
        encodeURIComponent(query) +
        "&count=10" +
        "&language=el" +
        "&format=json";


    const response =
        await fetch(url);


    if(!response.ok)
        throw new Error(
            "Σφάλμα αναζήτησης."
        );


    const data =
        await response.json();


    if(
        !data.results ||
        !data.results.length
    ){

        throw new Error(
            "Δεν βρέθηκε η περιοχή."
        );

    }


    const q =
        query
            .trim()
            .toLowerCase();


    return (
        data.results.find(
            x =>
                String(x.name)
                .toLowerCase() === q
        )
        ||
        data.results[0]
    );
}


/* =========================================================
   MODEL REQUEST
========================================================= */

async function getModelWeather(
    model,
    lat,
    lon
){

    const params =
        new URLSearchParams({

            latitude:lat,
            longitude:lon,

            timezone:"auto",

            forecast_days:"15",

            models:model.parameter,

            current:[
                "temperature_2m",
                "relative_humidity_2m",
                "apparent_temperature",
                "is_day",
                "precipitation",
                "weather_code",
                "cloud_cover",
                "wind_speed_10m",
                "wind_direction_10m",
                "wind_gusts_10m"
            ].join(","),

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
                "wind_gusts_10m",
                "is_day"
            ].join(","),

            daily:[
                "weather_code",
                "temperature_2m_max",
                "temperature_2m_min",
                "apparent_temperature_max",
                "apparent_temperature_min",
                "sunrise",
                "sunset",
                "precipitation_sum",
                "snowfall_sum",
                "precipitation_probability_max",
                "wind_speed_10m_max",
                "wind_gusts_10m_max",
                "wind_direction_10m_dominant"
            ].join(",")

        });


    const response =
        await fetch(
            "https://api.open-meteo.com/v1/forecast?" +
            params.toString()
        );


    if(!response.ok)
        throw new Error(
            model.name +
            " δεν απάντησε."
        );


    const data =
        await response.json();


    data.__model =
        model;


    return data;
}


/* =========================================================
   LOAD MODELS
========================================================= */

async function loadModels(){

    modelStatus.textContent =
        "Μοντέλα: λήψη ECMWF + GFS + ICON...";


    const results =
        await Promise.allSettled(

            MODELS.map(
                m =>
                    getModelWeather(
                        m,
                        locationData.latitude,
                        locationData.longitude
                    )
            )

        );


    modelData =
        results
            .filter(
                r =>
                    r.status === "fulfilled"
            )
            .map(
                r =>
                    r.value
            );


    if(!modelData.length)
        throw new Error(
            "Δεν υπάρχουν διαθέσιμα μοντέλα."
        );


    modelStatus.textContent =
        "Ενεργά μοντέλα: " +
        modelData
            .map(
                x =>
                    x.__model.short
            )
            .join(" + ");


    combineModels();
}


/* =========================================================
   COMBINE
========================================================= */

function combineModels(){

    const first =
        modelData[0];


    /* CURRENT */

    const currents =
        modelData.map(
            x =>
                x.current
        );


    const current = {

        temperature_2m:
            average(
                currents.map(
                    x => x.temperature_2m
                )
            ),

        relative_humidity_2m:
            average(
                currents.map(
                    x => x.relative_humidity_2m
                )
            ),

        apparent_temperature:
            average(
                currents.map(
                    x => x.apparent_temperature
                )
            ),

        precipitation:
            average(
                currents.map(
                    x => x.precipitation
                )
            ),

        cloud_cover:
            average(
                currents.map(
                    x => x.cloud_cover
                )
            ),

        wind_speed_10m:
            average(
                currents.map(
                    x => x.wind_speed_10m
                )
            ),

        wind_direction_10m:
            average(
                currents.map(
                    x => x.wind_direction_10m
                )
            ),

        wind_gusts_10m:
            average(
                currents.map(
                    x => x.wind_gusts_10m
                )
            ),

        is_day:
            currents[0].is_day

    };


    /* HOURLY */

    const hourly = {

        time:[],
        temperature_2m:[],
        apparent_temperature:[],
        precipitation_probability:[],
        precipitation:[],
        snowfall:[],
        weather_code:[],
        cloud_cover:[],
        wind_speed_10m:[],
        wind_direction_10m:[],
        wind_gusts_10m:[],
        is_day:[]

    };


    for(
        let i=0;
        i<first.hourly.time.length;
        i++
    ){

        const time =
            first.hourly.time[i];


        const rows = [];


        modelData.forEach(
            data => {

                const j =
                    data.hourly.time
                        .indexOf(time);


                if(j >= 0){

                    rows.push({

                        temp:
                            data.hourly.temperature_2m[j],

                        apparent:
                            data.hourly.apparent_temperature[j],

                        probability:
                            data.hourly.precipitation_probability[j],

                        precipitation:
                            data.hourly.precipitation[j],

                        snowfall:
                            data.hourly.snowfall[j],

                        code:
                            data.hourly.weather_code[j],

                        cloud:
                            data.hourly.cloud_cover[j],

                        wind:
                            data.hourly.wind_speed_10m[j],

                        direction:
                            data.hourly.wind_direction_10m[j],

                        gust:
                            data.hourly.wind_gusts_10m[j],

                        isDay:
                            data.hourly.is_day[j]

                    });

                }

            }
        );


        if(!rows.length)
            continue;


        hourly.time.push(time);


        hourly.temperature_2m.push(
            average(
                rows.map(
                    x => x.temp
                )
            )
        );


        hourly.apparent_temperature.push(
            average(
                rows.map(
                    x => x.apparent
                )
            )
        );


        hourly.precipitation_probability.push(
            average(
                rows.map(
                    x => x.probability
                )
            )
        );


        hourly.precipitation.push(
            average(
                rows.map(
                    x => x.precipitation
                )
            )
        );


        hourly.snowfall.push(
            average(
                rows.map(
                    x => x.snowfall
                )
            )
        );


        hourly.cloud_cover.push(
            average(
                rows.map(
                    x => x.cloud
                )
            )
        );


        hourly.wind_speed_10m.push(
            average(
                rows.map(
                    x => x.wind
                )
            )
        );


        hourly.wind_direction_10m.push(
            average(
                rows.map(
                    x => x.direction
                )
            )
        );


        hourly.wind_gusts_10m.push(
            average(
                rows.map(
                    x => x.gust
                )
            )
        );


        hourly.is_day.push(
            rows[0].isDay
        );


        /*
           Do NOT choose weather code from the
           highest probability model.

           Instead choose the most severe actual
           precipitation phenomenon ONLY when
           probability >=30.

           Otherwise cloud cover controls icon.
        */

        const probability =
            average(
                rows.map(
                    x => x.probability
                )
            );


        let chosenCode = 0;


        if(probability >= 30){

            const precipRows =
                rows.filter(
                    x =>
                        x.probability >= 30
                );


            if(precipRows.length){

                precipRows.sort(
                    (a,b) => {

                        const severity = code => {

                            if(
                                [95,96,99]
                                .includes(code)
                            )
                                return 6;

                            if(
                                [71,73,75,77,
                                 85,86]
                                .includes(code)
                            )
                                return 5;

                            if(
                                [61,63,65,
                                 66,67,
                                 80,81,82]
                                .includes(code)
                            )
                                return 4;

                            if(
                                [51,53,55,
                                 56,57]
                                .includes(code)
                            )
                                return 3;

                            return 0;

                        };


                        return severity(b.code)
                            -
                            severity(a.code);

                    }
                );


                chosenCode =
                    precipRows[0].code;

            }

        }
        else{

            /*
               No precipitation:
               code is derived from average cloud
               cover, avoiding false permanent clouds.
            */

            const cloud =
                average(
                    rows.map(
                        x => x.cloud
                    )
                );


            if(cloud < 20)
                chosenCode = 0;

            else if(cloud < 45)
                chosenCode = 1;

            else if(cloud < 70)
                chosenCode = 2;

            else
                chosenCode = 3;

        }


        hourly.weather_code.push(
            chosenCode
        );

    }


    /* DAILY */

    const daily = {

        time:first.daily.time,

        temperature_2m_max:[],
        temperature_2m_min:[],
        apparent_temperature_max:[],
        apparent_temperature_min:[],

        precipitation_sum:[],
        snowfall_sum:[],
        precipitation_probability_max:[],

        weather_code:[],
        cloud_cover:[],
        sunrise:[],
        sunset:[]

    };


    for(
        let d=0;
        d<first.daily.time.length;
        d++
    ){

        const date =
            first.daily.time[d];


        const rows = [];


        modelData.forEach(
            data => {

                const j =
                    data.daily.time
                        .indexOf(date);


                if(j >= 0){

                    rows.push({

                        max:
                            data.daily.temperature_2m_max[j],

                        min:
                            data.daily.temperature_2m_min[j],

                        apparentMax:
                            data.daily.apparent_temperature_max[j],

                        apparentMin:
                            data.daily.apparent_temperature_min[j],

                        precipitation:
                            data.daily.precipitation_sum[j],

                        snowfall:
                            data.daily.snowfall_sum[j],

                        probability:
                            data.daily.precipitation_probability_max[j],

                        code:
                            data.daily.weather_code[j],

                        sunrise:
                            data.daily.sunrise[j],

                        sunset:
                            data.daily.sunset[j]

                    });

                }

            }
        );


        daily.temperature_2m_max.push(
            average(
                rows.map(x => x.max)
            )
        );


        daily.temperature_2m_min.push(
            average(
                rows.map(x => x.min)
            )
        );


        daily.apparent_temperature_max.push(
            average(
                rows.map(x => x.apparentMax)
            )
        );


        daily.apparent_temperature_min.push(
            average(
                rows.map(x => x.apparentMin)
            )
        );


        const dailyPrecip =
            average(
                rows.map(
                    x => x.precipitation
                )
            );


        const dailySnow =
            average(
                rows.map(
                    x => x.snowfall
                )
            );


        const dailyProbability =
            average(
                rows.map(
                    x => x.probability
                )
            );


        daily.precipitation_sum.push(
            dailyPrecip
        );


        daily.snowfall_sum.push(
            dailySnow
        );


        daily.precipitation_probability_max.push(
            dailyProbability
        );


        /*
           Derive daily cloud cover from hourly
           combined data for that date.
        */

        const cloudValues = [];


        for(
            let h=0;
            h<hourly.time.length;
            h++
        ){

            if(
                hourly.time[h]
                    .startsWith(date)
            ){

                cloudValues.push(
                    hourly.cloud_cover[h]
                );

            }

        }


        const averageCloud =
            average(cloudValues) ?? 50;


        daily.cloud_cover.push(
            averageCloud
        );


        /*
           Determine daily weather condition
           from ACTUAL precipitation probability
           and precipitation type.
        */

        let dailyCode = 0;


        if(dailyProbability >= 30){

            const codes =
                rows.map(
                    x => x.code
                );


            if(
                codes.some(
                    x =>
                        [95,96,99]
                        .includes(x)
                )
            )
                dailyCode = 95;

            else if(
                dailySnow > 0 ||
                codes.some(
                    x =>
                        [71,73,75,77,
                         85,86]
                        .includes(x)
                )
            )
                dailyCode = 71;

            else
                dailyCode = 61;

        }
        else{

            if(averageCloud < 20)
                dailyCode = 0;

            else if(averageCloud < 45)
                dailyCode = 1;

            else if(averageCloud < 70)
                dailyCode = 2;

            else
                dailyCode = 3;

        }


        daily.weather_code.push(
            dailyCode
        );


        daily.sunrise.push(
            rows[0]
                ? rows[0].sunrise
                : null
        );


        daily.sunset.push(
            rows[0]
                ? rows[0].sunset
                : null
        );

    }


    combinedWeather = {

        current,
        hourly,
        daily

    };

}


/* =========================================================
   LOCATION DISPLAY
========================================================= */

function renderLocation(){

    const x =
        locationData;


    locationCard.innerHTML = `

        <div class="location-name">

            ${escapeHTML(x.name)}

        </div>


        <div class="location-country">

            <span class="country-flag">
                ${countryFlag(x.country_code)}
            </span>

            ${escapeHTML(
                x.country || "Άγνωστη χώρα"
            )}

        </div>


        ${
            x.admin1
            ?
            `
            <div class="location-admin">
                ${escapeHTML(x.admin1)}
            </div>
            `
            :
            ""
        }

    `;
}


/* =========================================================
   CURRENT
========================================================= */

function renderCurrent(){

    const c =
        combinedWeather.current;


    const h =
        combinedWeather.hourly;


    const now =
        new Date();


    let closest = 0;
    let smallest = Infinity;


    h.time.forEach(
        (time,index) => {

            const difference =
                Math.abs(
                    new Date(time) - now
                );


            if(difference < smallest){

                smallest = difference;
                closest = index;

            }

        }
    );


    const probability =
        Number(
            h.precipitation_probability[
                closest
            ] || 0
        );


    const precipitation =
        Number(
            h.precipitation[
                closest
            ] || 0
        );


    const snowfall =
        Number(
            h.snowfall[
                closest
            ] || 0
        );


    const cloud =
        Number(
            c.cloud_cover || 0
        );


    const code =
        h.weather_code[
            closest
        ];


    const isDay =
        Number(c.is_day) === 1;


    const icon =
        weatherSVG(
            code,
            cloud,
            probability,
            precipitation,
            isDay,
            snowfall
        );


    const description =
        weatherDescription(
            code,
            probability,
            precipitation
        );


    currentBox.innerHTML = `

        <div class="current">

            <div class="current-card">

                <div class="current-main">

                    <div class="current-icon">
                        ${icon}
                    </div>

                    <div>

                        <div class="current-temp">
                            ${Math.round(
                                c.temperature_2m
                            )}°C
                        </div>

                        <div class="current-description">
                            ${description}
                        </div>

                        <div class="current-time">
                            Αίσθηση
                            ${Math.round(
                                c.apparent_temperature
                            )}°C
                        </div>

                    </div>

                </div>

            </div>


            <div class="current-card">

                <div class="details">

                    <div class="detail">

                        <div class="detail-label">
                            💧 Υγρασία
                        </div>

                        <div class="detail-value">
                            ${Math.round(
                                c.relative_humidity_2m
                            )}%
                        </div>

                    </div>


                    <div class="detail">

                        <div class="detail-label">
                            💨 Άνεμος
                        </div>

                        <div class="detail-value">
                            ${Math.round(
                                c.wind_speed_10m
                            )} km/h
                        </div>

                    </div>


                    <div class="detail">

                        <div class="detail-label">
                            💨 Ριπές
                        </div>

                        <div class="detail-value">
                            ${Math.round(
                                c.wind_gusts_10m
                            )} km/h
                        </div>

                    </div>


                    <div class="detail">

                        <div class="detail-label">
                            Υετός
                        </div>

                        <div class="detail-value">
                            ${precipitation.toFixed(1)} mm
                            ${
                                probability >= 30
                                ? ` • ${Math.round(probability)}%`
                                : ""
                            }
                        </div>

                    </div>

                </div>

            </div>

        </div>

    `;
}


/* =========================================================
   15 DAYS
========================================================= */

function renderDays(){

    daysBox.innerHTML = "";


    const d =
        combinedWeather.daily;


    for(
        let i=0;
        i<15 &&
        i<d.time.length;
        i++
    ){

        const date =
            d.time[i];


        const probability =
            Number(
                d.precipitation_probability_max[i]
                || 0
            );


        const precipitation =
            Number(
                d.precipitation_sum[i]
                || 0
            );


        const snowfall =
            Number(
                d.snowfall_sum[i]
                || 0
            );


        const cloud =
            Number(
                d.cloud_cover[i]
                || 0
            );


        const code =
            d.weather_code[i];


        /*
           Daily icon is DAY icon because the
           card represents the whole daytime.
        */

        const icon =
            weatherSVG(
                code,
                cloud,
                probability,
                precipitation,
                true,
                snowfall
            );


        const card =
            document.createElement(
                "div"
            );


        card.className =
            "day";


        card.dataset.index =
            i;


        const day =
            i === 0
                ? "Σήμερα"
                : i === 1
                    ? "Αύριο"
                    : dayName(date);


        /*
           NO precipitation emoji below 30%.
        */

        const precipHTML =
            probability >= 30
            ?
            `
            <div class="precip">

                <div class="precip-line">
                    💧 ${precipitation.toFixed(1)} mm
                </div>

                <div class="precip-prob">
                    ${Math.round(probability)}%
                </div>

            </div>
            `
            :
            `
            <div class="precip">

                <div class="precip-prob">
                    ${Math.round(probability)}%
                </div>

            </div>
            `;


        card.innerHTML = `

            <div class="day-name">
                ${day}
            </div>

            <div class="day-date">
                ${formatDate(date)}
            </div>

            <div class="day-icon">
                ${icon}
            </div>

            <div class="day-desc">

                ${weatherDescription(
                    code,
                    probability,
                    precipitation
                )}

            </div>

            <div class="temps">

                <div class="temp-max">
                    ${Math.round(
                        d.temperature_2m_max[i]
                    )}°C
                </div>

                <div class="temp-min">
                    ${Math.round(
                        d.temperature_2m_min[i]
                    )}°C
                </div>

            </div>

            ${precipHTML}

        `;


        card.addEventListener(
            "click",
            () => {

                document
                    .querySelectorAll(".day")
                    .forEach(
                        x =>
                            x.classList.remove(
                                "selected"
                            )
                    );


                card.classList.add(
                    "selected"
                );


                renderHourly(i);

            }
        );


        daysBox.appendChild(card);

    }


    const first =
        daysBox.querySelector(
            ".day"
        );


    if(first){

        first.classList.add(
            "selected"
        );

        renderHourly(0);

    }

}


/* =========================================================
   HOURLY
========================================================= */

function renderHourly(dayIndex){

    const h =
        combinedWeather.hourly;


    const date =
        combinedWeather
            .daily
            .time[dayIndex];


    hourlyBox.innerHTML = "";


    selectedDayTitle.textContent =
        dayIndex === 0
            ? "Σήμερα"
            : dayIndex === 1
                ? "Αύριο"
                : dayName(date) +
                  " " +
                  formatDate(date);


    for(
        let i=0;
        i<h.time.length;
        i++
    ){

        if(
            !h.time[i].startsWith(date)
        )
            continue;


        const probability =
            Number(
                h.precipitation_probability[i]
                || 0
            );


        const precipitation =
            Number(
                h.precipitation[i]
                || 0
            );


        const snowfall =
            Number(
                h.snowfall[i]
                || 0
            );


        const code =
            h.weather_code[i];


        const cloud =
            Number(
                h.cloud_cover[i]
                || 0
            );


        const isDay =
            Number(
                h.is_day[i]
            ) === 1;


        const icon =
            weatherSVG(
                code,
                cloud,
                probability,
                precipitation,
                isDay,
                snowfall
            );


        const row =
            document.createElement(
                "div"
            );


        row.className =
            "hour";


        const precipHTML =
            probability >= 30
            ?
            `
            <div class="hour-rain">

                💧 ${precipitation.toFixed(1)} mm

                <br>

                <span style="opacity:.65;">
                    ${Math.round(probability)}%
                </span>

            </div>
            `
            :
            `
            <div class="hour-rain">

                ${Math.round(probability)}%

            </div>
            `;


        row.innerHTML = `

            <div class="hour-time">

                ${h.time[i]
                    .split("T")[1]
                    .substring(0,5)}

            </div>


            <div class="hour-icon">
                ${icon}
            </div>


            <div class="hour-temp">

                ${Math.round(
                    h.temperature_2m[i]
                )}°C

            </div>


            ${precipHTML}


            <div class="hour-wind">

                💨 ${Math.round(
                    h.wind_speed_10m[i]
                )} km/h

                <br>

                Ριπές ${Math.round(
                    h.wind_gusts_10m[i]
                )}

            </div>


            <div class="hour-dir">

                ${windDirection(
                    h.wind_direction_10m[i]
                )}

            </div>

        `;


        hourlyBox.appendChild(row);

    }


    hourlySection.style.display =
        "block";
}


/* =========================================================
   WIND
========================================================= */

function windDirection(degrees){

    if(
        degrees === null ||
        degrees === undefined ||
        isNaN(degrees)
    )
        return "—";


    const dirs = [
        "Β","ΒΑ","Α","ΝΑ",
        "Ν","ΝΔ","Δ","ΒΔ"
    ];


    return dirs[
        Math.round(
            Number(degrees)/45
        ) % 8
    ];
}


/* =========================================================
   REFRESH
========================================================= */

async function refreshWeather(){

    if(!locationData)
        return;


    try{

        modelStatus.textContent =
            "Μοντέλα: έλεγχος νέων δεδομένων...";


        await loadModels();


        renderCurrent();
        renderDays();


        lastUpdate.textContent =
            "Τελευταίος έλεγχος: " +
            new Date()
                .toLocaleTimeString(
                    "el-GR",
                    {
                        hour:"2-digit",
                        minute:"2-digit"
                    }
                );

    }
    catch(error){

        console.error(error);

        modelStatus.textContent =
            "Προσωρινό πρόβλημα ενημέρωσης.";

    }


    scheduleRefresh();
}


/* =========================================================
   EXACT 5 MINUTES
========================================================= */

function scheduleRefresh(){

    const now =
        new Date();


    const remainder =
        now.getMinutes() % 5;


    let minutes =
        5 - remainder;


    let delay =
        minutes * 60000 -
        now.getSeconds() * 1000 -
        now.getMilliseconds();


    if(delay < 1000)
        delay = 1000;


    setTimeout(
        refreshWeather,
        delay
    );
}


/* =========================================================
   SEARCH
========================================================= */

async function performSearch(){

    const query =
        cityInput.value.trim();


    if(!query){

        statusBox.innerHTML =
            `
            <span class="error">
                Γράψε μια περιοχή.
            </span>
            `;

        return;
    }


    searchBtn.disabled =
        true;


    statusBox.innerHTML =
        `
        <span class="loading">
            🔎 Αναζήτηση περιοχής...
        </span>
        `;


    try{

        locationData =
            await searchLocation(
                query
            );


        renderLocation();


        statusBox.innerHTML =
            `
            <span class="loading">
                🌦️ Συνδυασμός ECMWF + GFS + ICON...
            </span>
            `;


        await loadModels();


        renderCurrent();
        renderDays();


        statusBox.innerHTML =
            "";


        lastUpdate.textContent =
            "Τελευταία ενημέρωση: " +
            new Date()
                .toLocaleTimeString(
                    "el-GR",
                    {
                        hour:"2-digit",
                        minute:"2-digit"
                    }
                );

    }
    catch(error){

        locationCard.innerHTML = "";
        currentBox.innerHTML = "";
        daysBox.innerHTML = "";
        hourlyBox.innerHTML = "";

        hourlySection.style.display =
            "none";


        modelStatus.textContent =
            "Μοντέλα: —";


        statusBox.innerHTML =
            `
            <span class="error">
                ❌ ${escapeHTML(
                    error.message
                )}
            </span>
            `;

    }
    finally{

        searchBtn.disabled =
            false;

    }

}


/* =========================================================
   START
========================================================= */

searchBtn.addEventListener(
    "click",
    performSearch
);


cityInput.addEventListener(
    "keydown",
    e => {

        if(e.key === "Enter")
            performSearch();

    }
);


(async function(){

    await performSearch();

    scheduleRefresh();

})();

</script>

</body>

</html>
