<!DOCTYPE html>
<html lang="el">

<head>

<meta charset="UTF-8">

<meta name="viewport"
      content="width=device-width, initial-scale=1.0">

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

/* =========================
   SEARCH
========================= */

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

.search-box button:hover{
    background:#0d75cc;
}

.search-box button:disabled{
    opacity:.6;
    cursor:wait;
}

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

/* =========================
   LOCATION
========================= */

.location-card{
    background:rgba(255,255,255,.09);
    border:1px solid rgba(255,255,255,.10);
    border-radius:18px;
    padding:18px;
    margin-bottom:16px;
    text-align:center;
    box-shadow:0 8px 30px rgba(0,0,0,.15);
}

.location-name{
    font-size:29px;
    font-weight:bold;
}

.location-country{
    margin-top:7px;
    font-size:17px;
    opacity:.9;
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

.location-coordinates{
    margin-top:7px;
    font-size:12px;
    opacity:.45;
}

/* =========================
   CURRENT
========================= */

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
    font-size:70px;
    width:82px;
    text-align:center;
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

/* =========================
   MODEL INFO
========================= */

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

/* =========================
   SECTION
========================= */

.section-title{
    font-size:22px;
    font-weight:bold;
    margin:22px 0 12px;
}

/* =========================
   15 DAYS
   6 + 6 + 3
========================= */

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
    height:48px;

    display:flex;
    align-items:center;
    justify-content:center;

    font-size:39px;

    margin:8px 0;
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

/* precipitation only when >=30% */

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

/* =========================
   HOURLY
========================= */

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
    font-size:29px;
    text-align:center;
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

/* =========================
   SUN
========================= */

.sun-info{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:10px;
    margin-top:14px;
}

.sun-box{
    background:rgba(255,255,255,.08);
    border-radius:13px;
    padding:12px;
    text-align:center;
}

/* =========================
   FOOTER
========================= */

footer{
    text-align:center;
    margin-top:35px;
    padding:20px;
    opacity:.5;
    font-size:12px;
}

/* =========================
   TABLET
========================= */

@media(max-width:1050px){

    .days{
        grid-template-columns:
            repeat(4,minmax(0,1fr));
    }

}

/* =========================
   MOBILE
========================= */

@media(max-width:750px){

    .current{
        grid-template-columns:1fr;
    }

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

/* =========================
   SMALL MOBILE
========================= */

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

    .current-icon{
        font-size:55px;
        width:65px;
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

        padding:9px 7px;
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


<!-- SEARCH -->

<div class="search-box">

<input
    id="cityInput"
    type="text"
    value="Θεσσαλονίκη"
    placeholder="Γράψε πόλη ή περιοχή..."
    autocomplete="off"
>

<button
    id="searchBtn"
>
    🔎 Αναζήτηση
</button>

</div>


<div
    id="status"
    class="status"
></div>


<!-- LOCATION -->

<div
    id="locationCard"
></div>


<!-- CURRENT -->

<div
    id="current"
></div>


<!-- MODEL INFO -->

<div class="model-info">

<div class="model-main">
📡 Multi-model πρόγνωση:
ECMWF IFS • NOAA GFS • DWD ICON
</div>

<div class="model-sub">
Οι διαθέσιμες τιμές συνδυάζονται από τα ενεργά μοντέλα.
</div>

<div class="model-sub">
Έλεγχος νέων δεδομένων κάθε 5 λεπτά στα :00, :05, :10, :15...
</div>

<div
    id="modelStatus"
    class="model-status"
>
Μοντέλα: αναμονή δεδομένων...
</div>

<div
    id="lastUpdate"
    class="model-sub"
>
Τελευταίος έλεγχος: —
</div>

</div>


<!-- 15 DAYS -->

<div class="section-title">
📅 Πρόγνωση 15 ημερών
</div>


<div
    id="days"
    class="days"
></div>


<!-- HOURLY -->

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

Weather data powered by Open-Meteo
<br>
ECMWF IFS • NOAA GFS • DWD ICON

</footer>


</div>


<script>

/* =========================================================
   GREECE WEATHER
   MULTI-MODEL VERSION

   Models:
   ECMWF IFS
   NOAA GFS
   DWD ICON

   Main idea:
   Request models independently.
   Combine available values instead of
   changing to a different model after refresh.
========================================================= */


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

let refreshTimer = null;


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
   WEATHER DESCRIPTION
========================================================= */

function weatherDescription(code){

    const c = Number(code);

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

    return "Άγνωστο";
}


/* =========================================================
   ONE-EMOJI WEATHER ICONS

   IMPORTANT:
   NEVER returns moon + cloud together.
   One emoji only.
========================================================= */

function weatherIcon(code,isDay=true){

    const c = Number(code);

    if(!isDay){

        if(c === 0)
            return "🌙";

        if(c === 1)
            return "🌙";

        if(c === 2)
            return "🌥️";

        if(c === 3)
            return "☁️";

        if([45,48].includes(c))
            return "🌫️";

        if(
            [51,53,55,
             56,57,
             61,63,65,
             66,67,
             80,81,82].includes(c)
        )
            return "🌧️";

        if(
            [71,73,75,77,
             85,86].includes(c)
        )
            return "🌨️";

        if([95,96,99].includes(c))
            return "⛈️";

        return "🌙";
    }


    if(c === 0)
        return "☀️";

    if(c === 1)
        return "🌤️";

    if(c === 2)
        return "⛅";

    if(c === 3)
        return "☁️";

    if([45,48].includes(c))
        return "🌫️";

    if([51,53,55])
        return "🌦️";

    if([56,57].includes(c))
        return "🌧️";

    if([61,63,65,
        66,67].includes(c))
        return "🌧️";

    if([71,73,75,77].includes(c))
        return "❄️";

    if([80,81,82].includes(c))
        return "🌦️";

    if([85,86].includes(c))
        return "🌨️";

    if([95,96,99].includes(c))
        return "⛈️";

    return "🌤️";
}


/* =========================================================
   IMPORTANT FIX:
   precipitating icon is only shown if
   probability >= 30%.

   This function overrides weather icon
   when probability is below threshold.
========================================================= */

function finalWeatherIcon(
    code,
    isDay,
    precipitationProbability
){

    const probability =
        Number(
            precipitationProbability || 0
        );

    /*
       If precipitation probability is below 30%,
       do NOT show precipitation emoji.
    */

    if(probability < 30){

        const c = Number(code);

        if(!isDay){

            if(c === 0 || c === 1)
                return "🌙";

            if(c === 2)
                return "🌥️";

            if(c === 3 ||
               [45,48].includes(c))
                return "☁️";

            /*
               Even if a model gives a precipitation
               code, probability <30 means no
               precipitation emoji.
            */

            return "🌙";
        }


        if(c === 0)
            return "☀️";

        if(c === 1)
            return "🌤️";

        if(c === 2)
            return "⛅";

        if(c === 3 ||
           [45,48].includes(c))
            return "☁️";

        return "🌤️";
    }


    /*
       >=30%:
       precipitation phenomenon is allowed.
    */

    return weatherIcon(code,isDay);
}


/* =========================================================
   WIND DIRECTION
========================================================= */

function windDirection(degrees){

    if(
        degrees === null ||
        degrees === undefined ||
        isNaN(degrees)
    )
        return "—";

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

    const index =
        Math.round(
            Number(degrees) / 45
        ) % 8;

    return dirs[index];
}


/* =========================================================
   COUNTRY FLAG
========================================================= */

function countryFlag(countryCode){

    if(!countryCode)
        return "🏳️";

    const code =
        String(countryCode)
        .toUpperCase();

    if(code.length !== 2)
        return "🏳️";

    return [...code]
        .map(
            char =>
                String.fromCodePoint(
                    127397 +
                    char.charCodeAt(0)
                )
        )
        .join("");
}


/* =========================================================
   ESCAPE HTML
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
   DATE HELPERS
========================================================= */

function dateObject(dateString){

    return new Date(
        dateString + "T12:00:00"
    );
}


function formatDate(dateString){

    return dateObject(dateString)
        .toLocaleDateString(
            "el-GR",
            {
                day:"2-digit",
                month:"2-digit"
            }
        );
}


function dayName(dateString){

    return dateObject(dateString)
        .toLocaleDateString(
            "el-GR",
            {
                weekday:"short"
            }
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

    return (
        valid.reduce(
            (sum,x) =>
                sum + Number(x),
            0
        ) / valid.length
    );
}


/* =========================================================
   ROUND
========================================================= */

function roundNumber(value,digits=1){

    if(
        value === null ||
        value === undefined ||
        isNaN(value)
    )
        return null;

    return Number(
        Number(value).toFixed(digits)
    );
}


/* =========================================================
   MODEL API
========================================================= */

async function getModelWeather(
    model,
    latitude,
    longitude
){

    const params =
        new URLSearchParams({

            latitude:latitude,

            longitude:longitude,

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
                "rain",
                "showers",
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
                "rain_sum",
                "showers_sum",
                "snowfall_sum",
                "precipitation_probability_max",
                "wind_speed_10m_max",
                "wind_gusts_10m_max",
                "wind_direction_10m_dominant"
            ].join(",")

        });


    const url =
        "https://api.open-meteo.com/v1/forecast?" +
        params.toString();


    const response =
        await fetch(url);


    if(!response.ok){

        throw new Error(
            model.name +
            " δεν απάντησε."
        );

    }


    const data =
        await response.json();


    data.__model =
        model;


    return data;
}


/* =========================================================
   SEARCH LOCATION
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
            "Σφάλμα κατά την αναζήτηση."
        );


    const data =
        await response.json();


    if(
        !data.results ||
        data.results.length === 0
    ){

        throw new Error(
            "Δεν βρέθηκε η περιοχή. Γράψε υπαρκτή πόλη ή περιοχή."
        );

    }


    const normalized =
        query.trim().toLowerCase();


    const exact =
        data.results.find(
            item =>
                String(item.name)
                .toLowerCase() === normalized
        );


    return exact || data.results[0];
}


/* =========================================================
   LOAD ALL MODELS
========================================================= */

async function loadAllModels(){

    modelStatus.textContent =
        "Μοντέλα: λήψη ECMWF + GFS + ICON...";


    const results =
        await Promise.allSettled(

            MODELS.map(
                model =>
                    getModelWeather(
                        model,
                        locationData.latitude,
                        locationData.longitude
                    )
            )

        );


    modelData =
        results
            .filter(
                result =>
                    result.status === "fulfilled"
            )
            .map(
                result =>
                    result.value
            );


    if(!modelData.length){

        throw new Error(
            "Δεν ήταν δυνατή η λήψη δεδομένων από τα μοντέλα."
        );

    }


    const names =
        modelData
            .map(
                data =>
                    data.__model.short
            )
            .join(" + ");


    modelStatus.textContent =
        "Ενεργά μοντέλα: " + names;


    if(modelData.length < 3){

        modelStatus.textContent +=
            " • Κάποιο μοντέλο δεν ήταν προσωρινά διαθέσιμο.";

    }


    combineModels();
}


/* =========================================================
   FIND HOURLY INDEX BY TIME
========================================================= */

function getHourlyTimes(){

    const first =
        modelData.find(
            x =>
                x.hourly &&
                x.hourly.time
        );

    if(!first)
        return [];

    return first.hourly.time;
}


/* =========================================================
   COMBINE CURRENT DATA
========================================================= */

function combineCurrent(){

    const currents =
        modelData
            .map(
                data =>
                    data.current
            )
            .filter(Boolean);


    if(!currents.length)
        return null;


    return {

        temperature_2m:
            average(
                currents.map(
                    x =>
                        x.temperature_2m
                )
            ),

        relative_humidity_2m:
            average(
                currents.map(
                    x =>
                        x.relative_humidity_2m
                )
            ),

        apparent_temperature:
            average(
                currents.map(
                    x =>
                        x.apparent_temperature
                )
            ),

        is_day:
            currents[0].is_day,

        precipitation:
            average(
                currents.map(
                    x =>
                        x.precipitation
                )
            ),

        cloud_cover:
            average(
                currents.map(
                    x =>
                        x.cloud_cover
                )
            ),

        wind_speed_10m:
            average(
                currents.map(
                    x =>
                        x.wind_speed_10m
                )
            ),

        wind_direction_10m:
            average(
                currents.map(
                    x =>
                        x.wind_direction_10m
                )
            ),

        wind_gusts_10m:
            average(
                currents.map(
                    x =>
                        x.wind_gusts_10m
                )
            )

    };
}


/* =========================================================
   COMBINE HOURLY DATA

   Weather code is selected using the model
   with strongest precipitation probability.
   Numerical fields are averaged.
========================================================= */

function combineHourly(){

    const baseTimes =
        getHourlyTimes();


    const result = {

        time:[],
        temperature_2m:[],
        apparent_temperature:[],
        precipitation_probability:[],
        precipitation:[],
        weather_code:[],
        wind_speed_10m:[],
        wind_direction_10m:[],
        wind_gusts_10m:[],
        is_day:[]

    };


    for(
        let i=0;
        i<baseTimes.length;
        i++
    ){

        const time =
            baseTimes[i];


        const entries = [];


        for(
            const data of modelData
        ){

            const index =
                data.hourly.time.indexOf(
                    time
                );


            if(index === -1)
                continue;


            entries.push({

                temp:
                    data.hourly.temperature_2m[index],

                apparent:
                    data.hourly.apparent_temperature[index],

                probability:
                    data.hourly.precipitation_probability
                        ? data.hourly.precipitation_probability[index]
                        : 0,

                precipitation:
                    data.hourly.precipitation[index],

                code:
                    data.hourly.weather_code[index],

                wind:
                    data.hourly.wind_speed_10m[index],

                direction:
                    data.hourly.wind_direction_10m[index],

                gust:
                    data.hourly.wind_gusts_10m[index],

                isDay:
                    data.hourly.is_day[index]

            });

        }


        if(!entries.length)
            continue;


        /*
           Average numerical fields.
        */

        result.time.push(time);

        result.temperature_2m.push(
            average(
                entries.map(
                    x =>
                        x.temp
                )
            )
        );

        result.apparent_temperature.push(
            average(
                entries.map(
                    x =>
                        x.apparent
                )
            )
        );

        result.precipitation_probability.push(
            average(
                entries.map(
                    x =>
                        x.probability
                )
            )
        );

        result.precipitation.push(
            average(
                entries.map(
                    x =>
                        x.precipitation
                )
            )
        );

        result.wind_speed_10m.push(
            average(
                entries.map(
                    x =>
                        x.wind
                )
            )
        );

        result.wind_direction_10m.push(
            average(
                entries.map(
                    x =>
                        x.direction
                )
            )
        );

        result.wind_gusts_10m.push(
            average(
                entries.map(
                    x =>
                        x.gust
                )
            )
        );

        result.is_day.push(
            entries[0].isDay
        );


        /*
           Select weather phenomenon from
           the model with highest probability.

           This avoids averaging WMO codes,
           because WMO codes are categorical.
        */

        const strongest =
            entries.reduce(
                (best,current) => {

                    if(!best)
                        return current;

                    return
                        current.probability >
                        best.probability
                            ? current
                            : best;

                },
                null
            );


        result.weather_code.push(
            strongest
                ? strongest.code
                : 0
        );

    }


    return result;
}


/* =========================================================
   COMBINE DAILY DATA
========================================================= */

function combineDaily(){

    const first =
        modelData.find(
            x =>
                x.daily &&
                x.daily.time
        );


    if(!first)
        return null;


    const dates =
        first.daily.time;


    const result = {

        time:dates,

        temperature_2m_max:[],
        temperature_2m_min:[],

        apparent_temperature_max:[],
        apparent_temperature_min:[],

        precipitation_sum:[],
        precipitation_probability_max:[],

        weather_code:[],

        wind_speed_10m_max:[],
        wind_gusts_10m_max:[],
        wind_direction_10m_dominant:[],

        sunrise:[],
        sunset:[]

    };


    for(
        let day=0;
        day<dates.length;
        day++
    ){

        const date =
            dates[day];


        const rows = [];


        for(
            const data of modelData
        ){

            const index =
                data.daily.time.indexOf(
                    date
                );


            if(index === -1)
                continue;


            rows.push({

                max:
                    data.daily.temperature_2m_max[index],

                min:
                    data.daily.temperature_2m_min[index],

                apparentMax:
                    data.daily.apparent_temperature_max[index],

                apparentMin:
                    data.daily.apparent_temperature_min[index],

                precipitation:
                    data.daily.precipitation_sum[index],

                probability:
                    data.daily.precipitation_probability_max
                        ? data.daily.precipitation_probability_max[index]
                        : 0,

                code:
                    data.daily.weather_code[index],

                wind:
                    data.daily.wind_speed_10m_max[index],

                gust:
                    data.daily.wind_gusts_10m_max[index],

                direction:
                    data.daily.wind_direction_10m_dominant[index],

                sunrise:
                    data.daily.sunrise[index],

                sunset:
                    data.daily.sunset[index]

            });

        }


        if(!rows.length)
            continue;


        result.temperature_2m_max.push(
            average(
                rows.map(
                    x =>
                        x.max
                )
            )
        );


        result.temperature_2m_min.push(
            average(
                rows.map(
                    x =>
                        x.min
                )
            )
        );


        result.apparent_temperature_max.push(
            average(
                rows.map(
                    x =>
                        x.apparentMax
                )
            )
        );


        result.apparent_temperature_min.push(
            average(
                rows.map(
                    x =>
                        x.apparentMin
                )
            )
        );


        result.precipitation_sum.push(
            average(
                rows.map(
                    x =>
                        x.precipitation
                )
            )
        );


        /*
           IMPORTANT:
           Daily precipitation probability
           is also averaged between models.
        */

        const probability =
            average(
                rows.map(
                    x =>
                        x.probability
                )
            );


        result.precipitation_probability_max.push(
            probability
        );


        result.wind_speed_10m_max.push(
            average(
                rows.map(
                    x =>
                        x.wind
                )
            )
        );


        result.wind_gusts_10m_max.push(
            average(
                rows.map(
                    x =>
                        x.gust
                )
            )
        );


        result.wind_direction_10m_dominant.push(
            average(
                rows.map(
                    x =>
                        x.direction
                )
            )
        );


        result.sunrise.push(
            rows[0].sunrise
        );


        result.sunset.push(
            rows[0].sunset
        );


        /*
           Again, categorical weather code:
           select strongest precipitating model.
        */

        const strongest =
            rows.reduce(
                (best,current) => {

                    if(!best)
                        return current;

                    return
                        current.probability >
                        best.probability
                            ? current
                            : best;

                },
                null
            );


        result.weather_code.push(
            strongest
                ? strongest.code
                : 0
        );

    }


    return result;
}


/* =========================================================
   COMBINE EVERYTHING
========================================================= */

function combineModels(){

    combinedWeather = {

        current:
            combineCurrent(),

        hourly:
            combineHourly(),

        daily:
            combineDaily()

    };

}


/* =========================================================
   LOCATION DISPLAY
========================================================= */

function renderLocation(){

    const x =
        locationData;


    const flag =
        countryFlag(
            x.country_code
        );


    const country =
        x.country ||
        "Άγνωστη χώρα";


    const admin =
        x.admin1 ||
        "";


    locationCard.innerHTML = `

        <div class="location-name">

            ${escapeHTML(x.name)}

        </div>


        <div class="location-country">

            <span class="country-flag">
                ${flag}
            </span>

            ${escapeHTML(country)}

        </div>


        ${
            admin
                ?
                `
                <div class="location-admin">
                    ${escapeHTML(admin)}
                </div>
                `
                :
                ""
        }


        <div class="location-coordinates">

            ${Number(x.latitude).toFixed(3)}
            ,
            ${Number(x.longitude).toFixed(3)}

        </div>

    `;
}


/* =========================================================
   CURRENT DISPLAY
========================================================= */

function renderCurrent(){

    const c =
        combinedWeather.current;


    if(!c)
        return;


    const isDay =
        Number(c.is_day) === 1;


    /*
       Current precipitation probability
       comes from closest hourly time.
    */

    const now =
        new Date();


    let probability = 0;


    if(
        combinedWeather.hourly &&
        combinedWeather.hourly.time.length
    ){

        let closest = 0;

        let smallest =
            Infinity;


        combinedWeather.hourly.time
            .forEach(
                (time,index) => {

                    const difference =
                        Math.abs(
                            new Date(time) -
                            now
                        );

                    if(
                        difference <
                        smallest
                    ){

                        smallest =
                            difference;

                        closest =
                            index;

                    }

                }
            );


        probability =
            Number(
                combinedWeather
                    .hourly
                    .precipitation_probability[
                        closest
                    ] || 0
            );

    }


    const icon =
        finalWeatherIcon(
            0,
            isDay,
            probability
        );


    /*
       For current weather we derive
       non-precipitating condition from cloud cover
       if precipitation probability <30.
    */

    let currentCode = 0;


    if(c.cloud_cover >= 85)
        currentCode = 3;

    else if(c.cloud_cover >= 55)
        currentCode = 2;

    else if(c.cloud_cover >= 25)
        currentCode = 1;

    else
        currentCode = 0;


    const finalIcon =
        finalWeatherIcon(
            currentCode,
            isDay,
            probability
        );


    const temp =
        Math.round(
            c.temperature_2m
        );


    const feels =
        Math.round(
            c.apparent_temperature
        );


    const humidity =
        Math.round(
            c.relative_humidity_2m
        );


    const wind =
        Math.round(
            c.wind_speed_10m
        );


    const gust =
        Math.round(
            c.wind_gusts_10m
        );


    const direction =
        windDirection(
            c.wind_direction_10m
        );


    const precipitation =
        Number(
            c.precipitation || 0
        );


    /*
       Current precipitation emoji only
       if probability >=30.
    */

    const precipitationHTML =
        probability >= 30
            ?
            `
            <div class="detail">
                <div class="detail-label">
                    💧 Υετός
                </div>

                <div class="detail-value">
                    ${precipitation.toFixed(1)} mm
                    (${Math.round(probability)}%)
                </div>
            </div>
            `
            :
            `
            <div class="detail">
                <div class="detail-label">
                    Υετός
                </div>

                <div class="detail-value">
                    ${precipitation.toFixed(1)} mm
                </div>
            </div>
            `;


    currentBox.innerHTML = `

        <div class="current">


            <div class="current-card">

                <div class="current-main">

                    <div class="current-icon">
                        ${finalIcon}
                    </div>


                    <div>

                        <div class="current-temp">
                            ${temp}°C
                        </div>


                        <div class="current-description">

                            ${
                                probability >= 30
                                    ? weatherDescription(
                                        combinedWeather
                                            .hourly
                                            .weather_code[0]
                                      )
                                    : weatherDescription(
                                        currentCode
                                      )
                            }

                        </div>


                        <div class="current-time">

                            Αίσθηση ${feels}°C

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
                            ${humidity}%
                        </div>

                    </div>


                    <div class="detail">

                        <div class="detail-label">
                            💨 Άνεμος
                        </div>

                        <div class="detail-value">
                            ${wind} km/h
                            ${direction}
                        </div>

                    </div>


                    <div class="detail">

                        <div class="detail-label">
                            💨 Ριπές
                        </div>

                        <div class="detail-value">
                            ${gust} km/h
                        </div>

                    </div>


                    ${precipitationHTML}


                </div>

            </div>


        </div>

    `;
}


/* =========================================================
   DAILY DISPLAY
========================================================= */

function renderDays(){

    daysBox.innerHTML = "";


    const d =
        combinedWeather.daily;


    if(!d)
        return;


    for(
        let i=0;
        i<Math.min(15,d.time.length);
        i++
    ){

        const date =
            d.time[i];


        const probability =
            Number(
                d.precipitation_probability_max[i] ||
                0
            );


        const precipitation =
            Number(
                d.precipitation_sum[i] ||
                0
            );


        /*
           Estimate day/night based on
           daily weather code + sunrise/sunset.
        */

        const code =
            d.weather_code[i];


        let icon;


        if(probability >= 30){

            icon =
                weatherIcon(
                    code,
                    true
                );

        }
        else{

            /*
               No precipitation emoji under 30%.
               Use cloud/clear category only.
            */

            if(code === 0)
                icon = "☀️";

            else if(code === 1)
                icon = "🌤️";

            else if(code === 2)
                icon = "⛅";

            else
                icon = "☁️";

        }


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
           Precipitation emoji is shown ONLY
           at >=30%.
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
                ${weatherDescription(code)}
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
   HOURLY DISPLAY
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
            !h.time[i].startsWith(
                date
            )
        )
            continue;


        const code =
            h.weather_code[i];


        const isDay =
            Number(
                h.is_day[i]
            ) === 1;


        const probability =
            Number(
                h.precipitation_probability[i] ||
                0
            );


        const precipitation =
            Number(
                h.precipitation[i] ||
                0
            );


        const temp =
            Math.round(
                h.temperature_2m[i]
            );


        const wind =
            Math.round(
                h.wind_speed_10m[i]
            );


        const gust =
            Math.round(
                h.wind_gusts_10m[i]
            );


        const direction =
            windDirection(
                h.wind_direction_10m[i]
            );


        const icon =
            finalWeatherIcon(
                code,
                isDay,
                probability
            );


        const time =
            h.time[i]
                .split("T")[1]
                .substring(0,5);


        const row =
            document.createElement(
                "div"
            );


        row.className =
            "hour";


        /*
           Precipitation emoji ONLY >=30%.
        */

        const rainHTML =
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

                    ${temp}°C

                </div>
                `;


        row.innerHTML = `

            <div class="hour-time">
                ${time}
            </div>


            <div class="hour-icon">
                ${icon}
            </div>


            <div class="hour-temp">
                ${temp}°C
            </div>


            ${rainHTML}


            <div class="hour-wind">

                💨 ${wind} km/h

                <br>

                Ριπές ${gust}

            </div>


            <div class="hour-dir">

                ${direction}

            </div>

        `;


        hourlyBox.appendChild(
            row
        );

    }


    hourlySection.style.display =
        "block";
}


/* =========================================================
   REFRESH WEATHER
========================================================= */

async function refreshWeather(){

    if(!locationData)
        return;


    try{

        modelStatus.textContent =
            "Μοντέλα: έλεγχος για νέα δεδομένα...";


        await loadAllModels();


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

        modelStatus.textContent =
            "Προσωρινό πρόβλημα ενημέρωσης.";

        console.error(error);

    }

}


/* =========================================================
   EXACT 5-MINUTE REFRESH
   :00 :05 :10 :15 :20...
========================================================= */

function scheduleRefresh(){

    if(refreshTimer)
        clearTimeout(
            refreshTimer
        );


    const now =
        new Date();


    const millisecondsUntilNext5 =
        (
            5 * 60 * 1000
        ) -
        (
            (
                now.getMinutes() % 5
            ) *
            60 *
            1000
            +
            now.getSeconds() * 1000
            +
            now.getMilliseconds()
        );


    refreshTimer =
        setTimeout(
            async () => {

                await refreshWeather();

                scheduleRefresh();

            },

            Math.max(
                1000,
                millisecondsUntilNext5
            )

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
                Γράψε μια περιοχή για αναζήτηση.
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

        const result =
            await searchLocation(
                query
            );


        locationData =
            result;


        renderLocation();


        statusBox.innerHTML =
            `
            <span class="loading">
                🌦️ Λήψη ECMWF + GFS + ICON...
            </span>
            `;


        await loadAllModels();


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

        console.error(error);


        locationCard.innerHTML =
            "";


        currentBox.innerHTML =
            "";


        daysBox.innerHTML =
            "";


        hourlyBox.innerHTML =
            "";


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
   EVENTS
========================================================= */

searchBtn.addEventListener(
    "click",
    performSearch
);


cityInput.addEventListener(
    "keydown",
    event => {

        if(
            event.key === "Enter"
        ){

            performSearch();

        }

    }
);


/* =========================================================
   START
========================================================= */

(async function(){

    await performSearch();

    scheduleRefresh();

})();

</script>

</body>

</html>
