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
                daysLeft: ''
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
                    this.daysLeft = "Это чудестное событие уже произошло!)"
                } else {
                    if (daysLeft === 0) {
                        this.daysLeft = "Завтра свадьба!!! 🥳"
                    } else {
                        this.daysLeft = "До особенного дня осталось " + daysLeft + dayname + "!!! 💒";
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
                    } else {
                        appeal = appeal + this.guests.name1 + ' ' + this.guests.surname1 + ' и';
                    }
                } else {
                    if (this.guests?.name3) {
                        appeal= appeal + this.guests.name1 + ',';
                    } else {
                        appeal= appeal + this.guests.name1 + ' и';
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
                } else if (this.guests.name3) {
                    appeal= appeal + ' ' + this.guests.name4 + ',';
                }

                return appeal;
            }
        },


    }
</script>

<template>
    <div class="overflow-hidden">
  <v-container class="pt-24 xl:pt-48">
      <section class="flex flex-col xl:flex-row align-middle wrapper">
        <h1 class="text-center hidden xl:block font-weight-light m-auto w-1/2 align-middle" style="font-size: 72px;line-height: 84px;color:#6B483C; background-color: transparent!important;letter-spacing: 12px;">
          Денис<br>
            &<br>
            Диана
        </h1>
          <h1 class="text-center block xl:hidden font-weight-light m-auto align-middle pb-12" style="font-size: 72px;color:#6B483C; background-color: transparent!important;">
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
          <video muted="muted" autoplay="autoplay" loop src="../assets/CrimeaAerial.mp4"> </video>
          <h3 class="text-2xl sm:text-3xl xl:text-6xl text-center text-white font-weight-light z-30 crimea-heading">Почему Крым?</h3>
          <div class="text-opacity grid grid-flow-row md:grid-flow-col md:grid-cols-2 md:gap-32 crimea-second-block">
              <p class="text-xs sm:text-2xl xl:text-2xl text-justify text-white font-weight-light z-30">
                  Ю́жный бе́рег Кры́ма — одна из важнейших и наиболее популярных в бывшем СССР приморских зон курортного лечения, отдыха и туризма; включает города-курорты Алупка, Ялта, Алушта, Судак и многочисленные курортные посёлки и курортные местности.
              </p>
              <p class="text-xs sm:text-2xl xl:text-2xl text-justify text-white font-weight-light z-30 crimea-second-text">
                  Ю́жный бе́рег Кры́ма — одна из важнейших и наиболее популярных в бывшем СССР приморских зон курортного лечения, отдыха и туризма; включает города-курорты Алупка, Ялта, Алушта, Судак и многочисленные курортные посёлки и курортные местности.
              </p>
          </div>
      </section>
    <v-container>
      <section class="flex flex-row justify-center align-middle pt-16" id="timer">
            <h3 class="text-2xl sm:text-3xl xl:text-6xl text-center text-white font-weight-light">{{ daysLeft }}</h3>
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
        position: absolute;
        filter: opacity(0.6);
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
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

    .crimea-second-text {
        @media screen and (max-width: 462px) {
            display: none;
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

    @media screen and (min-width: 1412px) {

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
