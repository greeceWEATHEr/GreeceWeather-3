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

html{
    scroll-behavior:smooth;
}

body{
    margin:0;
    font-family:Arial,Helvetica,sans-serif;
    color:#fff;

    background:
        linear-gradient(
            180deg,
            #071d35 0%,
            #0a294b 45%,
            #0d3762 100%
        );

    min-height:100vh;
}

/* =========================
   HEADER
========================= */

header{
    text-align:center;
    padding:28px 15px 18px;
}

header h1{
    margin:0;
    font-size:32px;
    font-weight:800;
}

header p{
    margin:8px 0 0;
    color:#c9def3;
    font-size:15px;
}

/* =========================
   SEARCH
========================= */

.search-area{
    width:min(900px,94%);
    margin:10px auto 20px;

    display:flex;
    gap:10px;
}

.search-area input{
    flex:1;

    padding:15px 17px;

    border:none;
    outline:none;

    border-radius:14px;

    background:rgba(255,255,255,.12);
    color:#fff;

    font-size:16px;

    box-shadow:
        inset 0 0 0 1px rgba(255,255,255,.12);
}

.search-area input::placeholder{
    color:#b8cde1;
}

.search-area button{
    border:none;
    border-radius:14px;

    padding:0 22px;

    background:#168cff;
    color:#fff;

    font-weight:bold;
    font-size:15px;

    cursor:pointer;

    transition:.2s;
}

.search-area button:hover{
    background:#0d75d8;
    transform:translateY(-1px);
}

/* =========================
   STATUS
========================= */

.status{
    width:min(900px,94%);
    margin:0 auto 18px;

    text-align:center;

    min-height:22px;

    font-size:14px;
    color:#c8def3;
}

.status.error{
    color:#ff9b9b;
    font-weight:bold;
}

/* =========================
   LOCATION
========================= */

.location-box{
    width:min(900px,94%);
    margin:0 auto 20px;

    padding:20px;

    border-radius:20px;

    background:
        linear-gradient(
            135deg,
            rgba(18,80,135,.8),
            rgba(7,40,73,.8)
        );

    border:1px solid rgba(255,255,255,.12);

    box-shadow:
        0 12px 35px rgba(0,0,0,.18);

    text-align:center;
}

.location-name{
    font-size:28px;
    font-weight:800;
}

.country-name{
    margin-top:7px;
    color:#bcd6ee;
    font-size:15px;
}

.update-info{
    margin-top:12px;
    color:#91b4d3;
    font-size:12px;
}

/* =========================
   MODEL INFO
========================= */

.model-box{
    width:min(900px,94%);
    margin:0 auto 20px;

    text-align:center;

    padding:12px;

    border-radius:14px;

    background:rgba(255,255,255,.06);

    color:#b9d2e9;

    font-size:12px;

    border:1px solid rgba(255,255,255,.08);
}

.model-box strong{
    color:#e6f3ff;
}

/* =========================
   FORECAST
========================= */

.forecast-title{
    width:min(1400px,94%);
    margin:25px auto 14px;

    font-size:22px;
    font-weight:800;
}

.forecast-grid{
    width:min(1400px,94%);
    margin:0 auto;

    display:grid;

    grid-template-columns:
        repeat(5, minmax(0,1fr));

    gap:14px;
}

/* =========================
   DAY CARD
========================= */

.day-card{
    position:relative;

    min-width:0;

    padding:17px;

    border-radius:20px;

    background:
        linear-gradient(
            180deg,
            rgba(255,255,255,.13),
            rgba(255,255,255,.07)
        );

    border:1px solid rgba(255,255,255,.12);

    box-shadow:
        0 10px 30px rgba(0,0,0,.15);

    transition:.2s;
}

.day-card:hover{
    transform:translateY(-2px);

    border-color:
        rgba(255,255,255,.25);
}

.day-card.hidden-card{
    display:none;
}

/* =========================
   CLOSE BUTTON
========================= */

.close-day{
    position:absolute;

    top:8px;
    right:9px;

    width:28px;
    height:28px;

    border-radius:50%;

    border:1px solid rgba(255,255,255,.2);

    background:rgba(0,0,0,.18);

    color:#fff;

    cursor:pointer;

    font-size:17px;

    line-height:25px;

    padding:0;
}

.close-day:hover{
    background:rgba(255,80,80,.35);
}

/* =========================
   DAY HEADER
========================= */

.day-name{
    text-align:center;

    font-weight:800;

    font-size:17px;

    margin-bottom:4px;

    padding-right:18px;
}

.date{
    text-align:center;

    color:#a9c5df;

    font-size:12px;

    margin-bottom:12px;
}

/* =========================
   ICONS
========================= */

.weather-icon{
    height:75px;

    display:flex;

    justify-content:center;

    align-items:center;

    font-size:52px;

    margin:4px 0;
}

.night-icon{
    font-size:38px;

    height:55px;
}

/* =========================
   TEMPERATURE
========================= */

.temps{
    text-align:center;

    margin:7px 0 13px;
}

.max-temp{
    font-size:28px;
    font-weight:800;
}

.min-temp{
    margin-top:3px;

    font-size:17px;

    color:#b7cbe0;
}

/* =========================
   DATA
========================= */

.data-row{
    display:flex;

    justify-content:space-between;

    gap:8px;

    padding:8px 0;

    border-top:
        1px solid rgba(255,255,255,.08);

    font-size:13px;
}

.data-label{
    color:#a9c2d9;
}

.data-value{
    font-weight:bold;

    text-align:right;
}

/* =========================
   PRECIPITATION
========================= */

.precip{
    margin-top:10px;

    padding:9px;

    border-radius:12px;

    background:rgba(30,150,255,.12);

    text-align:center;

    color:#bfe3ff;

    font-size:13px;
}

.precip strong{
    color:#fff;
}

/* =========================
   RESET
========================= */

.reset-area{
    width:min(1400px,94%);

    margin:20px auto 35px;

    text-align:center;
}

.reset-button{
    border:none;

    border-radius:13px;

    padding:11px 18px;

    background:rgba(255,255,255,.10);

    border:
        1px solid rgba(255,255,255,.13);

    color:#dcecff;

    cursor:pointer;

    font-weight:bold;
}

.reset-button:hover{
    background:rgba(255,255,255,.17);
}

/* =========================
   FOOTER
========================= */

footer{
    text-align:center;

    padding:25px 15px 35px;

    color:#7898b7;

    font-size:11px;
}

/* =========================
   RESPONSIVE
========================= */

@media(max-width:1100px){

    .forecast-grid{
        grid-template-columns:
            repeat(3,minmax(0,1fr));
    }

}

@media(max-width:720px){

    header h1{
        font-size:26px;
    }

    .search-area{
        flex-direction:column;
    }

    .search-area button{
        min-height:48px;
    }

    .forecast-grid{
        grid-template-columns:
            repeat(2,minmax(0,1fr));

        gap:10px;
    }

    .day-card{
        padding:13px;
    }

    .day-name{
        font-size:15px;
    }

    .max-temp{
        font-size:24px;
    }

}

@media(max-width:460px){

    .forecast-grid{
        grid-template-columns:1fr;
    }

}

/* =========================
   LOADING
========================= */

.loading{
    opacity:.55;
    pointer-events:none;
}

</style>

</head>

<body>

<header>

    <h1>🇬🇷 Greece Weather</h1>

    <p>
        Πρόγνωση καιρού για όλη την Ελλάδα και τον κόσμο
    </p>

</header>


<div class="search-area">

    <input
        id="searchInput"
        type="text"
        value="Θεσσαλονίκη"
        placeholder="Γράψε πόλη ή περιοχή..."
        autocomplete="off"
    >

    <button id="searchButton">
        Αναζήτηση
    </button>

</div>


<div
    id="status"
    class="status">
</div>


<div
    id="locationBox"
    class="location-box">

    <div
        id="locationName"
        class="location-name">
        Θεσσαλονίκη
    </div>

    <div
        id="countryName"
        class="country-name">
        🇬🇷 Ελλάδα
    </div>

    <div
        id="updateInfo"
        class="update-info">
        Φόρτωση δεδομένων...
    </div>

</div>


<div class="model-box">

    <strong>Μετεωρολογικά δεδομένα</strong><br>

    ECMWF IFS • NOAA GFS • DWD ICON /
    αυτόματη επιλογή κατάλληλου μοντέλου ανά περιοχή

    <br><br>

    🔄 Αυτόματη ανανέωση εφαρμογής:
    κάθε 5 λεπτά στα
    <strong>00, 05, 10, 15, 20...</strong>

</div>


<div class="forecast-title">

    📅 Πρόγνωση 15 ημερών

</div>


<div
    id="forecastGrid"
    class="forecast-grid">
</div>


<div class="reset-area">

    <button
        id="resetButton"
        class="reset-button">

        ↩ Εμφάνιση όλων των ημερών

    </button>

</div>


<footer>

    Τα δεδομένα προέρχονται από Open-Meteo.
    Η ανανέωση της σελίδας δεν σημαίνει ότι έχει
    δημιουργηθεί νέο model run.

</footer>


<script>

/* =========================================================
   GLOBALS
========================================================= */

let currentLocation = null;

let currentWeather = null;

let hiddenDays = new Set();

let lastSuccessfulSearch = "";


/* =========================================================
   ELEMENTS
========================================================= */

const searchInput =
    document.getElementById("searchInput");

const searchButton =
    document.getElementById("searchButton");

const statusBox =
    document.getElementById("status");

const forecastGrid =
    document.getElementById("forecastGrid");

const locationName =
    document.getElementById("locationName");

const countryName =
    document.getElementById("countryName");

const updateInfo =
    document.getElementById("updateInfo");

const resetButton =
    document.getElementById("resetButton");


/* =========================================================
   COUNTRY FLAGS
========================================================= */

function countryFlag(code){

    if(!code) return "🌍";

    code = code.toUpperCase();

    if(code.length !== 2){
        return "🌍";
    }

    return String.fromCodePoint(
        ...[...code].map(
            c => 127397 + c.charCodeAt(0)
        )
    );

}


/* =========================================================
   ERROR / STATUS
========================================================= */

function setStatus(message="", error=false){

    statusBox.textContent = message;

    statusBox.classList.toggle(
        "error",
        error
    );

}


/* =========================================================
   WEATHER ICON
   DAY AND NIGHT USE CORRESPONDING CONDITIONS
========================================================= */

function weatherIcon(code, isDay, precipitationProbability){

    const precipOK =
        Number(precipitationProbability || 0) >= 30;


    /*
       WMO WEATHER CODES

       0  clear
       1  mainly clear
       2  partly cloudy
       3  overcast
       45/48 fog
       51-57 drizzle
       61-67 rain
       71-77 snow
       80-82 showers
       85-86 snow showers
       95-99 thunderstorms
    */


    /* =========================
       PRECIPITATION FIRST
    ========================= */

    if(precipOK){

        if(
            code === 95 ||
            code === 96 ||
            code === 99
        ){

            return isDay
                ? "⛈️"
                : "🌙⛈️";

        }


        if(
            code >= 71 &&
            code <= 77
        ){

            return isDay
                ? "🌨️"
                : "🌙🌨️";

        }


        if(
            code >= 51 &&
            code <= 67
        ){

            return isDay
                ? "🌧️"
                : "🌙🌧️";

        }


        if(
            code >= 80 &&
            code <= 82
        ){

            return isDay
                ? "🌦️"
                : "🌙🌦️";

        }


        if(
            code >= 85 &&
            code <= 86
        ){

            return isDay
                ? "🌨️"
                : "🌙🌨️";

        }

    }


    /* =========================
       NO PRECIPITATION
    ========================= */

    if(
        code === 0
    ){

        return isDay
            ? "☀️"
            : "🌙";

    }


    if(
        code === 1
    ){

        return isDay
            ? "🌤️"
            : "🌙☁️";

    }


    if(
        code === 2
    ){

        return isDay
            ? "🌤️"
            : "🌙☁️";

    }


    if(
        code === 3
    ){

        return "☁️";

    }


    if(
        code === 45 ||
        code === 48
    ){

        return "🌫️";

    }


    return isDay
        ? "☀️"
        : "🌙";

}


/* =========================================================
   WIND DIRECTION
========================================================= */

function windDirection(deg){

    if(deg === null || deg === undefined){
        return "—";
    }

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

    const index =
        Math.round(deg / 45) % 8;

    return directions[index];

}


/* =========================================================
   FORMAT DATE
========================================================= */

function formatDate(dateString){

    const d =
        new Date(
            dateString + "T12:00:00"
        );

    return d.toLocaleDateString(
        "el-GR",
        {
            day:"2-digit",
            month:"2-digit"
        }
    );

}


/* =========================================================
   DAY NAME
========================================================= */

function dayName(dateString, index){

    if(index === 0){
        return "Σήμερα";
    }

    if(index === 1){
        return "Αύριο";
    }

    const d =
        new Date(
            dateString + "T12:00:00"
        );

    return d.toLocaleDateString(
        "el-GR",
        {
            weekday:"long"
        }
    );

}


/* =========================================================
   GEOCODING
========================================================= */

async function findLocation(query){

    const url =
        "https://geocoding-api.open-meteo.com/v1/search" +
        "?name=" +
        encodeURIComponent(query) +
        "&count=10" +
        "&language=el" +
        "&format=json";

    const response =
        await fetch(url);

    if(!response.ok){

        throw new Error(
            "Σφάλμα αναζήτησης."
        );

    }

    const data =
        await response.json();

    if(
        !data.results ||
        data.results.length === 0
    ){

        throw new Error(
            "Δεν βρέθηκε η περιοχή."
        );

    }


    /*
       Prefer an exact-ish result if possible.
    */

    const normalized =
        query.trim().toLowerCase();


    const exact =
        data.results.find(
            item =>
                item.name &&
                item.name.toLowerCase() === normalized
        );


    return exact || data.results[0];

}


/* =========================================================
   WEATHER REQUEST
========================================================= */

async function loadWeather(){

    if(!currentLocation){
        return;
    }


    const lat =
        currentLocation.latitude;

    const lon =
        currentLocation.longitude;


    const url =
        "https://api.open-meteo.com/v1/forecast" +

        "?latitude=" +
        encodeURIComponent(lat) +

        "&longitude=" +
        encodeURIComponent(lon) +

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
        "precipitation_sum," +
        "precipitation_probability_max," +
        "wind_speed_10m_max," +
        "wind_direction_10m_dominant," +
        "sunrise," +
        "sunset" +

        "&forecast_days=15" +

        "&timezone=auto" +

        "&temperature_unit=celsius" +

        "&wind_speed_unit=kmh" +

        "&precipitation_unit=mm";


    const response =
        await fetch(
            url,
            {
                cache:"no-store"
            }
        );


    if(!response.ok){

        throw new Error(
            "Δεν ήταν δυνατή η λήψη πρόγνωσης."
        );

    }


    const data =
        await response.json();


    currentWeather =
        data;


    renderForecast(
        data
    );


    updateInfo.textContent =
        "Τελευταία ενημέρωση εφαρμογής: " +
        new Date().toLocaleString(
            "el-GR"
        ) +
        " • Ζώνη ώρας: " +
        (data.timezone || "—");

}


/* =========================================================
   FIND DAY/NIGHT WEATHER CODE
========================================================= */

function getRepresentativeHour(
    weather,
    dateString,
    wantDay
){

    const times =
        weather.hourly.time;

    const codes =
        weather.hourly.weather_code;

    const probs =
        weather.hourly.precipitation_probability;

    const isDay =
        weather.hourly.is_day;


    let candidates = [];


    for(
        let i = 0;
        i < times.length;
        i++
    ){

        if(
            times[i].startsWith(
                dateString
            )
        ){

            if(
                Number(isDay[i]) ===
                (wantDay ? 1 : 0)
            ){

                candidates.push(i);

            }

        }

    }


    /*
       If a night/day value wasn't found,
       use the closest available hour.
    */

    if(candidates.length === 0){

        for(
            let i = 0;
            i < times.length;
            i++
        ){

            if(
                times[i].startsWith(
                    dateString
                )
            ){

                candidates.push(i);

            }

        }

    }


    if(candidates.length === 0){
        return null;
    }


    /*
       Select the middle representative
       hour to avoid using only midnight.
    */

    const index =
        candidates[
            Math.floor(
                candidates.length / 2
            )
        ];


    return {
        code: Number(codes[index] || 0),
        probability:
            Number(probs[index] || 0)
    };

}


/* =========================================================
   RENDER FORECAST
========================================================= */

function renderForecast(weather){

    forecastGrid.innerHTML = "";


    const daily =
        weather.daily;


    for(
        let i = 0;
        i < daily.time.length &&
        i < 15;
        i++
    ){

        const date =
            daily.time[i];


        const max =
            Math.round(
                daily.temperature_2m_max[i]
            );


        const min =
            Math.round(
                daily.temperature_2m_min[i]
            );


        const precipAmount =
            Number(
                daily.precipitation_sum[i] || 0
            );


        const precipProbability =
            Number(
                daily.precipitation_probability_max[i] || 0
            );


        const wind =
            Math.round(
                daily.wind_speed_10m_max[i] || 0
            );


        const windDir =
            Number(
                daily.wind_direction_10m_dominant[i] || 0
            );


        const dayRepresentative =
            getRepresentativeHour(
                weather,
                date,
                true
            );


        const nightRepresentative =
            getRepresentativeHour(
                weather,
                date,
                false
            );


        const dayCode =
            dayRepresentative
                ? dayRepresentative.code
                : Number(daily.weather_code[i]);


        const dayProbability =
            dayRepresentative
                ? dayRepresentative.probability
                : precipProbability;


        const nightCode =
            nightRepresentative
                ? nightRepresentative.code
                : dayCode;


        const nightProbability =
            nightRepresentative
                ? nightRepresentative.probability
                : precipProbability;


        const card =
            document.createElement("article");


        card.className =
            "day-card";


        card.dataset.index =
            i;


        if(
            hiddenDays.has(i)
        ){

            card.classList.add(
                "hidden-card"
            );

        }


        /*
           IMPORTANT:
           Night icon uses the SAME weather
           category as the night forecast,
           but with a night-specific icon.
        */


        const dayIcon =
            weatherIcon(
                dayCode,
                true,
                dayProbability
            );


        const nightIcon =
            weatherIcon(
                nightCode,
                false,
                nightProbability
            );


        const precipHTML =
            precipProbability >= 30

            ?

            `
            <div class="precip">
                💧 Υετός:
                <strong>
                    ${precipProbability}%
                </strong>
                • ${precipAmount.toFixed(1)} mm
            </div>
            `

            :

            `
            <div class="precip">
                💧
                <strong>
                    0–29%
                </strong>
                • χωρίς εμφάνιση φαινομένου υετού
            </div>
            `;


        card.innerHTML = `

            <button
                class="close-day"
                title="Κλείσιμο ημέρας"
                aria-label="Κλείσιμο ημέρας">
                ×
            </button>


            <div class="day-name">

                ${capitalize(
                    dayName(date,i)
                )}

            </div>


            <div class="date">

                ${formatDate(date)}

            </div>


            <div
                class="weather-icon"
                title="Καιρός ημέρας">

                ${dayIcon}

            </div>


            <div
                class="night-icon"
                style="display:flex;justify-content:center;align-items:center;"
                title="Καιρός νύχτας">

                ${nightIcon}

            </div>


            <div class="temps">

                <div class="max-temp">

                    ${max}°C

                </div>

                <div class="min-temp">

                    ${min}°C

                </div>

            </div>


            <div class="data-row">

                <span class="data-label">
                    🌬️ Άνεμος
                </span>

                <span class="data-value">

                    ${wind} km/h

                </span>

            </div>


            <div class="data-row">

                <span class="data-label">
                    🧭 Διεύθυνση
                </span>

                <span class="data-value">

                    ${windDirection(windDir)}

                    ${Math.round(windDir)}°

                </span>

            </div>


            ${precipHTML}

        `;


        const closeButton =
            card.querySelector(
                ".close-day"
            );


        closeButton.addEventListener(
            "click",
            function(){

                hiddenDays.add(i);

                card.classList.add(
                    "hidden-card"
                );

            }
        );


        forecastGrid.appendChild(
            card
        );

    }

}


/* =========================================================
   CAPITALIZE
========================================================= */

function capitalize(text){

    if(!text) return "";

    return text.charAt(0).toUpperCase()
        + text.slice(1);

}


/* =========================================================
   SEARCH
========================================================= */

async function searchLocation(){

    const query =
        searchInput.value.trim();


    if(!query){

        setStatus(
            "Γράψε μια περιοχή για αναζήτηση.",
            true
        );

        return;

    }


    setStatus(
        "🔎 Αναζήτηση..."
    );


    searchButton.disabled =
        true;


    try{

        const result =
            await findLocation(
                query
            );


        currentLocation =
            result;


        hiddenDays.clear();


        locationName.textContent =
            result.name || query;


        const country =
            result.country ||
            result.country_code ||
            "Άγνωστη χώρα";


        countryName.textContent =
            countryFlag(
                result.country_code
            ) +
            " " +
            country;


        lastSuccessfulSearch =
            query;


        await loadWeather();


        setStatus(
            ""
        );


    }
    catch(error){

        setStatus(
            "❌ Η περιοχή δεν βρέθηκε. " +
            "Δοκίμασε διαφορετική ονομασία.",
            true
        );

    }
    finally{

        searchButton.disabled =
            false;

    }

}


/* =========================================================
   RESET HIDDEN DAYS
========================================================= */

resetButton.addEventListener(
    "click",
    function(){

        hiddenDays.clear();


        document
            .querySelectorAll(
                ".day-card"
            )
            .forEach(
                card =>
                    card.classList.remove(
                        "hidden-card"
                    )
            );

    }
);


/* =========================================================
   EVENTS
========================================================= */

searchButton.addEventListener(
    "click",
    searchLocation
);


searchInput.addEventListener(
    "keydown",
    function(event){

        if(
            event.key === "Enter"
        ){

            searchLocation();

        }

    }
);


/* =========================================================
   AUTOMATIC REFRESH
   EXACTLY AT:
   00, 05, 10, 15, 20...
========================================================= */

function scheduleFiveMinuteRefresh(){

    const now =
        new Date();


    const minutes =
        now.getMinutes();


    const seconds =
        now.getSeconds();


    const milliseconds =
        now.getMilliseconds();


    const nextMultiple =
        (
            Math.floor(
                minutes / 5
            ) + 1
        ) * 5;


    let minutesUntil =
        nextMultiple - minutes;


    if(
        minutesUntil <= 0
    ){

        minutesUntil = 5;

    }


    const delay =
        (
            minutesUntil * 60 * 1000
        )
        -
        (
            seconds * 1000
        )
        -
        milliseconds;


    setTimeout(
        async function(){

            if(currentLocation){

                try{

                    await loadWeather();

                }
                catch(error){

                    setStatus(
                        "⚠️ Η αυτόματη ανανέωση απέτυχε προσωρινά.",
                        true
                    );

                }

            }


            scheduleFiveMinuteRefresh();

        },
        Math.max(
            delay,
            1000
        )
    );

}


/* =========================================================
   INITIAL LOAD
========================================================= */

(async function(){

    try{

        const result =
            await findLocation(
                "Θεσσαλονίκη"
            );


        currentLocation =
            result;


        locationName.textContent =
            result.name;


        countryName.textContent =
            countryFlag(
                result.country_code
            ) +
            " " +
            (
                result.country ||
                "Ελλάδα"
            );


        await loadWeather();


        setStatus("");


    }
    catch(error){

        setStatus(
            "❌ Δεν ήταν δυνατή η αρχική φόρτωση.",
            true
        );

    }


    scheduleFiveMinuteRefresh();

})();

</script>

</body>

</html>
