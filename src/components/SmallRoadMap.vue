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
            var scrollableElement = document.body; //document.getElementById('scrollableElement');
            scrollableElement.addEventListener('wheel', checkScrollDirection);

            function checkScrollDirection(event) {
                if (checkScrollDirectionIsUp(event)) {
                    const element = document.getElementById('airplane');
                    element.classList.add("airplane-up");
                    element.classList.remove("airplane-down");
                } else {
                    const element = document.getElementById('airplane');
                    element.classList.add("airplane-down");
                    element.classList.remove("airplane-up");
                }
            }

            function checkScrollDirectionIsUp(event) {
                if (event.wheelDelta) {
                    return event.wheelDelta > 0;
                }
                return event.deltaY < 0;
            }
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
            scrollingMap: function () {
                const elementDraw = document.getElementById('draw-line-height');
                let length = elementDraw.clientHeight + 500;
                // When the page scrolls...
                const elementAirplane = document.getElementById('airplane');
                const elementBeach = document.getElementById('beach');
                    if (length >= window.scrollY && window.scrollY >= 500) {
                        elementAirplane.setAttribute(
                            'style',
                            `top: ${window.scrollY-600}px`
                        )
                    }
                    if (length <= window.scrollY) {
                        elementAirplane.classList.add("nol-opatity");
                        elementBeach.setAttribute(
                            'style',
                            `opacity: 1; transform: translate3d(0, -10px, 0)`)
                    } else {
                        elementAirplane.classList.remove("nol-opatity");
                        elementBeach.setAttribute(
                            'style',
                            `opacity: 0;`)
                    }
            }
        }
    }
</script>

<template>
    <div class="draw-line-height mt-16" id="draw-line-height">
        <div class="w-1/6" style="position: relative">

            <div class="airplane transition-fast" style="transform: rotate(180deg);" v-scroll="scrollingMap" id="airplane"></div>
            <!--<svg style="top: 0;left: -2px" class="m-auto absolute circle-svg" width="55" height="55" viewBox="0 0 55 55" fill="none" xmlns="http://www.w3.org/2000/svg">
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
            </svg>-->
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
            <div class="z-20 transition-fast text-block mobile-event20 relative" style="opacity: 0;" v-scroll="handleScrollElement" id="mobile-event20">
                <p class="text-2xl text-center font-weight-light text-white">
                    Крым - последняя точка Карты начала нашей любви ❤️
                </p>
                <div class="relative">
                    <p class="text-xl m-auto text-center font-weight-light italic text-white">1 Сентября<br>2021г.</p>
                </div>
                <div class="beach-image transition-fast absolute" style="opacity: 0;" v-scroll="scrollingMap" id="beach"></div>
            </div>
        </section>
    </div>
</template>

<style lang="scss">
    #line-svg {
        width: 10%;
        min-width: 50px;
    }

    .nol-opatity {
        opacity: 0;
    }

    .airplane-up {
        transform: rotate(0deg);
    }

    .airplane-down {
        transform: rotate(180deg);
    }

    .airplane {
        position: absolute;
        width: 70px;
        height: 70px;
        background: url("data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iaXNvLTg4NTktMSI/Pg0KPCEtLSBHZW5lcmF0b3I6IEFkb2JlIElsbHVzdHJhdG9yIDE5LjAuMCwgU1ZHIEV4cG9ydCBQbHVnLUluIC4gU1ZHIFZlcnNpb246IDYuMDAgQnVpbGQgMCkgIC0tPg0KPHN2ZyB2ZXJzaW9uPSIxLjEiIGlkPSJMYXllcl8xIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHhtbG5zOnhsaW5rPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5L3hsaW5rIiB4PSIwcHgiIHk9IjBweCINCgkgdmlld0JveD0iMCAwIDUxMS45OTIgNTExLjk5MiIgc3R5bGU9ImVuYWJsZS1iYWNrZ3JvdW5kOm5ldyAwIDAgNTExLjk5MiA1MTEuOTkyOyIgeG1sOnNwYWNlPSJwcmVzZXJ2ZSI+DQo8Zz4NCgk8cG9seWdvbiBzdHlsZT0iZmlsbDojRjVGN0ZBOyIgcG9pbnRzPSIyNTcuOTk1LDM2Ny4zMSAxNTkuMzMzLDQyOS4zMDggMTU5LjMzMyw0NjguNjg0IDIxNC42NjcsNDUxLjk5NiAyOTEuMzM4LDQ0OS45OTYgDQoJCTM1MS4zMzcsNDY1Ljk5NiAzNTEuMzM3LDQyOS4zMDggCSIvPg0KCTxwb2x5Z29uIHN0eWxlPSJmaWxsOiNGNUY3RkE7IiBwb2ludHM9IjI5OS45OTQsMTgyLjQ5NCAxOTkuNDk2LDE4OS40OTMgMTEsMjgzLjUgMTUuNDk5LDMyOS40OTggMjU1Ljk5NSwyODYgNTA0Ljk5LDMyOS40OTggDQoJCTUwNC45OSwyODYgCSIvPg0KPC9nPg0KPHBvbHlnb24gc3R5bGU9ImZpbGw6IzRGQzJFOTsiIHBvaW50cz0iMjkxLjk5NCw2NC4wMjcgMjc1LjMzOSwzNy4zNTYgMjQ5LjMzMSwzNC4wMjggMjMxLjMzMSw0Ni42ODQgMjE0LjY2Nyw4Ni42ODMgDQoJMjIzLjUwMyw0NjguNjg0IDI4Ny41MSw0NjguNjg0IDI5Ni42NjYsMTE3LjM1NCAiLz4NCjxnPg0KCTxwYXRoIHN0eWxlPSJmaWxsOiMwODA4MDg7IiBkPSJNMjg2LjgyMyw5Mi4yMjljLTAuNDY5LTEuMjM0LTIuMzc1LTUuNTkzLTcuMjk3LTkuNzM0Yy00LjI1LTMuNTYyLTExLjg2Ny03LjgyOC0yNC4wMTYtNy44MjgNCgkJYy0xOS40NzYsMC0yOC44NDMsMTEuMDQ3LTMxLjMxMiwxNy41NjJjLTIuMDg2LDUuNTE2LDAuNjk1LDExLjY3Miw2LjIwMywxMy43NWM1LjM1OSwyLjAxNiwxMS4zMjgtMC41NDcsMTMuNTctNS43NjYNCgkJYzAuMzc1LTAuNjU2LDIuODItNC4yMTksMTEuNTM5LTQuMjE5YzguNzExLDAsMTEuMTU2LDMuNTYyLDExLjUzOSw0LjIxOWMxLjcxOSw0LDUuNjMzLDYuNDUzLDkuNzg5LDYuNDUzDQoJCWMxLjI1LDAsMi41MzEtMC4yMTksMy43ODEtMC42ODhDMjg2LjEyLDEwMy45MDEsMjg4LjksOTcuNzQ1LDI4Ni44MjMsOTIuMjI5eiIvPg0KCTxwYXRoIHN0eWxlPSJmaWxsOiMwODA4MDg7IiBkPSJNNTA2LjE0NiwyNzguNWwtNDcuNDk5LTI0LjEwMnYtNi4wNjJjMC01LjkwNi00Ljc2Ni0xMC42NzItMTAuNjU2LTEwLjY3Mg0KCQljLTQuMzU5LDAtOC4xMDksMi42MDktOS43NSw2LjM1OWwtNDMuNTkzLTIyLjA5M3YtNS41YzAtNS44NzUtNC43NjYtMTAuNjU2LTEwLjY1NS0xMC42NTZjLTQuMTg4LDAtNy43ODEsMi40MDYtOS41MzEsNS45MDYNCgkJbC02Ny42NzEtMzQuMzEyYzEuMjAzLTQzLjEyNCwyLjA0Ny03NS4yOCwyLjA0Ny04MS4zNzRjMC0xMy4zNDMtNS4wNjItMzEuMDc4LTEyLjg3NS00NS4xNzENCgkJYy0xMC41NjItMTkuMDE1LTI0LjkyOS0yOS40ODQtNDAuNDUyLTI5LjQ4NHMtMjkuODgyLDEwLjQ2OS00MC40NDUsMjkuNDg0Yy03LjgyOCwxNC4wOTMtMTIuODksMzEuODI4LTEyLjg5LDQ1LjE3MQ0KCQljMCw2LjEyNSwwLjg1MiwzOC41LDIuMDcsODEuODQybC02Ni43MSwzMy44NDNjLTEuNzUtMy41LTUuMzU5LTUuOTA2LTkuNTM5LTUuOTA2Yy01Ljg5MSwwLTEwLjY2NCw0Ljc4MS0xMC42NjQsMTAuNjU2djUuNQ0KCQlsLTQzLjU3NywyMi4wOTNjLTEuNjU2LTMuNzUtNS4zOTgtNi4zNTktOS43NTgtNi4zNTljLTUuODksMC0xMC42NjQsNC43NjYtMTAuNjY0LDEwLjY3MnY2LjA2Mkw1Ljg0NCwyNzguNQ0KCQlDMi4yNTgsMjgwLjMxMiwwLDI4My45NjksMCwyODh2NDIuNjU0YzAsMy4yMTksMS40NDUsNi4yNSwzLjkzOCw4LjI4MWMxLjkxNCwxLjU2Miw0LjI5NywyLjQwNiw2LjcyNywyLjQwNg0KCQljMC43MjcsMCwxLjQ1My0wLjA5NCwyLjE3MS0wLjIxOWwxOTQuOTU4LTQwLjU2MWMwLjgwNSwyNy4zMTEsMS42MDIsNTQuMTIzLDIuMzIsNzguMDYxbC01Ni4yMjYsMzkuMzExDQoJCWMtMi44NTksMS45NjktNC41NTUsNS4yNS00LjU1NSw4LjcxOXY0Mi42ODhjMCwzLjQzOCwxLjY1Niw2LjY1Niw0LjQ1Myw4LjY1NmMxLjgzNiwxLjMxMiw0LjAwOCwyLDYuMjExLDINCgkJYzEuMTQ4LDAsMi4zMDUtMC4xODgsMy40MjktMC41NjJsNDkuMjEtMTYuNjg4YzAuMTA5LDMuNTk0LDAuMTgsNS45NjksMC4yMTEsNi45MDZjMC4xNzIsNS43NSw0Ljg5OCwxMC4zNDQsMTAuNjY0LDEwLjM0NGgyMS4zMzUNCgkJbDAsMGMwLDUuOTA2LDQuNzczLDEwLjY1NiwxMC42NjQsMTAuNjU2YzUuODkxLDAsMTAuNjY0LTQuNzUsMTAuNjY0LTEwLjY1NmwwLDBoMjEuMzM1YzUuNzY2LDAsMTAuNDg0LTQuNTk0LDEwLjY3Mi0xMC4zNDQNCgkJYzAuMDE2LTAuOTY5LDAuMDk0LTMuNDY5LDAuMjE5LTcuMjVsNTAuMTU1LDE3LjAzMWMxLjEyNSwwLjM3NSwyLjI4MSwwLjU2MiwzLjQzOCwwLjU2MmMyLjIwMywwLDQuMzc1LTAuNjg4LDYuMjE5LTINCgkJYzIuNzgxLTIsNC40MzgtNS4yMTksNC40MzgtOC42NTZ2LTQyLjY4OGMwLTMuNDY5LTEuNjg4LTYuNzUtNC41NDctOC43MTlsLTU3LjE3MS0zOS45OThjMC43MDMtMjMuODEyLDEuNS01MC40MzgsMi4yOTctNzcuNTYxDQoJCWwxOTUuOTE4LDQwLjc0OGMwLjcxOSwwLjEyNSwxLjQ1MywwLjIxOSwyLjE4OCwwLjIxOWMyLjQyMiwwLDQuODEyLTAuODQ0LDYuNzE5LTIuNDA2YzIuNS0yLjAzMSwzLjkzOC01LjA2MiwzLjkzOC04LjI4MVYyODgNCgkJQzUxMS45OSwyODMuOTY5LDUwOS43NCwyODAuMzEyLDUwNi4xNDYsMjc4LjV6IE0zNDEuMzM3LDQzMi4yMTV2MjIuMjE5bC00MS4zNDMtMTRsMS4wNjItMzYuMzczTDM0MS4zMzcsNDMyLjIxNXogTTIxLjMzNSwzMTcuNTYNCgkJdi0yMi45OThMMjA0LjkxLDIwMS40M2MwLjY5NSwyNC4yOTYsMS40NjksNTAuODQzLDIuMjUsNzcuNDc2TDIxLjMzNSwzMTcuNTZ6IE0xNzAuNjYxLDQ1NC40MzR2LTIyLjIxOWw0MC4yMTgtMjguMTIzDQoJCWMwLjQxNCwxMy45MDQsMC43ODEsMjYuMjE3LDEuMDg2LDM2LjM0MkwxNzAuNjYxLDQ1NC40MzR6IE0yNjYuMTc1LDQ1OC42NTJ2LTUzLjMxMWMwLTUuOTA2LTQuNzczLTEwLjY4OC0xMC42NjQtMTAuNjg4DQoJCXMtMTAuNjY0LDQuNzgxLTEwLjY2NCwxMC42ODh2NTMuMzExaC0xMC45ODRjLTAuMDk0LTIuOTM4LTAuMjAzLTYuNDY5LTAuMzItMTAuNWMwLTAuMTU2LDAuMDA4LTAuMzEyLDAuMDA4LTAuNDY5bC0xLjg2Ny02My45OTgNCgkJYy0wLjAxNi0wLjQwNi0wLjA1NS0wLjgxMi0wLjEwOS0xLjIxOWMtMy4xNTYtMTA1LjY1NC04LjA2Mi0yNzIuMTktOC4wNjItMjg2LjQ3MmMwLTE4LjAxNSwxNC40ODQtNTMuMzI3LDMyLTUzLjMyNw0KCQlzMzEuOTk5LDM1LjMxMiwzMS45OTksNTMuMzI3YzAsMTguODc1LTguNTc3LDMwNC4zMTUtMTAuMzU4LDM2Mi42NTdMMjY2LjE3NSw0NTguNjUyTDI2Ni4xNzUsNDU4LjY1MnogTTQ5MC42NDYsMzE3LjU2DQoJCWwtMTg2Ljc3Ny0zOC44NDJjMC43ODEtMjYuNzU4LDEuNTYyLTUzLjQxNCwyLjI1LTc3Ljc4OGwxODQuNTI3LDkzLjYzMlYzMTcuNTZ6Ii8+DQo8L2c+DQo8Zz4NCjwvZz4NCjxnPg0KPC9nPg0KPGc+DQo8L2c+DQo8Zz4NCjwvZz4NCjxnPg0KPC9nPg0KPGc+DQo8L2c+DQo8Zz4NCjwvZz4NCjxnPg0KPC9nPg0KPGc+DQo8L2c+DQo8Zz4NCjwvZz4NCjxnPg0KPC9nPg0KPGc+DQo8L2c+DQo8Zz4NCjwvZz4NCjxnPg0KPC9nPg0KPGc+DQo8L2c+DQo8L3N2Zz4NCg==") no-repeat;
        z-index: 22;
        @media screen and (min-width: 1030px) and (max-width: 1412px) {
            width: 250px;
            height: 250px;
            left: 50px;
        }
        @media screen and (min-width: 768px) and (max-width: 1030px) {
            width: 150px;
            height: 150px;
            left: 55px;
        }
        @media screen and (min-width: 768px) and (max-width: 768px) {
            width: 100px;
            height: 100px;
            left: 20px;
        }
    }

    .beach-image {
        position: absolute;
        background: url("https://img.icons8.com/clouds/2x/beach.png") no-repeat;
        background-size: contain;
        z-index: 22;
        @media screen and (min-width: 1030px) and (max-width: 1412px) {
            width: 250px;
            height: 250px;
            left: -150px;
            top: -75px;
        }
        @media screen and (min-width: 768px) and (max-width: 1030px) {
            width: 150px;
            height: 150px;
            left: -150px;
            top: -75px;
        }
        @media screen and (max-width: 768px) {
            width: 120px;
            height: 120px;
            left: -70px;
            top: 55px;
        }
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
