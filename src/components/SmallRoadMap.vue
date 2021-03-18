<script>
    export default {
        name: "SmallRoadMap",

        data () {
            return {
                heightLine: 2000
            }
        },

        mounted() {
            this.scrollingMap();
        },


        methods: {
            handleScrollElement : function () {
                let id;
                const scrollY = window.scrollY;

                switch (true){
                    case scrollY >= 500 && scrollY <= 650:
                        id = 'mobile-event1';
                        break;
                    case scrollY >= 750 && scrollY <= 950:
                        id = 'mobile-event2';
                        break;
                    case  scrollY >= 950 && scrollY <= 1150:
                        id = 'mobile-event4';
                        break;
                    case  scrollY >= 1150 && scrollY <= 1350:
                        id = 'mobile-event5';
                        break;
                    case scrollY >= 1350 && scrollY <= 1450:
                        id = 'mobile-event6';
                        break;
                    case scrollY >= 1550 && scrollY <= 1650:
                        id = 'mobile-event7';
                        break;
                    case scrollY >= 1850 && scrollY <= 1950:
                        id = 'mobile-event8';
                        break;
                    case scrollY >= 1950 && scrollY <= 2000:
                        id = 'mobile-event9';
                        break;
                    case scrollY >= 2100 && scrollY <= 2300:
                        id = 'mobile-event10';
                        break;
                    case scrollY >= 2400 && scrollY <= 2500:
                        id = 'mobile-event11';
                        break;
                    case scrollY >= 2600 && scrollY <= 2750:
                        id = 'mobile-event12';
                        break;
                    case scrollY >= 2800 && scrollY <= 3000:
                        id = 'mobile-event13';
                        break;
                    case scrollY >= 3000 && scrollY <= 3100:
                        id = 'mobile-event14';
                        break;
                    case scrollY >= 3250 && scrollY <= 3350:
                        id = 'mobile-event15';
                        break;
                    case  scrollY >= 3550 && scrollY <= 3700:
                        id = 'mobile-event16';
                        break;
                    case scrollY >= 3700 && scrollY <= 3920:
                        id = 'mobile-event17';
                        break;
                    case scrollY >= 3920 && scrollY <= 4150:
                        id = 'mobile-event18';
                        break;
                    case scrollY >= 4150 && scrollY <= 4350:
                        id = 'mobile-event19';
                        break;
                    case /* myInterval >= 6 && */ scrollY >= 4350:
                        id = 'mobile-event20';
                        break;

                    default:
                        id = 'mobile-event1';
                }
                const element = document.getElementById(id);

                if (window.scrollY > 400) {
                    element.setAttribute(
                        'style',
                        'opacity: 1; transform: translate3d(0, -10px, 0)'
                    )
                }
            },
            scrollingMap () {
                const elementDraw = document.getElementById('roadmap-text');
                this.heightLine = elementDraw.clientHeight;
                console.log(this.heightLine);
                    // Get a reference to the <path>
                    var path = document.querySelector('#line-path');

                    // Get length of path... ~577px in this case
                    var pathLength = path.getTotalLength();

                    // Make very long dashes (the length of the path itself)
                    path.style.strokeDasharray = pathLength + ' ' + pathLength;

                    // Offset the dashes so the it appears hidden entirely
                    path.style.strokeDashoffset = pathLength;

                    // Jake Archibald says so
                    // https://jakearchibald.com/2013/animated-line-drawing-svg/
                    path.getBoundingClientRect();

                    // When the page scrolls...
                    window.addEventListener("scroll", function() {

                        var scrollPercentage = (document.documentElement.scrollTop + document.body.scrollTop) / (document.documentElement.scrollHeight - document.documentElement.clientHeight);

                        // Length to offset the dashes
                        const elementDraw = document.getElementById('roadmap-text');
                        let length = elementDraw.clientHeight;
                        //let length = 4500;
                        let drawLength;
                        const scrollY = window.scrollY;

                        switch (true){
                            case scrollY < 1800:
                                drawLength = length * (scrollPercentage - 1.5);
                                break;
                            case scrollY >= 1800 && scrollY <= 2000:
                                drawLength = length * (scrollPercentage - 1.1);
                                break;
                            case scrollY >= 2000 && scrollY <= 3200:
                                drawLength = length * (scrollPercentage - 0.1);
                                break;
                            case scrollY <= 3200:
                                drawLength = length * (scrollPercentage - 0.08);
                                break;
                            /*case  scrollY >= 1300 && scrollY <= 1400:
                                drawLength = length * (scrollPercentage + 0.12);
                                break;
                            case  scrollY >= 1400 && scrollY <= 1500:
                                drawLength = length * (scrollPercentage + 0.18);
                                break;
                            case scrollY >= 1500 && scrollY <= 1700:
                                drawLength = length * (scrollPercentage + 0.22);
                                break;
                            case scrollY >= 1700 && scrollY <= 1800:
                                drawLength = length * (scrollPercentage + 0.25);
                                break;
                            case scrollY >= 1800 && scrollY <= 1900:
                                drawLength = length * (scrollPercentage + 0.30);
                                break;
                            case scrollY >= 1900 && scrollY <= 2300:
                                drawLength = length * (scrollPercentage + 0.36);
                                break;
                            case scrollY >= 2300:
                                drawLength = length * (scrollPercentage + 0.46);
                                break;*/

                            default:
                                drawLength = length * (scrollPercentage);
                        }

                        // Draw in reverse
                        path.style.strokeDashoffset = pathLength - drawLength;

                        // When complete, remove the dash array, otherwise shape isn't quite sharp
                        // Accounts for fuzzy math

                    });
            }
        }
    }
</script>

<template>
    <div class="draw-line-height mt-16">
        <div style="position: relative" class="rele">
            <svg id="line-svg" width="5" :height="heightLine"  viewBox="0 0 5 2637" fill="none" xmlns="http://www.w3.org/2000/svg">
                <line class="transition-fast" id="line-path" x1="2.5" y1="-2.12817e-07" x2="2.50022" y2="2637" stroke="#6B483C" stroke-width="5"/>
            </svg>
            <svg style="top: 0;left: -2px" class="m-auto absolute circle-svg" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
            </svg>
            <svg  style="top: 155px; left: -2px;" class="absolute z-10 circle-svg" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
            </svg>
            <svg class="absolute z-10 circle-svg" style="top: 305px;left: -2px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
            </svg>
            <svg class="absolute z-10 circle-svg" style="top: 475px;left: -2px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
            </svg>
            <svg class="absolute z-1 circle-svg" style="top: 680px;left: -2px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
            </svg>
            <svg class="absolute z-10 circle-svg" style="top: 880px;left: -2px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
            </svg>
            <svg class="absolute z-10 circle-svg" style="top: 1075px; left: -2px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
            </svg>
            <svg class="absolute z-10 circle-svg" style="top: 1280px; left: -2px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
            </svg>
            <svg class="absolute z-10 circle-svg" style="top: 1480px;left: -2px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
            </svg>
            <svg class="absolute z-10 circle-svg" style="top: 1680px;left: -2px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
            </svg>
            <svg class="absolute z-10 circle-svg" style="top: 1880px;left: -2px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
            </svg>
            <svg class="absolute z-10 circle-svg" style="top: 2085px;left: -2px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
            </svg>
            <svg class="absolute z-10 circle-svg" style="top: 2285px;left: -2px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
            </svg>
            <svg class="absolute z-10 circle-svg" style="top: 2525px;left: -2px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
            </svg>
            <svg class="absolute z-10 circle-svg" style="top: 2715px;left: -2px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
            </svg>
            <svg class="absolute z-10 circle-svg" style="top: 2915px;left: -2px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
            </svg>
            <svg class="absolute z-10 circle-svg" style="top: 3120px;right: -2px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
            </svg>
            <svg class="absolute z-10 circle-svg" style="top: 3340px;left: -2px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
            </svg>
            <svg class="absolute z-10 circle-svg" style="top: 3540px;left: -2px;" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
                <circle cx="27.5" cy="27.5" r="27.5" fill="#D0B39F"/>
            </svg>
        </div>
        <section class="flex flex-column justify-center align-middle relative text-indent" id="roadmap-text">
            <div class="z-20 transition-fast text-block" style="opacity: 0;" v-scroll="handleScrollElement" id="mobile-event1">
                <p class="text-3xl m-auto text-center font-weight-light italic text-white">1 Сенября 2017г.</p>
                <p class="text-2xl m-auto text-center font-weight-light text-white">
                    Знакомство — Церковь ⛪️
                    Рэу им. Плеханова
                </p>
            </div>
            <div class=" z-20 transition-fast text-block" style="opacity: 0;" v-scroll="handleScrollElement" id="mobile-event2">
                <div class="relative">
                    <p class="text-3xl m-auto text-center font-weight-light italic text-white">5 Ноября 2017.</p>
                </div>
                <p class="text-2xl text-center font-weight-light text-white">
                    Начало отношений —
                    Нежка 👩‍❤️‍👨
                </p>
            </div>
            <div class=" z-20 transition-fast text-block" style="opacity: 0;" v-scroll="handleScrollElement" id="mobile-event4">
                <p class="text-3xl m-auto text-center font-weight-light italic text-white">1 Января 2018г.</p>
                <p class="text-2xl text-center font-weight-light text-white">
                    Первый совместный
                    Новый Год — Реутов🎄
                </p>
            </div>
            <div class=" z-20 transition-fast text-block" style="opacity: 0;" v-scroll="handleScrollElement" id="mobile-event5">
                <div class="relative">
                    <p class="text-3xl m-auto text-center font-weight-light italic text-white">14 Февраля<br>2018г.</p>
                </div>
                <p class="text-2xl text-center font-weight-light text-white">
                    Сюрприз в лифте — ЦДМ🍿
                </p>
            </div>
            <div class="z-20 transition-fast text-block mobile-event6" style="opacity: 0;" v-scroll="handleScrollElement" id="mobile-event6">
                <div class="relative">
                    <p class="text-3xl m-auto text-center font-weight-light italic text-white">25 Марта<br>2018г.</p>
                </div>
                <p class="text-2xl text-center font-weight-light text-white">
                    Прекрасный Город<br>— Питер 🚂
                </p>
            </div>
            <div class="z-20 transition-fast text-block mobile-event7" style="opacity: 0;" v-scroll="handleScrollElement" id="mobile-event7">
                <div class="relative">
                    <p class="text-3xl m-auto text-center font-weight-light italic text-white">27 Мая<br>2018г.</p>
                </div>
                <p class="text-2xl text-center font-weight-light text-white">
                    Конная прогулка —
                    КД Лесное🐎
                </p>
            </div>
            <div class="z-20 transition-fast text-block mobile-event8" style="opacity: 0;" v-scroll="handleScrollElement" id="mobile-event8">
                <div class="relative">
                    <p class="text-3xl m-auto text-center font-weight-light italic text-white">Июль<br>2018г.</p>
                </div>
                <p class="text-2xl text-center font-weight-light text-white">
                    Студенческая
                    поездка — Анапа 🏖
                </p>
            </div>
            <div class="z-20 transition-fast text-block mobile-event9" style="opacity: 0;" v-scroll="handleScrollElement" id="mobile-event9">
                <div class="relative">
                    <p class="text-3xl m-auto text-center font-weight-light italic text-white">Август<br>2018г.</p>
                </div>
                <p class="text-2xl text-center font-weight-light text-white">
                    Прекрасный
                    Калининград 🏰
                </p>
            </div>
            <div class="z-20 transition-fast text-block mobile-event10" style="opacity: 0;" v-scroll="handleScrollElement" id="mobile-event10">
                <div class="relative">
                    <p class="text-3xl m-auto text-center font-weight-light italic text-white">5 Ноября<br>2018г.</p>
                </div>
                <p class="text-2xl text-center font-weight-light text-white">
                    Первая годовщина —
                    далеко, но рядом🥂
                </p>
            </div>
            <div class="z-20 transition-fast text-block  mobile-event11" style="opacity: 0;" v-scroll="handleScrollElement" id="mobile-event11">
                <div class="relative">
                    <p class="text-3xl m-auto text-center font-weight-light italic text-white">27 Апреля<br>2019г.</p>
                </div>
                <p class="text-2xl text-center font-weight-light text-white">
                    Знакомство с мамой
                    невесты — "Карлсон" 🤗
                </p>
            </div>
            <div class="z-20 transition-fast text-block mobile-event12" style="opacity: 0;" v-scroll="handleScrollElement" id="mobile-event12">
                <div class="relative">
                    <p class="text-3xl m-auto text-center font-weight-light italic text-white">25 Мая<br>2019г.</p>
                </div>
                <p class="text-2xl text-center font-weight-light text-white">
                    Начало совместной
                    жизни — А.Янгеля 🏠
                </p>
            </div>
            <div class="z-20 transition-fast text-block mobile-event13" style="opacity: 0;" v-scroll="handleScrollElement" id="mobile-event13">
                <div class="relative">
                    <p class="text-3xl m-auto text-center font-weight-light italic text-white">29 Декабря<br>2019г.</p>
                </div>
                <p class="text-2xl text-center font-weight-light text-white">
                    Совместный отдых
                    во Владивостоке 🌉
                </p>
            </div>
            <div class="z-20 transition-fast text-block mobile-event14" style="opacity: 0;" v-scroll="handleScrollElement" id="mobile-event14">
                <div class="relative">
                    <p class="text-3xl m-auto text-center font-weight-light italic text-white">31 Декабря<br>2019г.</p>
                </div>
                <p class="text-2xl text-center font-weight-light text-white">
                    Новый Год в кругу семьи невесты — Владивосток 🎄
                </p>
            </div>
            <div class="z-20 transition-fast text-block mobile-event15" style="opacity: 0;" v-scroll="handleScrollElement" id="mobile-event15">
                <div class="relative">
                    <p class="text-3xl m-auto text-center font-weight-light italic text-white">26 мая<br>2020г.</p>
                </div>
                <p class="text-2xl text-center font-weight-light text-white">
                    Предложение
                    руки и сердца 💍
                </p>
            </div>
            <div class="z-20 transition-fast text-block mobile-event16" style="opacity: 0;" v-scroll="handleScrollElement" id="mobile-event16">
                <div class="relative">
                    <p class="text-3xl m-auto text-center font-weight-light italic text-white">31 Декабря<br>2020г.</p>
                </div>
                <p class="text-2xl text-center font-weight-light text-white">
                    Окончание РЭУ
                    им. Плеханова 🧑‍🎓
                </p>
            </div>
            <div class="z-20 transition-fast text-block mobile-event17" style="opacity: 0;" v-scroll="handleScrollElement" id="mobile-event17">
                <div class="relative">
                    <p class="text-3xl m-auto text-center font-weight-light italic text-white">23 Сентября<br>2020г.</p>
                </div>
                <p class="text-2xl text-center font-weight-light text-white">
                    Теперь мы коллеги
                    — М.Белоруская 👩🏼‍💻
                </p>
            </div>
            <div class="z-20 transition-fast text-block mobile-event18" style="opacity: 0;" v-scroll="handleScrollElement" id="mobile-event18">
                <div class="relative">
                    <p class="text-3xl m-auto text-center font-weight-light italic text-white">Ноябрь<br>2020г.</p>
                </div>
                <p class="text-2xl text-center font-weight-light text-white">
                    Совместная с мамой жениха
                    зимняя поездка на Кавказ🏔

                </p>
            </div>
            <div class="z-20 transition-fast text-block mobile-event19" style="opacity: 0;" v-scroll="handleScrollElement" id="mobile-event19">
                <div class="relative">
                    <p class="text-3xl m-auto text-center font-weight-light italic text-white">Март<br>2021г.</p>
                </div>
                <p class="text-2xl text-center font-weight-light text-white">
                    День влюблённых<br>в снегу 🏂
                </p>
            </div>
            <div class="z-20 transition-fast text-block mobile-event20" style="opacity: 0;" v-scroll="handleScrollElement" id="mobile-event20">
                <p class="text-2xl text-center font-weight-light text-white">
                    Крым - последняя точка Карты начала нашей любви ❤️
                </p>
                <div class="relative">
                    <p class="text-xl m-auto text-center font-weight-light italic text-white">1 Сентября<br>2021г.</p>
                </div>
            </div>
        </section>
    </div>
</template>

<style lang="scss">
    #line-svg {
        width: 10%;
        min-width: 50px;
    }

    .transition-slow {
        transition: 0.5s;
    }

    .transition-fast {
        transition: 1.5s all cubic-bezier(0.39, 0.575, 0.565, 1);
    }

    .text-block {
        margin-bottom: 32px;
        @media screen and (min-width: 430px) {
            margin-bottom: 38px;
        }
    }

    @media screen and (min-width: 430px) {
        .circle-svg {
            display: none;
        }
    }

    .text-indent {
        margin-left: 36px;
        @media screen and (max-width: 381px) {
            margin-left: 24px;
        }
    }
</style>
