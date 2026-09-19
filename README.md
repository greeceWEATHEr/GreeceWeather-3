<!DOCTYPE html>
<html lang="el">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Greece Weather</title>

<style>

/* =========================================================
   ΒΑΣΙΚΑ
========================================================= */

*{
    box-sizing:border-box;
}

body{
    margin:0;
    min-height:100vh;
    font-family:Arial,Helvetica,sans-serif;
    color:#fff;

    background:
        linear-gradient(
            180deg,
            #06172f 0%,
            #0a2b50 55%,
            #06172f 100%
        );
}


/* =========================================================
   HEADER
========================================================= */

header{
    text-align:center;
    padding:25px 15px 15px;
}

.logo{
    font-size:30px;
    font-weight:bold;
}

.subtitle{
    margin-top:6px;
    color:#a9c9eb;
    font-size:15px;
}


/* =========================================================
   SEARCH
========================================================= */

.search-area{
    position:relative;
    width:94%;
    max-width:850px;
    margin:18px auto;
}

.search-box{
    display:flex;
    gap:8px;
}

.search-box input{
    flex:1;
    min-width:0;

    padding:15px 17px;

    border:0;
    outline:0;
    border-radius:14px;

    background:#fff;
    color:#14263d;

    font-size:16px;
}

.search-box button{
    padding:0 22px;

    border:0;
    border-radius:14px;

    background:#399cff;
    color:white;

    font-size:16px;
    font-weight:bold;

    cursor:pointer;
}

.search-box button:active{
    transform:scale(.97);
}


/* =========================================================
   SEARCH RESULTS
========================================================= */

.results{
    position:absolute;

    top:62px;
    left:0;
    right:0;

    z-index:100;

    background:#102b4c;

    border-radius:13px;

    overflow:hidden;

    box-shadow:0 10px 30px rgba(0,0,0,.4);
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
    margin-top:4px;
    color:#a9c9eb;
    font-size:13px;
}


/* =========================================================
   ERROR
========================================================= */

.error{
    display:none;

    width:94%;
    max-width:800px;

    margin:18px auto;

    padding:15px;

    border-radius:13px;

    background:#702832;

    text-align:center;
}


/* =========================================================
   ΠΕΡΙΟΧΗ + ΧΩΡΑ + ΣΗΜΑΙΑ
========================================================= */

.location{
    text-align:center;
    margin:25px auto 15px;
}

.location-line{
    display:flex;

    justify-content:center;
    align-items:center;

    gap:9px;

    flex-wrap:wrap;
}

.location h1{
    margin:0;
    font-size:31px;
}

.flag{
    font-size:29px;
    line-height:1;
}

.country{
    margin-top:7px;

    color:#a9c9eb;

    font-size:17px;
}


/* =========================================================
   CURRENT WEATHER
========================================================= */

.current{
    width:94%;
    max-width:900px;

    margin:20px auto;

    padding:24px;

    border-radius:22px;

    text-align:center;

    background:rgba(255,255,255,.08);

    border:1px solid rgba(255,255,255,.06);
}

.current-temp{
    font-size:60px;
    font-weight:bold;
}

.current-condition{
    display:flex;

    justify-content:center;
    align-items:center;

    gap:10px;

    font-size:21px;

    margin-top:4px;
}

.current-details{
    display:flex;

    justify-content:center;

    gap:25px;

    flex-wrap:wrap;

    margin-top:20px;

    color:#c8ddf4;
}

.loading{
    padding:25px;
    color:#a9c9eb;
}


/* =========================================================
   ΕΝΙΑΙΑ WEATHER ICONS
========================================================= */

/*
   Τα εικονίδια δεν είναι πολλά emoji κολλημένα μαζί.
   Είναι ένα ενιαίο SVG icon που δημιουργείται από τον κώδικα.
*/

.weather-icon{
    width:52px;
    height:52px;

    display:inline-flex;

    justify-content:center;
    align-items:center;

    flex-shrink:0;
}

.weather-icon svg{
    width:100%;
    height:100%;

    overflow:visible;
}


/* =========================================================
   FORECAST TITLE
========================================================= */

.forecast-title{
    width:94%;
    max-width:1100px;

    margin:30px auto 15px;

    font-size:22px;
    font-weight:bold;
}


/* =========================================================
   15 ΗΜΕΡΕΣ
   ΑΚΡΙΒΩΣ 6 + 6 + 3
========================================================= */

.forecast{
    width:94%;
    max-width:1100px;

    margin:auto;

    display:grid;

    grid-template-columns:
        repeat(6,minmax(0,1fr));

    gap:12px;
}


/* =========================================================
   DAY CARD
========================================================= */

.day{
    min-width:0;

    padding:15px 8px;

    text-align:center;

    border-radius:17px;

    background:rgba(255,255,255,.08);

    border:1px solid rgba(255,255,255,.07);

    cursor:pointer;

    transition:
        transform .2s,
        background .2s,
        border .2s;
}

.day:hover{
    transform:translateY(-2px);

    background:rgba(255,255,255,.14);
}

.day.selected{
    border:2px solid #55aaff;

    background:rgba(55,150,255,.16);
}

.day-name{
    font-weight:bold;

    font-size:15px;

    white-space:nowrap;

    overflow:hidden;

    text-overflow:ellipsis;
}

.day-date{
    color:#9ebddd;

    font-size:12px;

    margin-top:5px;
}


/* ΕΝΙΑΙΟ ICON ΜΕΣΑ ΣΤΟ ΠΛΑΙΣΙΟ */

.day .weather-icon{
    width:48px;
    height:48px;

    margin:10px auto;
}


/* =========================================================
   ΘΕΡΜΟΚΡΑΣΙΕΣ
   ΜΕΓΙΣΤΗ ΠΑΝΩ
   ΕΛΑΧΙΣΤΗ ΑΚΡΙΒΩΣ ΑΠΟ ΚΑΤΩ
========================================================= */

.temps{
    display:flex;

    flex-direction:column;

    align-items:center;

    justify-content:center;

    line-height:1.35;

    font-size:18px;
}

.max{
    display:block;

    font-weight:bold;
}

.min{
    display:block;

    margin-top:1px;

    color:#a9c9eb;
}


/* =========================================================
   ΥΕΤΟΣ
========================================================= */

.precip{
    display:flex;

    align-items:center;

    justify-content:center;

    gap:5px;

    margin-top:10px;

    color:#c4ddf4;

    font-size:13px;
}

.precip-icon{
    width:19px;
    height:19px;

    display:inline-flex;
}

.precip-icon svg{
    width:100%;
    height:100%;
}


/* =========================================================
   WIND
========================================================= */

.wind{
    margin-top:7px;

    color:#c4ddf4;

    font-size:13px;
}


/* =========================================================
   SELECTED DAY DETAILS
========================================================= */

.details{
    display:none;

    width:94%;
    max-width:1100px;

    margin:25px auto 40px;

    padding:20px;

    border-radius:20px;

    background:rgba(255,255,255,.08);
}

.details h2{
    margin-top:0;

    text-transform:capitalize;
}

.hourly{
    display:grid;

    grid-template-columns:
        repeat(auto-fit,minmax(105px,1fr));

    gap:9px;
}

.hour{
    padding:12px 6px;

    text-align:center;

    border-radius:13px;

    background:rgba(0,0,0,.16);
}

.hour-time{
    color:#a9c9eb;

    font-size:13px;
}

.hour .weather-icon{
    width:36px;
    height:36px;

    margin:7px auto;
}

.hour-temp{
    font-size:17px;
    font-weight:bold;
}

.hour-wind{
    margin-top:6px;

    color:#c4d9ef;

    font-size:12px;
}


/* =========================================================
   TABLET
========================================================= */

@media(max-width:900px){

    .forecast{
        grid-template-columns:
            repeat(3,minmax(0,1fr));
    }

}


/* =========================================================
   ΚΙΝΗΤΟ
========================================================= */

@media(max-width:600px){

    .forecast{
        grid-template-columns:
            repeat(2,minmax(0,1fr));

        gap:8px;
    }

    .day{
        padding:13px 6px;
    }

    .current-temp{
        font-size:50px;
    }

    .search-box button{
        padding:0 15px;
    }

}


/* =========================================================
   ΠΟΛΥ ΜΙΚΡΗ ΟΘΟΝΗ
========================================================= */

@media(max-width:380px){

    .logo{
        font-size:25px;
    }

    .location h1{
        font-size:26px;
    }

}

</style>
</head>


<body>


<!-- =====================================================
     HEADER
===================================================== -->

<header>

    <div class="logo">
        🌦️ Greece Weather
    </div>

    <div class="subtitle">
        15ήμερη πρόγνωση με ECMWF + GFS
    </div>

</header>


<!-- =====================================================
     SEARCH
===================================================== -->

<div class="search-area">

    <div class="search-box">

        <input
            id="searchInput"
            type="text"
            placeholder="Αναζήτησε οποιαδήποτε περιοχή στον κόσμο..."
            autocomplete="off"
        >

        <button onclick="searchLocation()">
            Αναζήτηση
        </button>

    </div>

    <div
        id="results"
        class="results"
    ></div>

</div>


<div
    id="error"
    class="error"
></div>


<!-- =====================================================
     LOCATION
===================================================== -->

<div class="location">

    <div class="location-line">

        <h1 id="placeName">
            Θεσσαλονίκη
        </h1>

        <span
            id="flag"
            class="flag"
        >
            🇬🇷
        </span>

    </div>

    <div
        id="countryName"
        class="country"
    >
        Ελλάδα
    </div>

</div>


<!-- =====================================================
     CURRENT
===================================================== -->

<div
    id="current"
    class="current"
>

    <div class="loading">
        Φόρτωση δεδομένων...
    </div>

</div>


<!-- =====================================================
     15 DAYS
===================================================== -->

<div class="forecast-title">
    15ήμερη πρόγνωση
</div>

<div
    id="forecast"
    class="forecast"
></div>


<!-- =====================================================
     SELECTED DAY
===================================================== -->

<div
    id="details"
    class="details"
></div>


<script>

/* =========================================================
   ΑΡΧΙΚΗ ΠΕΡΙΟΧΗ
========================================================= */

let currentLocation = {

    name:"Θεσσαλονίκη",

    country:"Ελλάδα",

    countryCode:"GR",

    latitude:40.6401,

    longitude:22.9444

};

let forecastData = null;


/* =========================================================
   COUNTRY FLAG
========================================================= */

function countryFlag(code){

    if(!code)
        return "🌍";

    code =
        String(code)
        .trim()
        .toUpperCase();

    if(code.length !== 2)
        return "🌍";

    return String.fromCodePoint(
        ...[...code].map(
            char =>
                127397 +
                char.charCodeAt(0)
        )
    );

}


/* =========================================================
   ΕΝΙΑΙΑ SVG WEATHER ICONS
========================================================= */

function weatherSVG(code,isDay=true){

    const sun = `
        <circle
            cx="28"
            cy="28"
            r="10"
            fill="#FFD84D"
        />

        <g
            stroke="#FFD84D"
            stroke-width="3"
            stroke-linecap="round"
        >

            <line x1="28" y1="5" x2="28" y2="11"/>
            <line x1="28" y1="45" x2="28" y2="51"/>

            <line x1="5" y1="28" x2="11" y2="28"/>
            <line x1="45" y1="28" x2="51" y2="28"/>

            <line x1="12" y1="12" x2="16" y2="16"/>
            <line x1="40" y1="40" x2="44" y2="44"/>

            <line x1="40" y1="16" x2="44" y2="12"/>
            <line x1="12" y1="44" x2="16" y2="40"/>

        </g>
    `;


    const moon = `
        <path
            d="
                M39 8
                C25 10 17 20 18 32
                C19 44 29 51 40 49
                C46 48 51 44 54 39
                C48 42 42 42 37 39
                C27 34 25 23 30 15
                C32 12 35 10 39 8
                Z
            "
            fill="#DDE7F2"
        />
    `;


    const cloud = `
        <path
            d="
                M15 42
                C9 42 6 38 6 33
                C6 28 10 24 15 24
                C16 17 22 13 29 13
                C37 13 43 18 44 25
                C50 25 54 29 54 35
                C54 40 50 43 45 43
                Z
            "
            fill="#B9C8D8"
        />
    `;


    const darkCloud = `
        <path
            d="
                M14 43
                C8 43 5 39 5 34
                C5 29 9 25 14 25
                C15 18 21 14 28 14
                C36 14 42 19 43 26
                C49 26 54 30 54 36
                C54 41 50 44 44 44
                Z
            "
            fill="#8999AA"
        />
    `;


    const rain = `
        <g
            stroke="#55B9FF"
            stroke-width="4"
            stroke-linecap="round"
        >
            <line x1="18" y1="43" x2="14" y2="51"/>
            <line x1="29" y1="43" x2="25" y2="51"/>
            <line x1="40" y1="43" x2="36" y2="51"/>
        </g>
    `;


    const snow = `
        <g
            stroke="#E8F6FF"
            stroke-width="2.5"
            stroke-linecap="round"
        >

            <line x1="16" y1="47" x2="20" y2="47"/>
            <line x1="18" y1="45" x2="18" y2="49"/>
            <line x1="16.5" y1="45.5" x2="19.5" y2="48.5"/>
            <line x1="19.5" y1="45.5" x2="16.5" y2="48.5"/>

            <line x1="27" y1="48" x2="31" y2="48"/>
            <line x1="29" y1="46" x2="29" y2="50"/>
            <line x1="27.5" y1="46.5" x2="30.5" y2="49.5"/>
            <line x1="30.5" y1="46.5" x2="27.5" y2="49.5"/>

            <line x1="38" y1="46" x2="42" y2="46"/>
            <line x1="40" y1="44" x2="40" y2="48"/>
            <line x1="38.5" y1="44.5" x2="41.5" y2="47.5"/>
            <line x1="41.5" y1="44.5" x2="38.5" y2="47.5"/>

        </g>
    `;


    const thunder = `
        <polygon
            points="30,37 23,37 31,24 28,24 39,8 35,23 42,23"
            fill="#FFD84D"
        />
    `;


    /* =====================================================
       ΗΜΕΡΑ
    ===================================================== */

    if(isDay){

        if(code === 0){

            return `
                <svg viewBox="0 0 60 60">
                    ${sun}
                </svg>
            `;

        }


        if(code === 1){

            return `
                <svg viewBox="0 0 60 60">

                    <g transform="translate(-7,-7) scale(.72)">
                        ${sun}
                    </g>

                    ${cloud}

                </svg>
            `;

        }


        if(code === 2){

            return `
                <svg viewBox="0 0 60 60">

                    <g transform="translate(-8,-8) scale(.65)">
                        ${sun}
                    </g>

                    ${cloud}

                </svg>
            `;

        }


        if(code === 3){

            return `
                <svg viewBox="0 0 60 60">
                    ${darkCloud}
                </svg>
            `;

        }


        if(code === 45 || code === 48){

            return `
                <svg viewBox="0 0 60 60">

                    <path
                        d="M10 28H50M8 36H52M12 44H48"
                        stroke="#B7C4D0"
                        stroke-width="5"
                        stroke-linecap="round"
                    />

                </svg>
            `;

        }


        if(code >= 51 && code <= 67){

            return `
                <svg viewBox="0 0 60 60">
                    ${cloud}
                    ${rain}
                </svg>
            `;

        }


        if(code >= 71 && code <= 77){

            return `
                <svg viewBox="0 0 60 60">
                    ${cloud}
                    ${snow}
                </svg>
            `;

        }


        if(code >= 80 && code <= 82){

            return `
                <svg viewBox="0 0 60 60">
                    ${darkCloud}
                    ${rain}
                </svg>
            `;

        }


        if(code >= 85 && code <= 86){

            return `
                <svg viewBox="0 0 60 60">
                    ${darkCloud}
                    ${snow}
                </svg>
            `;

        }


        if(code >= 95){

            return `
                <svg viewBox="0 0 60 60">
                    ${darkCloud}
                    ${thunder}
                    ${rain}
                </svg>
            `;

        }

    }


    /* =====================================================
       ΝΥΧΤΑ
    ===================================================== */

    /*
       0  = Σκέτο φεγγάρι
       1  = Φεγγάρι + λίγα σύννεφα
       2  = Φεγγάρι + πολλά σύννεφα
       3  = Πλήρης συννεφιά σκέτη
       51-67 = Φεγγάρι + σύννεφα + βροχή
       71-77 = Φεγγάρι + σύννεφα + χιόνι
       80-82 = Φεγγάρι + σύννεφα + βροχή
       85-86 = Φεγγάρι + σύννεφα + χιόνι
       95+ = Φεγγάρι + σύννεφα + καταιγίδα
    */


    if(code === 0){

        return `
            <svg viewBox="0 0 60 60">
                ${moon}
            </svg>
        `;

    }


    if(code === 1){

        return `
            <svg viewBox="0 0 60 60">

                <g transform="translate(-4,-5) scale(.78)">
                    ${moon}
                </g>

                <g transform="translate(4,7) scale(.62)">
                    ${cloud}
                </g>

            </svg>
        `;

    }


    if(code === 2){

        return `
            <svg viewBox="0 0 60 60">

                <g transform="translate(-7,-6) scale(.72)">
                    ${moon}
                </g>

                <g transform="translate(4,5) scale(.72)">
                    ${darkCloud}
                </g>

            </svg>
        `;

    }


    if(code === 3){

        return `
            <svg viewBox="0 0 60 60">
                ${darkCloud}
            </svg>
        `;

    }


    if(code === 45 || code === 48){

        return `
            <svg viewBox="0 0 60 60">

                <path
                    d="M10 28H50M8 36H52M12 44H48"
                    stroke="#B7C4D0"
                    stroke-width="5"
                    stroke-linecap="round"
                />

            </svg>
        `;

    }


    /* ΦΕΓΓΑΡΙ + ΣΥΝΝΕΦΑ + ΒΡΟΧΗ */

    if(
        (code >= 51 && code <= 67) ||
        (code >= 80 && code <= 82)
    ){

        return `
            <svg viewBox="0 0 60 60">

                <g transform="translate(-8,-7) scale(.67)">
                    ${moon}
                </g>

                ${darkCloud}

                ${rain}

            </svg>
        `;

    }


    /* ΦΕΓΓΑΡΙ + ΣΥΝΝΕΦΑ + ΧΙΟΝΙ */

    if(
        (code >= 71 && code <= 77) ||
        (code >= 85 && code <= 86)
    ){

        return `
            <svg viewBox="0 0 60 60">

                <g transform="translate(-8,-7) scale(.67)">
                    ${moon}
                </g>

                ${darkCloud}

                ${snow}

            </svg>
        `;

    }


    /* ΦΕΓΓΑΡΙ + ΣΥΝΝΕΦΑ + ΚΑΤΑΙΓΙΔΑ */

    if(code >= 95){

        return `
            <svg viewBox="0 0 60 60">

                <g transform="translate(-8,-7) scale(.67)">
                    ${moon}
                </g>

                ${darkCloud}

                ${thunder}

                ${rain}

            </svg>
        `;

    }


    return `
        <svg viewBox="0 0 60 60">
            ${moon}
        </svg>
    `;

}


/* =========================================================
   WEATHER ICON ELEMENT
========================================================= */

function weatherIconElement(code,isDay=true){

    const wrapper =
        document.createElement("span");

    wrapper.className =
        "weather-icon";

    wrapper.innerHTML =
        weatherSVG(code,isDay);

    return wrapper;

}


/* =========================================================
   PRECIPITATION ICON
   ΕΝΑ ΕΝΙΑΙΟ ΕΙΚΟΝΙΔΙΟ
========================================================= */

function precipitationSVG(code){

    if(code >= 95){

        return `
            <svg viewBox="0 0 30 30">

                <polygon
                    points="15,2 10,15 15,15 11,28 22,12 17,12 21,2"
                    fill="#FFD84D"
                />

            </svg>
        `;

    }


    if(code >= 71 && code <= 86){

        return `
            <svg viewBox="0 0 30 30">

                <circle
                    cx="15"
                    cy="14"
                    r="7"
                    fill="#B8C9D8"
                />

                <g
                    stroke="#EAF7FF"
                    stroke-width="2"
                    stroke-linecap="round"
                >

                    <line x1="9" y1="23" x2="12" y2="23"/>
                    <line x1="10.5" y1="21.5" x2="10.5" y2="24.5"/>

                    <line x1="17" y1="23" x2="20" y2="23"/>
                    <line x1="18.5" y1="21.5" x2="18.5" y2="24.5"/>

                </g>

            </svg>
        `;

    }


    return `
        <svg viewBox="0 0 30 30">

            <path
                d="M7 18C7 13 10 10 14 10C15 6 18 4 22 4C27 4 29 8 29 12C32 12 34 15 34 19C34 23 31 25 27 25H10C6 25 4 22 4 19C4 18 5 18 7 18Z"
                fill="#9CB5CC"
                transform="translate(-4,0)"
            />

            <g
                stroke="#55B9FF"
                stroke-width="2.5"
                stroke-linecap="round"
            >

                <line x1="10" y1="22" x2="8" y2="28"/>
                <line x1="16" y1="22" x2="14" y2="28"/>
                <line x1="22" y1="22" x2="20" y2="28"/>

            </g>

        </svg>
    `;

}


/* =========================================================
   WIND DIRECTION
========================================================= */

function windDirection(degrees){

    if(degrees == null)
        return "";

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
   WEATHER TEXT
========================================================= */

function weatherText(code){

    if(code === 0)
        return "Αίθριος";

    if(code === 1)
        return "Κυρίως αίθριος";

    if(code === 2)
        return "Λίγες νεφώσεις";

    if(code === 3)
        return "Πλήρης συννεφιά";

    if(code === 45 || code === 48)
        return "Ομίχλη";

    if(code >= 51 && code <= 57)
        return "Ψιλόβροχο";

    if(code >= 61 && code <= 67)
        return "Βροχή";

    if(code >= 71 && code <= 77)
        return "Χιόνι";

    if(code >= 80 && code <= 82)
        return "Μπόρες";

    if(code >= 85 && code <= 86)
        return "Χιονομπόρες";

    if(code >= 95)
        return "Καταιγίδα";

    return "Άγνωστο";

}


/* =========================================================
   SEARCH WORLDWIDE
========================================================= */

async function searchLocation(){

    const input =
        document
        .getElementById("searchInput")
        .value
        .trim();


    if(!input)
        return;


    const results =
        document.getElementById("results");


    hideError();


    results.innerHTML =
        '<div class="result">🔎 Αναζήτηση...</div>';


    try{

        const url =
            "https://geocoding-api.open-meteo.com/v1/search" +

            "?name=" +
            encodeURIComponent(input) +

            "&count=8" +

            "&language=el" +

            "&format=json";


        const response =
            await fetch(url);


        if(!response.ok)
            throw new Error();


        const data =
            await response.json();


        results.innerHTML = "";


        if(
            !data.results ||
            data.results.length === 0
        ){

            showError(
                "Δεν βρέθηκε πραγματική περιοχή με αυτό το όνομα."
            );

            return;

        }


        data.results.forEach(place => {

            const div =
                document.createElement("div");


            div.className =
                "result";


            const flag =
                countryFlag(
                    place.country_code
                );


            div.innerHTML = `

                <div class="result-name">

                    ${escapeHTML(place.name)}
                    ${flag}

                </div>

                <div class="result-country">

                    ${escapeHTML(
                        place.country || ""
                    )}

                    ${
                        place.admin1
                        ?
                        " • " +
                        escapeHTML(place.admin1)
                        :
                        ""
                    }

                </div>

            `;


            div.onclick = () => {

                results.innerHTML = "";


                loadWeather({

                    name:
                        place.name,

                    country:
                        place.country || "",

                    countryCode:
                        place.country_code || "",

                    latitude:
                        place.latitude,

                    longitude:
                        place.longitude

                });

            };


            results.appendChild(div);

        });


    }catch(error){

        showError(
            "Η αναζήτηση απέτυχε. Έλεγξε τη σύνδεσή σου."
        );

    }

}


/* =========================================================
   LOAD WEATHER
========================================================= */

async function loadWeather(location){

    hideError();


    currentLocation =
        location;


    document
        .getElementById("placeName")
        .textContent =
        location.name;


    document
        .getElementById("countryName")
        .textContent =
        location.country;


    document
        .getElementById("flag")
        .textContent =
        countryFlag(
            location.countryCode
        );


    document
        .getElementById("current")
        .innerHTML =
        '<div class="loading">🌐 Φόρτωση πραγματικών δεδομένων...</div>';


    document
        .getElementById("forecast")
        .innerHTML =
        '<div class="loading">📅 Φόρτωση 15ήμερου...</div>';


    document
        .getElementById("details")
        .style.display =
        "none";


    try{

        /* =================================================
           ECMWF
        ================================================= */

        const ecmwfURL =

            "https://api.open-meteo.com/v1/forecast" +

            "?latitude=" +
            location.latitude +

            "&longitude=" +
            location.longitude +

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


        /* =================================================
           GFS
        ================================================= */

        const gfsURL =

            "https://api.open-meteo.com/v1/gfs" +

            "?latitude=" +
            location.latitude +

            "&longitude=" +
            location.longitude +

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


        const responses =
            await Promise.all([

                fetch(ecmwfURL),

                fetch(gfsURL)

            ]);


        if(
            !responses[0].ok ||
            !responses[1].ok
        ){

            throw new Error();

        }


        const ecmwf =
            await responses[0].json();


        const gfs =
            await responses[1].json();


        forecastData =
            combineModels(
                ecmwf,
                gfs
            );


        renderCurrent(
            forecastData
        );


        renderForecast(
            forecastData
        );


    }catch(error){

        console.error(error);


        document
            .getElementById("current")
            .innerHTML =
            '<div class="loading">❌ Δεν ήταν δυνατή η φόρτωση των δεδομένων.</div>';


        showError(
            "Δεν ήταν δυνατή η φόρτωση των καιρικών δεδομένων."
        );

    }

}


/* =========================================================
   AVERAGE
========================================================= */

function average(a,b){

    if(
        a == null &&
        b == null
    )
        return null;


    if(a == null)
        return b;


    if(b == null)
        return a;


    return (a+b)/2;

}


/* =========================================================
   COMBINE MODELS
========================================================= */

function combineModels(ecmwf,gfs){

    const daily = [];


    const days =
        Math.min(

            ecmwf.daily.time.length,

            gfs.daily.time.length,

            15

        );


    for(
        let i=0;
        i<days;
        i++
    ){

        const max =
            average(

                ecmwf
                .daily
                .temperature_2m_max[i],

                gfs
                .daily
                .temperature_2m_max[i]

            );


        const min =
            average(

                ecmwf
                .daily
                .temperature_2m_min[i],

                gfs
                .daily
                .temperature_2m_min[i]

            );


        const precip =
            Math.round(

                average(

                    ecmwf
                    .daily
                    .precipitation_probability_max[i],

                    gfs
                    .daily
                    .precipitation_probability_max[i]

                )

            );


        const code =
            ecmwf
            .daily
            .weather_code[i]
            ??
            gfs
            .daily
            .weather_code[i];


        const wind =
            average(

                ecmwf
                .daily
                .wind_speed_10m_max[i],

                gfs
                .daily
                .wind_speed_10m_max[i]

            );


        const windDir =
            ecmwf
            .daily
            .wind_direction_10m_dominant[i]
            ??
            gfs
            .daily
            .wind_direction_10m_dominant[i];


        daily.push({

            date:
                ecmwf
                .daily
                .time[i],

            max:
                Math.round(max),

            min:
                Math.round(min),

            precip:
                precip,

            code:
                code,

            wind:
                Math.round(wind),

            windDir:
                windDirection(windDir)

        });

    }


    /* =================================================
       HOURLY
    ================================================= */

    const hourly = [];


    const hours =
        Math.min(

            ecmwf.hourly.time.length,

            gfs.hourly.time.length

        );


    for(
        let i=0;
        i<hours;
        i++
    ){

        hourly.push({

            time:
                ecmwf
                .hourly
                .time[i],


            temp:
                average(

                    ecmwf
                    .hourly
                    .temperature_2m[i],

                    gfs
                    .hourly
                    .temperature_2m[i]

                ),


            precip:
                Math.round(

                    average(

                        ecmwf
                        .hourly
                        .precipitation_probability[i],

                        gfs
                        .hourly
                        .precipitation_probability[i]

                    )

                ),


            code:
                ecmwf
                .hourly
                .weather_code[i]
                ??
                gfs
                .hourly
                .weather_code[i],


            wind:
                average(

                    ecmwf
                    .hourly
                    .wind_speed_10m[i],

                    gfs
                    .hourly
                    .wind_speed_10m[i]

                ),


            windDir:
                windDirection(

                    ecmwf
                    .hourly
                    .wind_direction_10m[i]
                    ??
                    gfs
                    .hourly
                    .wind_direction_10m[i]

                ),


            isDay:
                ecmwf
                .hourly
                .is_day[i]

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

                new Date(hour.time)
                -
                now

            );


        if(diff < bestDiff){

            bestDiff =
                diff;

            nearest =
                hour;

        }

    });


    const currentIcon =
        weatherSVG(
            nearest.code,
            nearest.isDay
        );


    document
        .getElementById("current")
        .innerHTML = `

        <div class="current-temp">

            ${Math.round(
                nearest.temp
            )}°

        </div>

        <div class="current-condition">

            <span class="weather-icon">
                ${currentIcon}
            </span>

            ${weatherText(
                nearest.code
            )}

        </div>

        <div class="current-details">

            <span>
                💧 Υετός:
                ${nearest.precip}%
            </span>

            <span>
                💨 Άνεμος:
                ${Math.round(
                    nearest.wind
                )}
                km/h
                ${nearest.windDir}
            </span>

        </div>

    `;

}


/* =========================================================
   15 ΗΜΕΡΕΣ
========================================================= */

function renderForecast(data){

    const container =
        document
        .getElementById("forecast");


    container.innerHTML = "";


    data.daily.forEach(
        (day,index) => {


        const date =
            new Date(
                day.date +
                "T12:00:00"
            );


        const dayName =
            date.toLocaleDateString(

                "el-GR",

                {
                    weekday:"long"
                }

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
        =====================================================
        ΕΜΦΑΝΙΣΗ ΥΕΤΟΥ

        <30%:
        μόνο ποσοστό

        >=30%:
        ενιαίο εικονίδιο βροχής/χιονιού/καταιγίδας
        =====================================================
        */

        let precipitationHTML =
            `${day.precip}%`;


        if(day.precip >= 30){

            precipitationHTML = `

                <span class="precip-icon">

                    ${precipitationSVG(
                        day.code
                    )}

                </span>

                ${day.precip}%

            `;

        }


        const div =
            document
            .createElement("div");


        div.className =
            "day";


        /*
        =====================================================
        ΓΙΑ ΤΗΝ ΗΜΕΡΗΣΙΑ ΚΑΡΤΑ:
        Χρησιμοποιούμε το ημερήσιο weather code.
        =====================================================
        */

        const iconHTML =
            weatherSVG(
                day.code,
                true
            );


        div.innerHTML = `

            <div class="day-name">
                ${dayName}
            </div>

            <div class="day-date">
                ${dateText}
            </div>

            <span class="weather-icon">
                ${iconHTML}
            </span>

            <div class="temps">

                <span class="max">
                    ${day.max}°
                </span>

                <span class="min">
                    ${day.min}°
                </span>

            </div>

            <div class="precip">

                ${precipitationHTML}

            </div>

            <div class="wind">

                💨
                ${day.wind}
                km/h
                ${day.windDir}

            </div>

        `;


        div.onclick =
            () => {

                document
                    .querySelectorAll(".day")
                    .forEach(card => {

                        card.classList.remove(
                            "selected"
                        );

                    });


                div.classList.add(
                    "selected"
                );


                showDayDetails(
                    index
                );

            };


        container.appendChild(
            div
        );

    });

}


/* =========================================================
   SELECTED DAY / HOURLY
========================================================= */

function showDayDetails(dayIndex){

    const day =
        forecastData
        .daily[dayIndex];


    const details =
        document
        .getElementById("details");


    const hours =
        forecastData
        .hourly
        .filter(
            hour =>
                hour.time.startsWith(
                    day.date
                )
        );


    let html = `

        <h2>

            ${new Date(
                day.date +
                "T12:00:00"
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
            hour.time.substring(
                11,
                16
            );


        /*
        =====================================================
        ΩΡΙΑΙΟΣ ΥΕΤΟΣ

        ΜΟΝΟ >=30%
        =====================================================
        */

        let precipHTML =
            `${hour.precip}%`;


        if(hour.precip >= 30){

            precipHTML = `

                <span class="precip-icon">

                    ${precipitationSVG(
                        hour.code
                    )}

                </span>

                ${hour.precip}%

            `;

        }


        html += `

            <div class="hour">

                <div class="hour-time">
                    ${time}
                </div>

                <span class="weather-icon">

                    ${weatherSVG(
                        hour.code,
                        hour.isDay
                    )}

                </span>

                <div class="hour-temp">

                    ${Math.round(
                        hour.temp
                    )}°

                </div>

                <div class="precip">

                    ${precipHTML}

                </div>

                <div class="hour-wind">

                    💨
                    ${Math.round(
                        hour.wind
                    )}
                    km/h
                    ${hour.windDir}

                </div>

            </div>

        `;

    });


    html += `
        </div>
    `;


    details.innerHTML =
        html;


    details.style.display =
        "block";


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
        document
        .getElementById("error");


    error.textContent =
        message;


    error.style.display =
        "block";

}


function hideError(){

    document
        .getElementById("error")
        .style.display =
        "none";

}


/* =========================================================
   HTML ESCAPE
========================================================= */

function escapeHTML(text){

    return String(text)

        .replaceAll(
            "&",
            "&amp;"
        )

        .replaceAll(
            "<",
            "&lt;"
        )

        .replaceAll(
            ">",
            "&gt;"
        )

        .replaceAll(
            '"',
            "&quot;"
        )

        .replaceAll(
            "'",
            "&#039;"
        );

}


/* =========================================================
   ENTER = SEARCH
========================================================= */

document
    .getElementById("searchInput")
    .addEventListener(
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
   AUTO REFRESH
========================================================= */

setInterval(

    () => {

        loadWeather(
            currentLocation
        );

    },

    2 * 60 * 60 * 1000

);


/* =========================================================
   START
========================================================= */

loadWeather(
    currentLocation
);

</script>

</body>
</html>
