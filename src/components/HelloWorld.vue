<script>
    import RoadMap from './RoadMap';
    import SmallRoadMap from './SmallRoadMap';

    export default {
        name: 'HelloWorld',

        components: {
            RoadMap,
            SmallRoadMap
        },

        data () {
            return {
                items: [
                    {
                        src: 'https://sun9-74.userapi.com/impf/e_2iJ3cFyVqUrSpRAbJYQSQzSy7lObINcyRV4A/BXulRkg-H6E.jpg?size=1620x2160&quality=96&sign=19960dff0519831b30fbbb38cd324097&type=album',
                    },
                    {
                        src: 'https://sun9-76.userapi.com/impf/SH_7k-NhEJOedCgiJN8XXj5AXECd3c2cUWd1yw/GtrW2KHOdJo.jpg?size=960x1280&quality=96&sign=6fd5e5cb1c546055265b65c598090d5a&type=album',
                    },
                    {
                        src: 'https://sun9-45.userapi.com/impf/TWInnZv7pa6oqLb4oi6NEZImT8NBwYtyl4CBuQ/Kf1OL8QtqJE.jpg?size=2560x1920&quality=96&sign=bd8ff0c67a78270ef41d6ae8e4fedd0b&type=album',
                    },
                    {
                        src: 'https://sun9-32.userapi.com/impf/suxRsIk_8_uLh4uUyelaBIKxhJg6ixNwKR7WWQ/p1EWB-q14N8.jpg?size=1620x2160&quality=96&sign=31889a9087a8c65a39341ad62e16d6bc&type=album',
                    },
                    {
                        src: 'https://sun9-57.userapi.com/impf/0Irbti5NXdSguXWr_a8RdEisqvZj_XxSdQgNLg/LrT2J-uDUW4.jpg?size=1024x768&quality=96&sign=450247ef71845da051b0f444192ba5b4&type=album',
                    },
                    {
                        src: 'https://sun9-10.userapi.com/impf/33QeLQXiSkCGHnXxFK3F3Zab1TWGD9K0HTPdvg/CGHquEzWZIw.jpg?size=2560x1920&quality=96&sign=7af8fa6f8700b2277d05f85f8b447962&type=album',
                    },
                ],
                guests: {},
                timerText: '',
                daysLeft: '',
                dayName: ''
            }
        },

        created()
        {
            this.daysLeftNewYear();
            let href = window.location.href;
            let decoderLink;
            try {
                decoderLink = decodeURI(href);
            } catch (e) {
                console.error(e);
            }
            let uri = decoderLink.split('?');
            if (uri.length === 2)
            {
                let vars = uri[1].split('&');
                let getVars = {};
                let tmp = '';
                vars.forEach(function(v){
                    tmp = v.split('=');
                    if(tmp.length === 2)
                        getVars[tmp[0]] = tmp[1];
                });
                this.guests = getVars;
            }
        },

        methods: {
            setControls(){
                const videoElement = document.getElementById("video");
                if(document.documentElement.clientWidth <= 800){
                    videoElement.setAttribute('controls', 'controls');
                }
            },
            daysLeftNewYear() {
                const today = new Date();
                const nextDate = new Date("September 1, 2021");
                //Количество миллисекунд в одном дне
                const msPerDay = 24 * 60 * 60 * 1000;
                //Высчитываем количество дней
                const daysLeft = Math.round((nextDate.getTime() - today.getTime()) / msPerDay);
                let dayname = "";
                const ds = "" + daysLeft;
                //Вырезаем последнею цифру
                const dd = parseInt(ds.substr(ds.length - 1));
                //Склоняем слово ДЕНЬ
                if (daysLeft > 4 && daysLeft < 21) dayname = " дней";
                else if (dd === 1) dayname = " день";
                else if (dd === 2 || dd === 3 || dd === 4) dayname = " дня";
                else dayname = " дней";
                if (daysLeft < 0) {
                    this.timerText = "Урааа, это чудестное событие уже произошло! 🥳"
                } else {
                    if (daysLeft === 0) {
                        this.timerText = "Завтра свадьба!!! 🥳"
                    } else {
                        this.timerText = "До особенного дня осталось:";
                        this.daysLeft = daysLeft;
                        this.dayName = dayname;
                    }
                }
            }
        },

        computed: {
            appeal(){
                let appeal;

                if(this.guests?.g){
                    this.guests.g === 'm' ? appeal = 'Дорогой ' : appeal = 'Дорагая ';
                } else {
                    appeal = 'Дорогие ';
                }

                if (this.guests?.surname1) {
                    if (this.guests?.name3) {
                        appeal = appeal + this.guests.name1 + ' ' + this.guests.surname1 + ',';
                    } else if ( !this.guests?.name3 && this.guests?.name2 ) {
                        appeal = appeal + this.guests.name1 + ' ' + this.guests.surname1 + ' и';
                    } else {
                        appeal = appeal + this.guests.name1 + ' ' + this.guests.surname1 + ',';
                    }
                } else {
                    if (this.guests?.name3) {
                        appeal= appeal + this.guests.name1 + ',';
                    } else if ( !this.guests?.name3 && this.guests?.name2 ) {
                        appeal= appeal + this.guests.name1 + ' и';
                    } else {
                        appeal = appeal + this.guests.name1 + ',';
                    }
                }

                if (this.guests?.surname2) {
                    appeal= appeal + ' ' + this.guests.name2 + ' ' + this.guests.surname2 + ',';
                } else if (this.guests.name2) {
                    appeal= appeal + ' ' + this.guests.name2 + ',';
                }

                if (this.guests?.surname3) {
                    appeal= appeal + ' ' + this.guests.name3 + ' ' + this.guests.surname3 + ',';
                } else if (this.guests.name3) {
                    appeal= appeal + ' ' + this.guests.name3 + ',';
                }

                if (this.guests?.surname4) {
                    appeal= appeal + ' ' + this.guests.name4 + ' ' + this.guests.surname4 + ',';
                } else if (this.guests.name4) {
                    appeal= appeal + ' ' + this.guests.name4 + ',';
                }

                return appeal;
            }
        },
        head () {
            return {
                title: 'test',
                meta: [
                    {
                        name: 'viewport',
                        content: 'width=device-width,initial-scale=1.0,minimum-scale=1.0'
                    }
                ]
            }
        }

    }
</script>

<template>
    <div class="overflow-hidden">
  <v-container class="pt-24 xl:pt-48">
      <section class="flex flex-col xl:flex-row align-middle wrapper">
        <h1 class="text-center hidden xl:block font-weight-light m-auto w-1/2 align-middle main-heading">
          Денис<br>
            &<br>
            Диана
        </h1>
          <h1 class="text-center block xl:hidden font-weight-light m-auto align-middle pb-12 main-heading">
              Денис & Диана
          </h1>
          <v-carousel
                  class="w-full xl:w-1/2 rounded-2xl photo-carousel"
                      cycle
                      height="640"
                      hide-delimiter-background
                    hide-delimiters
                      show-arrows-on-hover
              >
                      <v-carousel-item
                              v-for="(item,i) in items"
                              :key="i"
                              :src="item.src"
                      ></v-carousel-item>
              </v-carousel>
      </section>
      <section class="flex flex-row align-middle pt-24 xl:pt-64 wrapper">
          <h2 class="text-5xl text-center font-weight-light m-auto" style="color:#6B483C">
              Немного из истории
          </h2>
      </section>
      <RoadMap class="road-map_block" />
      <SmallRoadMap class="road-map_block-mobile" />
      <section class="flex flex-column justify-center align-middle appeal-block">
          <h1 class="mb-6 mx-4 text-2xl sm:text-4xl xl:text-5xl" style="color:#6B483C; background-color: transparent!important;">{{ appeal }} мы, Диана и Денис, с удовольствием приглашаем вас провести с нами наш особенный день.<br>Будем очень рады вас видеть 1 сентября на нашей свадьбе. 🎉</h1>
          <h2 class="text-xl sm:text-2xl xl:text-3xl" style="color:#6B483C; background-color: transparent!important;">Также будем благодарны, если вы постараетесь соблюсти мягкие оттенки в цветовой гамме своих нарядов. </h2>
      </section>
  </v-container>
      <section style="justify-content: end" class="flex flex-column videoWrapper align-middle">
          <video v-scroll="setControls" id="video" muted="muted" autoplay="autoplay" loop src="../assets/CrimeaAerial.mp4"> </video>
          <h3 class="text-2xl sm:text-3xl xl:text-6xl text-center text-white font-weight-light z-30 crimea-heading">Почему Крым?</h3>
          <div class="text-opacity grid grid-flow-row md:grid-flow-col md:grid-cols-1 crimea-second-block">
              <p class="text-justify text-white hidden md:block font-weight-light crimea-text z-30">
                  Крым - чудесное место. Нереально красивые виды, приятный климат, чистое и тёплое море! Нам кажется, что это даст возможность не только побывать на нашем празднике, но и прекрасно провести свой отпуск.
                  <br><br>Дату мы тоже постарались подобрать, чтобы это было удобно для каждого гостя. Те, кто зависят от учебного процесса, смогут и отдохнуть в августе, и посетить наш праздник, и при этом совсем ненадолго выйдут из привычного режима. А те, у кого есть время, смогут задержаться в Крыму, где сентябрь - бархатный сезон (цены ниже летних, приезжих меньше, а погода приятнее).
                  <br>Мы очень ждём вас и надеемся, что радостно и комфортно будет всем!
              </p>
          </div>
      </section>
        <section style="justify-content: end" class="flex flex-column align-middle">
            <p class="text-center text-white font-weight-light block md:hidden mx-6 sm:mx-12 mt-12 crimea-text z-30">
                Крым - чудесное место. Нереально красивые виды, приятный климат, чистое и тёплое море! Нам кажется, что это даст возможность не только побывать на нашем празднике, но и прекрасно провести свой отпуск.
                <br><br>Дату мы тоже постарались подобрать, чтобы это было удобно для каждого гостя. Те, кто зависят от учебного процесса, смогут и отдохнуть в августе, и посетить наш праздник, и при этом совсем ненадолго выйдут из привычного режима. А те, у кого есть время, смогут задержаться в Крыму, где сентябрь - бархатный сезон (цены ниже летних, приезжих меньше, а погода приятнее).
                <br>Мы очень ждём вас и надеемся, что радостно и комфортно будет всем!
            </p>
        </section>
    <v-container>
      <section class="flex flex-column justify-center align-middle pt-16" id="timer">
            <h3 class="text-2xl sm:text-3xl sm:text-6xl mb-6 text-center text-white font-weight-light">{{ timerText }}</h3>
          <div style="width: fit-content;" class="relative m-auto">
              <svg style="width: 240px;height: 240px; margin: auto" width="240" height="240" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M3.09265 9.40427H20.9166" stroke="#6B483C" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
                  <path d="M16.0437 2V5.29078" stroke="#6B483C" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
                  <path d="M7.96552 2V5.29078" stroke="#6B483C" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
                  <path fill-rule="evenodd" clip-rule="evenodd" d="M16.2383 3.57919H7.77096C4.83427 3.57919 3 5.21513 3 8.22222V17.2719C3 20.3262 4.83427 22 7.77096 22H16.229C19.175 22 21 20.3546 21 17.3475V8.22222C21.0092 5.21513 19.1842 3.57919 16.2383 3.57919Z" stroke="#6B483C" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
              <div v-if="daysLeft > 1" class="timer-position absolute">
                  <p class="text-6xl mb-0 text-center text-white font-weight-light timer-position">{{ daysLeft }}</p>
                  <p class="text-xl text-center text-white font-weight-light timer-position">{{ dayName }}</p>
              </div>
          </div>
      </section>
      <section class="flex flex-row justify-center align-middle pt-24">
        <iframe src="https://docs.google.com/forms/d/e/1FAIpQLSfHv_IqtKxUhyZHPG4DwSIIA8u2OH9RXZAp8TnfTiJBvYNOhw/viewform?embedded=true" width="640" height="1000" frameborder="0" marginheight="0" marginwidth="0">Загрузка…</iframe>
      </section>
  </v-container>
    </div>
</template>

<style lang="scss" >

    body {
        font-family: 'arial', sans-serif;
    }

    .photo-carousel {
        max-width: 720px!important;
        margin: auto;
    }

    .wrapper {
        margin: 0 auto;
        max-width: 1200px;
    }

    .road-map_block {
        min-width: 1512px !important;
    }
    .road-map_block-mobile {
        display: none;
    }

    .videoWrapper {
        position: relative;
        padding-bottom: 56.25%; /* 16:9 */
        height: 0;
    }
    .videoWrapper video {
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        position: absolute;
        @media screen and (min-width: 767px) {
            filter: opacity(0.4);
        }
        @media screen and (max-width: 767px) {
            filter: opacity(0.8);
        }
    }

    .crimea-second-block{
        @media screen and (min-width: 1412px) {
            margin: auto 6rem;
        }
        @media screen and (min-width: 811px) and (max-width: 1412px) {
            margin: auto 3rem;
        }
        margin: auto 1rem;
    }

    .crimea-text {
        font-size: 1.7rem;
        line-height: 50px;
        @media screen and (min-width: 991px) and (max-width: 1212px) {
            font-size: 1.3rem;
            line-height: 40px;
        }
        @media screen  and (min-width: 767px) and (max-width: 991px) {
            font-size: 1rem;
            line-height: 30px;
        }
        @media screen and (min-width: 411px) and (max-width: 767px) {
            font-size: 1.5rem;
            line-height: 30px;
        }
        @media screen and (max-width: 411px) {
            font-size: 1rem;
            line-height: 28px;
        }
    }

    .crimea-heading{
        @media screen and (min-width: 1412px) {
            margin-top: 6rem;
            margin-bottom: 4rem;
        }
        margin-top: 2rem;
        margin-bottom: 1rem;
    }

    .text-opacity{
        filter: opacity(1);
    }

    .appeal-block {
        background-color: white;
        @media screen and (min-width: 1412px) {
            margin-top: 24rem;
            margin-bottom: 8rem;
            padding: 45px;
            border-radius: 40px;
        }
        @media screen and (min-width: 811px) and (max-width: 1412px) {
            margin-top: 2rem;
            margin-bottom: 8rem;
            padding: 35px;
            border-radius: 30px;
        }
        @media screen and (max-width: 811px) {
            margin: 2rem 2rem 8rem;
            border-radius: 20px;
            padding: 15px;
        }
    }

    .timer-position {
        top: 45%;
        left: 28%;
    }

    .main-heading {
        color:#6B483C;
        background-color: transparent!important;
        @media screen and (min-width: 511px) {
            font-size: 72px;
            line-height: 84px;
            letter-spacing: 12px;
        }
        @media screen and (max-width: 514px) {
            font-size: 42px;
            line-height: 54px;
            letter-spacing: 8px;
        }
    }

    @media screen and (max-width: 1412px) {
        .road-map_block {
            display: none!important;
        }
        .road-map_block-mobile {
            width: 100%;
            justify-content: flex-end;
            display: flex;
        }
    }

    svg {
        transition: 3.5s all cubic-bezier(0.39, 0.575, 0.565, 1);
    }
</style>
