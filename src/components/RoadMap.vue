<script>
    export default {
        name: "RoadMap",

        methods: {
            /*getAppealString(name, surname, index){
                if(name) {
                    if(surname) {
                        this.appeal = name + ' ' + surname;
                        this.getAppealString(this.guests?.name2, this.guests?.surname2, index+1);
                    } else {
                        this.appeal = name;
                        this.getAppealString(this.guests?.name2, this.guests?.surname2, index+1)
                    }
                } else {
                    return this.appeal;
                }
            },*/
            handleScroll: function () {
                const el = document.getElementById("roadmap");
                //const height = document.documentElement.clientHeight;
                if (window.scrollY > 600) {
                    el.setAttribute(
                        'style',
                        'opacity: 1;visibility: visible;'
                    );
                    this.scroll();
                }
                return window.scrollY > 100
            },
            handleScrollElement : function () {
                let id;
                const scrollY = window.scrollY;

                switch (true){
                    case scrollY >= 400 && scrollY <= 500:
                        id = 'event1';
                        break;
                    case scrollY >= 650 && scrollY <= 750:
                        id = 'event2';
                        break;
                    case  scrollY >= 950 && scrollY <= 1150:
                        id = 'event4';
                        break;
                    case  scrollY >= 1150 && scrollY <= 1350:
                        id = 'event5';
                        break;
                    case scrollY >= 1350 && scrollY <= 1450:
                        id = 'event6';
                        break;
                    case scrollY >= 1450 && scrollY <= 1500:
                        id = 'event7';
                        break;
                    case scrollY >= 1500 && scrollY <= 1600:
                        id = 'event8';
                        break;
                    case scrollY >= 1700 && scrollY <= 1800:
                        id = 'event9';
                        break;
                    case scrollY >= 1800 && scrollY <= 1900:
                        id = 'event10';
                        break;
                    case scrollY >= 2000 && scrollY <= 2200:
                        id = 'event11';
                        break;
                    case scrollY >= 2200 && scrollY <= 2300:
                        id = 'event12';
                        break;
                    case scrollY >= 2400 && scrollY <= 2500:
                        id = 'event13';
                        break;
                    case scrollY >= 2600 && scrollY <= 2700:
                        id = 'event14';
                        break;
                    case scrollY >= 2800 && scrollY <= 2900:
                        id = 'event15';
                        break;
                    case  scrollY >= 3000 && scrollY <= 3100:
                        id = 'event16';
                        break;
                    case scrollY >= 3150 && scrollY <= 3220:
                        id = 'event17';
                        break;
                    case scrollY >= 3220 && scrollY <= 3450:
                        id = 'event18';
                        break;
                    case scrollY >= 3450 && scrollY <= 3550:
                        id = 'event19';
                        break;
                    case /* myInterval >= 6 && */ scrollY >= 3750:
                        id = 'event20';
                        break;

                    default:
                        id = 'event1';
                }
                const element = document.getElementById(id);

                if (window.scrollY > 400) {
                    element.setAttribute(
                        'style',
                        'opacity: 1; visibility: visible; transform: translate3d(0, -10px, 0)'
                    )
                }
            },
            scroll() {
                // set height of the svg path as constant
                const svg = document.getElementById("svgPath");
                const length = svg.getTotalLength();

                svg.style.strokeDasharray = length;
                svg.style.strokeDashoffset = length;

                window.addEventListener("scroll", function () {
                    const fixScrollHeight = 5518;
                    const scrollpercent = (document.body.scrollTop + document.documentElement.scrollTop) / (fixScrollHeight - document.documentElement.clientHeight);
                    let draw;
                    const scrollY = window.scrollY;

                    switch (true){
                        case scrollY < 1200:
                            draw = length * (scrollpercent - 0.12);
                            break;
                        case scrollY >= 1200 && scrollY <= 1300:
                            draw = length * (scrollpercent - 0.09);
                            break;
                        case  scrollY >= 1300 && scrollY <= 1400:
                            draw = length * (scrollpercent - 0.06);
                            break;
                        case  scrollY >= 1400 && scrollY <= 1500:
                            draw = length * (scrollpercent - 0.03);
                            break;
                        case scrollY >= 1500 && scrollY <= 1700:
                            draw = length * (scrollpercent);
                            break;
                        case scrollY >= 1700 && scrollY <= 1800:
                            draw = length * (scrollpercent + 0.04);
                            break;
                        case scrollY >= 1800 && scrollY <= 1900:
                            draw = length * (scrollpercent + 0.08);
                            break;
                        case scrollY >= 1900 && scrollY <= 2300:
                            draw = length * (scrollpercent + 0.1);
                            break;
                        case scrollY >= 2300 && scrollY <= 3100:
                            draw = length * (scrollpercent + 0.15);
                            break;
                        case /* myInterval >= 6 && */ scrollY >= 3100:
                            draw = length * (scrollpercent + 0.2);
                            break;

                        default:
                            draw = length * (scrollpercent);
                    }

                    /*if ( scrollY < 1200 ) {
                         draw = length * (scrollpercent - 0.12);
                     } else if (1200 < scrollY < 1800) {
                         draw = length * (scrollpercent);
                     } else if (1800 < scrollY < 2800) {
                         draw = length * (scrollpercent + 1);
                     }*/

                    //draw = length * (scrollpercent);

                    // Reverse the drawing when scroll upwards
                    svg.style.strokeDashoffset = length - draw;
                });
            }
        }
    }
</script>

<template>
    <section class="flex flex-column justify-center align-middle pt-24 relative">
        <v-tooltip   color="rgba(255,255,255, 0.2)" max-width="400" z-index="50" top>
            <template v-slot:activator="{ on, attrs }">
                <div v-bind="attrs" v-on="on" class="z-20 transition-fast" style="opacity: 0; visibility: hidden;" v-scroll="handleScrollElement" id="event1">
                    <p class="text-3xl m-auto text-center font-weight-light italic text-white">1 Сенября 2017г.</p>
                    <p class="text-5xl m-auto text-center font-weight-light text-white">
                        Знакомство — Церковь ⛪️<br>
                        Рэу им. Плеханова
                    </p>
                    <svg class="m-auto" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
                    </svg>
                </div>
            </template>
            <img
                    class=""
                src="https://lh3.googleusercontent.com/pw/ACtC-3f6r6_e0P3wQuMPHWeNwh9QGB_DhlmbiMQy99YmXnuS4ZSKimkLwNFJneRLwjW-2cti0EHIkE9DCQhyRC5BQRbpYtEXm1jyGryJMwJDO5USMcpMn_0Us3bROfrFfRs-UXuP1nufCAxGSsr9JDtMtGUv=w1280-h853-no?authuser=0"
                alt=""
            >
        </v-tooltip>
        <div class="absolute z-20 transition-fast event2" style="opacity: 0;" v-scroll="handleScrollElement" id="event2">
            <div class="relative">
                <p class="text-3xl m-auto text-center font-weight-light italic text-white">5 Ноября 2017.</p>
                <svg class="absolute z-10" style="top: 105px; right: 490px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
                </svg>
            </div>
            <p class="text-5xl text-center font-weight-light text-white">
                Начало отношений —<br>
                Нежка 👩‍❤️‍👨
            </p>
        </div>
        <div class="absolute z-20 transition-fast event4" style="opacity: 0;" v-scroll="handleScrollElement" id="event4">
            <v-tooltip   color="rgba(255,255,255, 0.2)" max-width="400" z-index="50" top>
                <template v-slot:activator="{ on, attrs }">
                    <div v-bind="attrs" v-on="on" class="relative">
                        <p class="text-3xl m-auto text-center font-weight-light italic text-white">1 Января 2018г.</p>
                        <p class="text-5xl text-center font-weight-light text-white">
                            Первый <br>совместный<br>
                            Новый Год —<br>Реутов🎄
                        </p>
                        <svg class="absolute z-10" style="top: 185px;left: 270px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
                        </svg>
                    </div>
                </template>
                <img
                        class=""
                        src="https://lh3.googleusercontent.com/pw/ACtC-3fBeVEs5n6QK64O6IzcIT1NH16PlyU5uCiwej5zazn6a8PRPNixC94vGwGxqNRkvAynXdHx7ipgzxnpQ-1SpDKND5S-JB_tCZEZECFe99RTiaa7TA4cXIyzGf2L_kLh1NBMVj9_5TBURzVtpNXeMvBE=w1280-h960-no?authuser=0"
                        alt=""
                >
            </v-tooltip>
        </div>
        <div class="absolute z-20 transition-fast event5" style="opacity: 0;" v-scroll="handleScrollElement" id="event5">
            <div class="relative">
                <p class="text-3xl m-auto text-center font-weight-light italic text-white">14 Февраля<br>2018г.</p>
                <svg class="absolute z-10" style="top: 50px;left: 300px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
                </svg>
            </div>
            <p class="text-5xl text-center font-weight-light text-white">
                Сюрприз<br>в лифте — ЦДМ🍿
            </p>
        </div>
        <div class="absolute z-20 transition-fast event6" style="opacity: 0;" v-scroll="handleScrollElement" id="event6">
            <v-tooltip  color="rgba(255,255,255, 0.2)" max-width="400" z-index="50" top>
                <template v-slot:activator="{ on, attrs }">
                    <div v-bind="attrs" v-on="on" class="relative">
                        <p class="text-3xl m-auto text-center font-weight-light italic text-white">25 Марта<br>2018г.</p>
                        <svg class="absolute z-10" style="top: 190px;left: -13px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
                        </svg>
                        <p class="text-5xl text-center font-weight-light text-white">
                            Прекрасный Город<br>— Питер 🚂
                        </p>
                    </div>
                </template>
                <img
                        class=""
                        src="https://lh3.googleusercontent.com/pw/ACtC-3fcmB0LV8aEpqIkHA8xRWs7m5ct9Ce0j2sOcPipLIoVG0TV46M7MLaxplXWFuMRTc96ySUQ2z04i5WN6gUdi4cbV0aP1zGBeuWRNuYRqpTFJBshtE5PXsHaIf5SbigT-OHdOm0R_Vd5CTokqUJn7c4=w2352-h1764-no?authuser=0"
                        alt=""
                >
            </v-tooltip>
        </div>
        <div class="absolute z-20 transition-fast event7" style="opacity: 0;" v-scroll="handleScrollElement" id="event7">
            <v-tooltip  color="rgba(255,255,255, 0.2)" max-width="400" z-index="50" top>
                <template v-slot:activator="{ on, attrs }">
                    <div v-bind="attrs" v-on="on" class="relative">
                        <p class="text-3xl m-auto text-center font-weight-light italic text-white">27 Мая<br>2018г.</p>
                        <svg class="absolute z-10" style="top: 40px;right: 355px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
                        </svg>
                        <p class="text-5xl text-center font-weight-light text-white">
                            Конная прогулка —<br>
                            КД Лесное🐎
                        </p>
                    </div>
                </template>
                <img
                        class=""
                        src="https://lh3.googleusercontent.com/pw/ACtC-3e9MweheRMmSB6hzAAHPiS13z6umjmHEWsQZz1ObZkWe0nC-H1S_GZrl8jVq2hjwYS76xIr3MRLLhm_TVJOvsbbOeJG9em9kC6Sl9QuJa8pOhUeHGiLDkGg1aUWbAiZ70elLOL8lEhObO52PF_0ScA=w960-h1280-no?authuser=0"
                        alt=""
                >
            </v-tooltip>
        </div>
        <div class="absolute z-20 transition-fast event8" style="opacity: 0;" v-scroll="handleScrollElement" id="event8">
            <v-tooltip  color="rgba(255,255,255, 0.2)" max-width="400" z-index="50" top>
                <template v-slot:activator="{ on, attrs }">
                    <div v-bind="attrs" v-on="on" class="relative">
                        <p class="text-3xl m-auto text-center font-weight-light italic text-white">Июль<br>2018г.</p>
                        <svg class="absolute z-10" style="top: 45px; left: 420px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
                        </svg>
                        <p class="text-5xl text-center font-weight-light text-white">
                            Студенческая<br>
                            поездка — Анапа 🏖
                        </p>
                    </div>
                </template>
                <img
                        class=""
                        src="https://lh3.googleusercontent.com/pw/ACtC-3e6To7PuHdA-ISjjpGKe0VvaOdjNA3N2DDBZs9oJ3pV-Wu71iiX9qzyyubWKeP8626DTQTt92SqfRZoIDPbbn5yHGqFGbMDaICZL_lgKH8qW15bVCg8ERUrQCVCrYFSivxzmoOhSVmy7EPy4lTAkKM=w1330-h1772-no?authuser=0"
                        alt=""
                >
            </v-tooltip>
        </div>
        <div class="absolute z-20 transition-fast event9" style="opacity: 0;" v-scroll="handleScrollElement" id="event9">
            <v-tooltip  color="rgba(255,255,255, 0.2)" max-width="400" z-index="50" top>
                <template v-slot:activator="{ on, attrs }">
                    <div v-bind="attrs" v-on="on" class="relative">
                        <p class="text-3xl m-auto text-center font-weight-light italic text-white">Август<br>2018г.</p>
                        <svg class="absolute z-10" style="top: 140px; right: 380px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
                        </svg>
                        <p class="text-5xl text-center font-weight-light text-white">
                            Прекрасный<br>
                            Калининград 🏰
                        </p>
                    </div>
                </template>
                <img
                        class=""
                        src="https://lh3.googleusercontent.com/pw/ACtC-3dn1cvK9NY023_Ihjvpjyz9bpUyHXY7pHsSC9VY85cQCf4g_0hf7IQsY1jW4wGsl6Oi8dfELUW0vX3f2HXlE8z3xiMHrveBWJY88Cmdu142KCHxBH9H9kNkXyd8Tv48b2cEAKKU318MHWZTRxkXzlQ=w1330-h1772-no?authuser=0"
                        alt=""
                >
            </v-tooltip>
        </div>
        <div class="absolute z-20 transition-fast event10" style="opacity: 0;" v-scroll="handleScrollElement" id="event10">
            <v-tooltip  color="rgba(255,255,255, 0.2)" max-width="400" z-index="50" top>
                <template v-slot:activator="{ on, attrs }">
                    <div v-bind="attrs" v-on="on" class="relative">
                        <p class="text-3xl m-auto text-center font-weight-light italic text-white">5 Ноября<br>2018г.</p>
                        <svg class="absolute z-10" style="top: 100px;right: -75px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
                        </svg>
                        <p class="text-5xl text-center font-weight-light text-white">
                            Первая годовщина —<br>
                            далеко, но рядом🥂
                        </p>
                    </div>
                 </template>
                <img
                        class=""
                        src="https://lh3.googleusercontent.com/pw/ACtC-3dJBHiqTOJUjVEpOdUCczqcgePSbl-hsDQN8J86gWmYZfoX1svjHwBcCh0l6jh17xMArEFYRl2YuCQRI28BFZbrGWdlF4UrnjwqGz6D35uGUEhdxY5jmrlI3HpN1btK7pJKepihKYDjlDr_gGFQZeA=w2364-h1772-no?authuser=0"
                        alt=""
                >
            </v-tooltip>
        </div>
        <div class="absolute z-20 transition-fast event11" style="opacity: 0;" v-scroll="handleScrollElement" id="event11">
            <v-tooltip  color="rgba(255,255,255, 0.2)" max-width="400" z-index="50" top>
                <template v-slot:activator="{ on, attrs }">
                    <div v-bind="attrs" v-on="on" class="relative">
                        <p class="text-3xl m-auto text-center font-weight-light italic text-white">27 Апреля<br>2019г.</p>
                        <svg class="absolute z-10" style="top: 0; right: 320px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
                        </svg>
                        <p class="text-5xl text-center font-weight-light text-white">
                            Знакомство с мамой<br>
                            невесты — "Карлсон" 🤗
                        </p>
                    </div>
                </template>
                <img
                        class=""
                        src="https://lh3.googleusercontent.com/pw/ACtC-3f9Yc1YtRZfzQ9vLmrqYowhrKhWm13lLYy6oezMGG7-O8RvNmLgYhRhhDRyGjs6i14n5tRKmg12OWU8_s6Da7_Imiu8YvTAVnJ70oN8wimdy5Na2Frj48KV4u0WH0N1rUyjIasNOu3EBo3_oi_3H80z=w1330-h1772-no?authuser=0"
                        alt=""
                >
            </v-tooltip>
        </div>
        <div class="absolute z-20 transition-fast event12" style="opacity: 0;" v-scroll="handleScrollElement" id="event12">
            <v-tooltip  color="rgba(255,255,255, 0.2)" max-width="400" z-index="50" top>
                <template v-slot:activator="{ on, attrs }">
                    <div v-bind="attrs" v-on="on" class="relative">
                        <p class="text-3xl m-auto text-center font-weight-light italic text-white">25 Мая<br>2019г.</p>
                        <svg class="absolute z-10" style="top: 190px;left: 390px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
                        </svg>
                        <p class="text-5xl text-center font-weight-light text-white">
                            Начало совместной<br>
                            жизни — А.Янгеля 🏠
                        </p>
                    </div>
                </template>
                <img
                        class=""
                        src="https://lh3.googleusercontent.com/pw/ACtC-3fqT0E3F9WInZbdo9fakpwV4WszhU9V8BPGLP23a8Ig6ej3OQXPfCUw6zzEG12fqFUP05HALHA5FmKboREpaYQ4NB1usGXuvtKGquT8TEZk7hQvwQDcMvMf8Yn3pCAAeXENyQ6CCLzzfxXYD19cRWM=w960-h721-no?authuser=0"
                        alt=""
                >
            </v-tooltip>
        </div>
        <div class="absolute z-20 transition-fast event13" style="opacity: 0;" v-scroll="handleScrollElement" id="event13">
            <v-tooltip  color="rgba(255,255,255, 0.2)" max-width="400" z-index="50" top>
                <template v-slot:activator="{ on, attrs }">
                    <div v-bind="attrs" v-on="on" class="relative">
                            <p class="text-3xl m-auto text-center font-weight-light italic text-white">29 Декабря<br>2019г.</p>
                            <svg class="absolute z-10" style="top: 35px;left: -95px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
                            </svg>
                        <p class="text-5xl text-center font-weight-light text-white">
                            Совместный отдых<br>
                            во Владивостоке 🌉
                        </p>
                    </div>
                </template>
                <img
                        class=""
                        src="https://lh3.googleusercontent.com/pw/ACtC-3fvwRsUtBtyBTRJaVoJ-DDd4fHQntKy3BY8J5eedoD76l5hom31sq09Rt1u3gHzNowsg8ntTXlVkOZ8eUtwLPFJG3osPjT7tSwU-jR7kc4KsE0Ex7uHtHP1laugP6z_6-JY5FZGgcMfcNr1-ujBuX30=w1324-h1764-no?authuser=0"
                        alt=""
                >
            </v-tooltip>
        </div>
        <div class="absolute z-20 transition-fast event14" style="opacity: 0;" v-scroll="handleScrollElement" id="event14">
            <v-tooltip  color="rgba(255,255,255, 0.2)" max-width="400" z-index="50" top>
                <template v-slot:activator="{ on, attrs }">
                    <div v-bind="attrs" v-on="on" class="relative">
                        <p class="text-3xl m-auto text-center font-weight-light italic text-white">31 Декабря<br>2019г.</p>
                        <svg class="absolute z-10" style="top: -65px;left: 220px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
                        </svg>
                        <p class="text-5xl text-center font-weight-light text-white">
                            Новый Год<br>
                            в кругу семьи невесты<br>
                            — Владивосток 🎄
                        </p>
                    </div>
                </template>
                <img
                        class=""
                        src="https://lh3.googleusercontent.com/pw/ACtC-3feRlZl2lVrSnv67lHaqLGlfQ2kGQO-TY_VcpTO-fbvM_aURQdLPsvNm9L7qjopm8WJ_Qa2Yff9waALfglVXKAzsJAjKIV4M6lBMLJkXtZ1C1kUMbGHJ2Gwj467Ct5qVrNMN6JyQ3s4SekER0SV4cMW=w2352-h1764-no?authuser=0"
                        alt=""
                >
            </v-tooltip>
        </div>
        <div class="absolute z-20 transition-fast event15" style="opacity: 0;" v-scroll="handleScrollElement" id="event15">
            <v-tooltip  color="rgba(255,255,255, 0.2)" max-width="400" z-index="50" top>
                <template v-slot:activator="{ on, attrs }">
                    <div v-bind="attrs" v-on="on" class="relative">
                        <p class="text-3xl m-auto text-center font-weight-light italic text-white">26 мая<br>2020г.</p>
                        <svg class="absolute z-10" style="top: 155px;left: -67px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
                        </svg>
                        <p class="text-5xl text-center font-weight-light text-white">
                            Предложение<br>
                            руки и сердца 💍
                        </p>
                    </div>
                </template>
                <img
                        class=""
                        src="https://lh3.googleusercontent.com/pw/ACtC-3e6pdY12ANedwfuUcMExz4W-gPjg_ER6ALECFxysQdxvfzcWyAiaNQbwhFi8p2H3VPoBX57RnIaDhRbRIV-qoRdnAd35wNqgVH3aDX63AF7kfZD95mkf03wx_8zcVsbc7NWglZpt_ZRHnHMBDAp28M1=w720-h1280-no?authuser=0"
                        alt=""
                >
            </v-tooltip>
        </div>
        <div class="absolute z-20 transition-fast event16" style="opacity: 0;" v-scroll="handleScrollElement" id="event16">
            <v-tooltip  color="rgba(255,255,255, 0.2)" max-width="400" z-index="50" top>
                <template v-slot:activator="{ on, attrs }">
                <div v-bind="attrs" v-on="on" class="relative">
                    <p class="text-3xl m-auto text-center font-weight-light italic text-white">31 Декабря<br>2020г.</p>
                    <svg class="absolute z-10" style="top: 30px;left: -13px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
                    </svg>
                    <p class="text-5xl text-center font-weight-light text-white">
                        Окончание РЭУ<br>
                        им. Плеханова 🧑‍🎓
                    </p>
                </div>
                </template>
                <img
                        class=""
                        src="https://lh3.googleusercontent.com/pw/ACtC-3eSi5v959slKYLj09ypJ8hKal9P4FBMzWi2g_Jv8FbPJNQ2oe_VuGsCORWqo_3qlrmTYfky6WsgY9zSKAS2o-m44tbozsU0-RDgAfiHIhRdzc2MT7wn5WIWw6JTVcqRAsOTkveoRsaAmmqZPuuaQxfS=w1324-h1764-no?authuser=0"
                        alt=""
                >
            </v-tooltip>
        </div>
        <div class="absolute z-20 transition-fast event17" style="opacity: 0;" v-scroll="handleScrollElement" id="event17">
            <div class="relative">
                <p class="text-3xl m-auto text-center font-weight-light italic text-white">23 Сентября<br>2020г.</p>
                <svg class="absolute z-10" style="top: 130px;left: 455px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
                </svg>
            </div>
            <p class="text-5xl text-center font-weight-light text-white">
                Теперь мы коллеги<br>
                — М.Белоруская 👩🏼‍💻
            </p>
        </div>
        <div class="absolute z-20 transition-fast event18" style="opacity: 0;" v-scroll="handleScrollElement" id="event18">
            <v-tooltip  color="rgba(255,255,255, 0.2)" max-width="400" z-index="50" top>
                <template v-slot:activator="{ on, attrs }">
                    <div v-bind="attrs" v-on="on" class="relative">
                        <p class="text-3xl m-auto text-center font-weight-light italic text-white">Ноябрь<br>2020г.</p>
                        <svg class="absolute z-10" style="top: 30px;right: 65px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
                        </svg>
                        <p class="text-5xl text-center font-weight-light text-white">
                            Совместная с мамой жениха<br>
                            зимняя поездка на Кавказ🏔
                        </p>
                    </div>
                </template>
                <img
                        class=""
                        src="https://lh3.googleusercontent.com/pw/ACtC-3dnE10KsJrOuQLCxJE_cKjgq59ar_g2VKLEd4a-Kvp4dEiwnyEuDDbqEdZxMzGVlhCM9cXILKdCADl-CliFlgXMp-O2lHT3rWJku2EKVRBOsNr8CV-K8x9yvdg-9k8agxmn0VODBCRltEz0VkP8D92X=w2352-h1764-no?authuser=0"
                        alt=""
                >
            </v-tooltip>
        </div>
        <div class="absolute z-20 transition-fast event19" style="opacity: 0;" v-scroll="handleScrollElement" id="event19">
            <v-tooltip  color="rgba(255,255,255, 0.2)" max-width="400" z-index="50" top>
                <template v-slot:activator="{ on, attrs }">
                    <div  v-bind="attrs" v-on="on" class="relative">
                        <p class="text-3xl m-auto text-center font-weight-light italic text-white">Март<br>2021г.</p>
                        <svg class="absolute z-10" style="top: 133px;left: -90px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
                        </svg>
                        <p class="text-5xl text-center font-weight-light text-white">
                            День влюблённых<br>в снегу 🏂
                        </p>
                    </div>
                </template>
                <img
                        class=""
                        src="https://lh3.googleusercontent.com/pw/ACtC-3fLuHAcHZtw0Y3EgQio3Kt9BtbXHEnMaSsKE12P0xvvEeFpei36KWiLeARBhLu8uzqIIWgUe5Bh8E68bGoXqTW2cMZVlm8tMTpk01JXs7AujSUDeBVBqB323IrIWpRJ5pxnUiiJuO4bjECSS5c3Tr_H=w2352-h1764-no?authuser=0"
                        alt=""
                >
            </v-tooltip>
        </div>
        <div class="absolute z-20 transition-fast event20" style="opacity: 0;" v-scroll="handleScrollElement" id="event20">
            <p class="text-5xl text-center font-weight-light text-white">
                Крым - последняя точка<br>
                Карты начала нашей любви ❤️
            </p>
            <div class="relative">
                <p class="text-3xl m-auto text-center font-weight-light italic text-white">1 Сентября<br>2021г.</p>
                <svg class="absolute z-10" style="top: -160px;left: 290px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
                </svg>
            </div>
        </div>
        <div v-scroll="handleScroll" class="container flex flex-row justify-center" style="visibility: hidden;" id="roadmap">
            <div style="margin-top: -50px" class="draw-line-height relative">

                <!--<svg width="828" height="2820" viewBox="0 0 828 2820" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M295.007 1L296.98 26.2668C303.917 115.069 245.98 195.993 159.681 218.045L132.959 224.873C67.5707 241.581 21.8245 300.948 21.8245 368.438V368.438C21.8245 418.763 47.6945 465.88 90.3143 492.642V492.642C142.675 525.521 210.052 521.928 258.619 483.669L315.355 438.974C328.748 428.424 343.46 419.667 359.118 412.925L364.362 410.667C439.912 378.137 527.836 398.447 581.464 460.817V460.817L599.787 485.356C653.203 556.894 624.926 659.596 542.42 693.71V693.71C532.617 697.763 522.376 700.663 511.904 702.35L466.215 709.714C462.087 710.379 460.024 710.712 458.039 711.073C408.608 720.066 364.372 747.335 334.129 787.456C332.915 789.066 331.691 790.761 329.242 794.149V794.149L318.876 809.862C298.598 840.603 301.413 881.114 325.748 908.754V908.754L335.811 920.577C347.244 934.008 352.96 940.723 359.203 946.875C367.201 954.755 375.847 961.948 385.052 968.377C392.237 973.396 399.881 977.794 415.169 986.591L499.719 1035.24L647.838 1098.83L698.485 1123.4C712.446 1130.17 719.426 1133.56 725.755 1137.22C775.509 1166.02 810.463 1214.84 821.7 1271.22C823.13 1278.39 824.087 1286.09 826 1301.49V1301.49V1305.31C826 1312.94 826 1316.76 825.876 1320.28C823.294 1393.55 780.828 1459.53 715.209 1492.24C712.057 1493.81 708.583 1495.39 701.636 1498.55V1498.55L640.933 1519.52C615.829 1528.19 603.278 1532.53 590.448 1535.15C574.014 1538.51 557.222 1539.8 540.469 1538.97C527.389 1538.32 514.325 1535.94 488.196 1531.18L385.834 1512.53L325.962 1502.55C304.942 1499.04 294.432 1497.29 284.07 1496.65C252.499 1494.71 220.917 1500.28 191.918 1512.91C182.399 1517.06 173.124 1522.3 154.573 1532.79V1532.79L112.551 1554.18C112.092 1554.42 111.863 1554.53 111.636 1554.65C88.3616 1566.57 67.6512 1582.94 50.6772 1602.83C50.5116 1603.03 50.3451 1603.22 50.0121 1603.62V1603.62C49.1696 1604.61 48.7484 1605.1 48.3525 1605.58C7.11715 1654.76 -8.00606 1720.75 7.69383 1782.99C7.84458 1783.59 8.00766 1784.22 8.33383 1785.48L17.6324 1821.4L50.4702 1907.35L68.477 1960.1C84.3695 2006.65 139.173 2026.65 181.314 2001.28V2001.28C216.177 1980.29 261.348 1989.98 284.536 2023.42L303.391 2050.61L326.411 2075.7C347.061 2098.21 373.056 2115.14 401.99 2124.93L431.389 2134.88C444.086 2139.18 455.337 2146.93 463.882 2157.25V2157.25C476.911 2173 482.659 2193.53 479.7 2213.75L475.964 2239.29L467.475 2271.33C450.004 2337.27 396.31 2387.58 329.42 2400.96V2400.96C309.466 2404.95 290.283 2412.36 272.843 2422.85L235.282 2445.43C198.487 2467.56 178.066 2509.18 183.093 2551.82V2551.82C188.593 2598.47 223.305 2636.38 269.291 2645.96L366.086 2666.12C410.257 2675.32 428.489 2728.43 399.278 2762.82V2762.82C390.148 2773.57 385.136 2787.21 385.136 2801.31V2820" id="svgPath" stroke="#D0B39F" stroke-width="3" stroke-miterlimit="16" stroke-linejoin="bevel" stroke-dasharray="15 15"/>
                    <path d="M295.007 1L296.98 26.2668C303.917 115.069 245.98 195.993 159.681 218.045L132.959 224.873C67.5707 241.581 21.8245 300.948 21.8245 368.438V368.438C21.8245 418.763 47.6945 465.88 90.3143 492.642V492.642C142.675 525.521 210.052 521.928 258.619 483.669L315.355 438.974C328.748 428.424 343.46 419.667 359.118 412.925L364.362 410.667C439.912 378.137 527.836 398.447 581.464 460.817V460.817L599.787 485.356C653.203 556.894 624.926 659.596 542.42 693.71V693.71C532.617 697.763 522.376 700.663 511.904 702.35L466.215 709.714C462.087 710.379 460.024 710.712 458.039 711.073C408.608 720.066 364.372 747.335 334.129 787.456C332.915 789.066 331.691 790.761 329.242 794.149V794.149L318.876 809.862C298.598 840.603 301.413 881.114 325.748 908.754V908.754L335.811 920.577C347.244 934.008 352.96 940.723 359.203 946.875C367.201 954.755 375.847 961.948 385.052 968.377C392.237 973.396 399.881 977.794 415.169 986.591L499.719 1035.24L647.838 1098.83L698.485 1123.4C712.446 1130.17 719.426 1133.56 725.755 1137.22C775.509 1166.02 810.463 1214.84 821.7 1271.22C823.13 1278.39 824.087 1286.09 826 1301.49V1301.49V1305.31C826 1312.94 826 1316.76 825.876 1320.28C823.294 1393.55 780.828 1459.53 715.209 1492.24C712.057 1493.81 708.583 1495.39 701.636 1498.55V1498.55L640.933 1519.52C615.829 1528.19 603.278 1532.53 590.448 1535.15C574.014 1538.51 557.222 1539.8 540.469 1538.97C527.389 1538.32 514.325 1535.94 488.196 1531.18L385.834 1512.53L325.962 1502.55C304.942 1499.04 294.432 1497.29 284.07 1496.65C252.499 1494.71 220.917 1500.28 191.918 1512.91C182.399 1517.06 173.124 1522.3 154.573 1532.79V1532.79L112.551 1554.18C112.092 1554.42 111.863 1554.53 111.636 1554.65C88.3616 1566.57 67.6512 1582.94 50.6772 1602.83C50.5116 1603.03 50.3451 1603.22 50.0121 1603.62V1603.62C49.1696 1604.61 48.7484 1605.1 48.3525 1605.58C7.11715 1654.76 -8.00606 1720.75 7.69383 1782.99C7.84458 1783.59 8.00766 1784.22 8.33383 1785.48L17.6324 1821.4L50.4702 1907.35L68.477 1960.1C84.3695 2006.65 139.173 2026.65 181.314 2001.28V2001.28C216.177 1980.29 261.348 1989.98 284.536 2023.42L303.391 2050.61L326.411 2075.7C347.061 2098.21 373.056 2115.14 401.99 2124.93L431.389 2134.88C444.086 2139.18 455.337 2146.93 463.882 2157.25V2157.25C476.911 2173 482.659 2193.53 479.7 2213.75L475.964 2239.29L467.475 2271.33C450.004 2337.27 396.31 2387.58 329.42 2400.96V2400.96C309.466 2404.95 290.283 2412.36 272.843 2422.85L235.282 2445.43C198.487 2467.56 178.066 2509.18 183.093 2551.82V2551.82C188.593 2598.47 223.305 2636.38 269.291 2645.96L366.086 2666.12C410.257 2675.32 428.489 2728.43 399.278 2762.82V2762.82C390.148 2773.57 385.136 2787.21 385.136 2801.31V2820" class="narmol" stroke="#000" stroke-width="3" stroke-miterlimit="16" stroke-linejoin="bevel" stroke-dasharray="15 15"/>
                </svg>-->
                <svg width="846" height="2849" viewBox="0 0 846 2849" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M434 40.0001V40.0001C472.006 138.377 406.34 246.028 301.476 257.255L160.705 272.328C91.958 279.689 39.8245 337.702 39.8245 406.842V406.842C39.8245 453.385 63.7501 496.66 103.167 521.41L108.314 524.642C160.675 557.521 228.052 553.928 276.619 515.669L333.355 470.974C346.748 460.424 361.46 451.667 377.118 444.925L382.362 442.667C457.912 410.137 545.836 430.447 599.464 492.817V492.817L617.787 517.356C671.203 588.894 642.926 691.597 560.42 725.71V725.71C550.617 729.763 540.376 732.663 529.904 734.351L484.215 741.714C480.087 742.379 478.024 742.712 476.039 743.073C426.608 752.066 382.372 779.335 352.129 819.456C350.915 821.066 349.691 822.761 347.242 826.15V826.15L336.876 841.862C316.598 872.603 319.413 913.114 343.748 940.754V940.754L353.811 952.577C365.244 966.008 370.96 972.724 377.203 978.875C385.201 986.755 393.847 993.948 403.052 1000.38C410.237 1005.4 417.881 1009.79 433.169 1018.59L517.719 1067.24L665.838 1130.83L716.486 1155.4C730.446 1162.17 737.426 1165.56 743.755 1169.22C793.509 1198.02 828.463 1246.84 839.7 1303.22C841.13 1310.39 842.087 1318.09 844 1333.49V1333.49V1337.31C844 1344.94 844 1348.76 843.876 1352.28C841.294 1425.55 798.828 1491.53 733.209 1524.24C730.057 1525.81 726.583 1527.39 719.636 1530.55V1530.55L658.933 1551.52C633.829 1560.19 621.278 1564.53 608.448 1567.15C592.014 1570.51 575.222 1571.8 558.469 1570.97C545.389 1570.32 532.325 1567.94 506.196 1563.18L403.834 1544.53L343.963 1534.55C322.942 1531.04 312.432 1529.29 302.07 1528.65C270.499 1526.71 238.917 1532.28 209.918 1544.91C200.399 1549.06 191.124 1554.3 172.573 1564.79V1564.79L130.551 1586.18C130.092 1586.42 129.863 1586.53 129.636 1586.65C106.362 1598.57 85.6512 1614.94 68.6772 1634.83C68.5116 1635.03 68.3451 1635.22 68.012 1635.62V1635.62C67.1696 1636.61 66.7484 1637.1 66.3525 1637.58C25.1172 1686.76 9.99396 1752.75 25.6939 1814.99C25.8446 1815.59 26.0077 1816.22 26.3339 1817.48L35.6324 1853.4L68.4702 1939.35L86.477 1992.1C102.369 2038.65 157.173 2058.65 199.314 2033.28V2033.28C234.177 2012.29 279.348 2021.98 302.536 2055.42L321.391 2082.61L344.411 2107.7C365.061 2130.21 391.056 2147.14 419.99 2156.93L449.389 2166.88C462.086 2171.18 473.337 2178.93 481.882 2189.25V2189.25C494.911 2205 500.659 2225.53 497.7 2245.75L493.964 2271.29L485.475 2303.33C468.004 2369.27 414.31 2419.58 347.42 2432.96V2432.96C327.466 2436.95 308.283 2444.36 290.843 2454.85L253.282 2477.43C216.487 2499.56 196.066 2541.18 201.093 2583.82L202.293 2594C207.077 2634.57 237.263 2667.54 277.255 2675.87L391.368 2699.63C426.744 2707 436.98 2752.6 408.147 2774.38V2774.38C393.48 2785.46 387.706 2804.78 393.886 2822.09L403.136 2848" class="transition-slow" id="svgPath" stroke="#D0B39F" stroke-width="3" stroke-miterlimit="16" stroke-linejoin="bevel" stroke-dasharray="15 15"/>
                    <path d="M434 40.0001V40.0001C472.006 138.377 406.34 246.028 301.476 257.255L160.705 272.328C91.958 279.689 39.8245 337.702 39.8245 406.842V406.842C39.8245 453.385 63.7501 496.66 103.167 521.41L108.314 524.642C160.675 557.521 228.052 553.928 276.619 515.669L333.355 470.974C346.748 460.424 361.46 451.667 377.118 444.925L382.362 442.667C457.912 410.137 545.836 430.447 599.464 492.817V492.817L617.787 517.356C671.203 588.894 642.926 691.597 560.42 725.71V725.71C550.617 729.763 540.376 732.663 529.904 734.351L484.215 741.714C480.087 742.379 478.024 742.712 476.039 743.073C426.608 752.066 382.372 779.335 352.129 819.456C350.915 821.066 349.691 822.761 347.242 826.15V826.15L336.876 841.862C316.598 872.603 319.413 913.114 343.748 940.754V940.754L353.811 952.577C365.244 966.008 370.96 972.724 377.203 978.875C385.201 986.755 393.847 993.948 403.052 1000.38C410.237 1005.4 417.881 1009.79 433.169 1018.59L517.719 1067.24L665.838 1130.83L716.486 1155.4C730.446 1162.17 737.426 1165.56 743.755 1169.22C793.509 1198.02 828.463 1246.84 839.7 1303.22C841.13 1310.39 842.087 1318.09 844 1333.49V1333.49V1337.31C844 1344.94 844 1348.76 843.876 1352.28C841.294 1425.55 798.828 1491.53 733.209 1524.24C730.057 1525.81 726.583 1527.39 719.636 1530.55V1530.55L658.933 1551.52C633.829 1560.19 621.278 1564.53 608.448 1567.15C592.014 1570.51 575.222 1571.8 558.469 1570.97C545.389 1570.32 532.325 1567.94 506.196 1563.18L403.834 1544.53L343.963 1534.55C322.942 1531.04 312.432 1529.29 302.07 1528.65C270.499 1526.71 238.917 1532.28 209.918 1544.91C200.399 1549.06 191.124 1554.3 172.573 1564.79V1564.79L130.551 1586.18C130.092 1586.42 129.863 1586.53 129.636 1586.65C106.362 1598.57 85.6512 1614.94 68.6772 1634.83C68.5116 1635.03 68.3451 1635.22 68.012 1635.62V1635.62C67.1696 1636.61 66.7484 1637.1 66.3525 1637.58C25.1172 1686.76 9.99396 1752.75 25.6939 1814.99C25.8446 1815.59 26.0077 1816.22 26.3339 1817.48L35.6324 1853.4L68.4702 1939.35L86.477 1992.1C102.369 2038.65 157.173 2058.65 199.314 2033.28V2033.28C234.177 2012.29 279.348 2021.98 302.536 2055.42L321.391 2082.61L344.411 2107.7C365.061 2130.21 391.056 2147.14 419.99 2156.93L449.389 2166.88C462.086 2171.18 473.337 2178.93 481.882 2189.25V2189.25C494.911 2205 500.659 2225.53 497.7 2245.75L493.964 2271.29L485.475 2303.33C468.004 2369.27 414.31 2419.58 347.42 2432.96V2432.96C327.466 2436.95 308.283 2444.36 290.843 2454.85L253.282 2477.43C216.487 2499.56 196.066 2541.18 201.093 2583.82L202.293 2594C207.077 2634.57 237.263 2667.54 277.255 2675.87L391.368 2699.63C426.744 2707 436.98 2752.6 408.147 2774.38V2774.38C393.48 2785.46 387.706 2804.78 393.886 2822.09L403.136 2848" class="transition-slow" stroke="#000" stroke-width="3" stroke-miterlimit="16" stroke-linejoin="bevel" stroke-dasharray="15 15"/>
                </svg>

            </div>
        </div>
    </section>
</template>

<style lang="scss">
    .container {
        min-height: 800px;
        text-align: center;
    }
    .v-tooltip__content.menuable__content__active {
        opacity: 1!important;
    }
    .transition-slow {
        transition: 0.5s;
    }

    .transition-fast {
        transition: 1.5s all cubic-bezier(0.39, 0.575, 0.565, 1);
    }
    .event2 {
        top: 365px;
        right: 260px;
    }
    .event4 {
        top: 450px;
        left: 80px;
    }
    .event5{
        top: 750px;
        left: 160px;
    }
    .event6{
        top: 570px;
        right: 170px;
    }
    .event7 {
        top: 950px;
        right: 260px
    }
    .event8 {
        top: 1050px;
        left: 220px;
    }
    .event9 {
        top: 1210px;
        right: 200px;
    }
    .event10 {
        top: 1500px;
        left: 660px;
    }
    .event11 {
        top: 1800px;
        right: 160px;
    }
    .event12 {
        top: 1650px;
        left: 50px;
    }
    .event13 {
        top: 2000px;
        left: 420px
    }
    .event14 {
        top: 2325px;
        left: 180px;
    }
    .event15 {
        top: 2300px;
        right: 280px;
    }
    .event16 {
        top: 2550px;
        right: 330px;
    }
    .event17 {
        top: 2600px;
        left: 110px;
    }
    .event18 {
        top: 2860px;
        left: -5px;;
    }
    .event19 {
        top: 2890px;
        right: 305px;
    }
    .event20 {
        top: 3180px;
        left: 430px;
    }
</style>
