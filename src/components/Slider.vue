<template>
    <div class="wrapper">
        <b-carousel ref="slider"
                    id="carousel-1"
                    v-model="slide"
                    :interval="4000"
                    indicators
                    background="#ababab"
                    img-height="600"
                    @sliding-start="onSlideStart"
                    @sliding-end="onSlideEnd">
            <b-carousel-slide>
                <template #img>
                    <a href=#>
                        <div style="background: black;">
                            <div class="d-block img-fluid w-100 img img-1"></div>
                        </div>
                        <div class="content">
                            <h2>Подготовка спрайтов для анимации в Unity</h2>
                            <p>Спрайты должны немного отличаться друг от друга, чтобы было заметно движение.</p>
                        </div>
                    </a>
                </template>
            </b-carousel-slide>
            <b-carousel-slide img-src="../assets/images/slide_2.jpg">
                <template #img>
                    <a href=#>
                        <div style="background: black;">
                            <div class="d-block img-fluid w-100 img img-2"></div>
                        </div>
                        <div class="content">
                            <h2>Подготовка спрайтов для анимации в Unity</h2>
                            <p>Спрайты должны немного отличаться друг от друга, чтобы было заметно движение.</p>
                        </div>
                    </a>
                </template>
            </b-carousel-slide>
            <b-carousel-slide img-src="../assets/images/slide_3.jpg">
                <template #img>
                    <a href=#>
                        <div style="background: black;">
                            <div class="d-block img-fluid w-100 img img-3"></div>
                        </div>
                        <div class="content">
                            <h2>Подготовка спрайтов для анимации в Unity</h2>
                            <p>Спрайты должны немного отличаться друг от друга, чтобы было заметно движение.</p>
                        </div>
                    </a>
                </template>
            </b-carousel-slide>
        </b-carousel>
        <div class="arrows">
            <div class="arrowLeft"
                 @click="prev">
                <svg xmlns="http://www.w3.org/2000/svg"
                     width="31.495"
                     height="22.141"
                     viewBox="0 0 31.495 22.141">
                    <path id="left-arrow"
                          d="M21.22,5.009A1.117,1.117,0,1,0,19.633,6.58l8.047,8.047H1.126A1.118,1.118,0,0,0,0,15.738a1.131,1.131,0,0,0,1.127,1.127H27.68L19.633,24.9a1.139,1.139,0,0,0,0,1.587,1.112,1.112,0,0,0,1.587,0l9.952-9.952a1.12,1.12,0,0,0,0-1.571Z"
                          transform="translate(0.001 -4.676)"
                          fill="currentColor" />
                </svg>
            </div>
            <div class="arrowRight"
                 @click="next">
                <svg xmlns="http://www.w3.org/2000/svg"
                     width="31.495"
                     height="22.141"
                     viewBox="0 0 31.495 22.141">
                    <path id="left-arrow"
                          d="M21.22,5.009A1.117,1.117,0,1,0,19.633,6.58l8.047,8.047H1.126A1.118,1.118,0,0,0,0,15.738a1.131,1.131,0,0,0,1.127,1.127H27.68L19.633,24.9a1.139,1.139,0,0,0,0,1.587,1.112,1.112,0,0,0,1.587,0l9.952-9.952a1.12,1.12,0,0,0,0-1.571Z"
                          transform="translate(0.001 -4.676)"
                          fill="currentColor" />
                </svg>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Slider',
        data() {
            return {
                slide: 0,
                sliding: null,
            };
        },
        methods: {
            onSlideStart() {
                this.sliding = true;
            },
            onSlideEnd() {
                this.sliding = false;
            },
            prev() {
                this.$refs.slider.prev();
            },
            next() {
                this.$refs.slider.next();
            },
        },
    };
</script>
<style lang="scss" scoped>
    .img {
        height: 600px;
        background-position: center center;
        background-size: cover;

        @include respond-to(sm) {
            height: 240px;
        }
    }

    .img-1 {
        background-image: url('../assets/images/slide_1.jpg');
        opacity: 0.56;
    }

    .img-2 {
        background-image: url('../assets/images/slide_2.jpg');
        opacity: 0.56;
    }

    .img-3 {
        background-image: url('../assets/images/slide_3.jpg');
        opacity: 0.56;
    }

    .content {
        position: absolute;
        top: 176px;
        left: 50%;
        transform: translateX(-50%);
        width: 1110px;

        @include respond-to(sm) {
            top: 67px;
            width: 100%;
            left: 53%;
        }

        h2 {
            font-size: 46px;
            line-height: 54px;
            font-weight: 600;
            color: $white;
            text-transform: uppercase;
            max-width: 766px;
            margin-bottom: 19px;

            @include respond-to(sm) {
                max-width: 266px;
                font-size: 16px;
                line-height: 20px;
                margin-bottom: 10px;
            }
        }

        p {
            text-align: left;
            font-size: 24px;
            line-height: 30px;
            letter-spacing: 0px;
            color: $white;
            opacity: 1;
            margin: 0;
            max-width: 659px;

            @include respond-to(sm) {
                font-size: 14px;
                line-height: 18px;
                max-width: 290px;
            }
        }
    }

    .wrapper {
        position: relative;
        margin-top: 142px;

        @include respond-to(sm) {
            margin-top: 44px;
        }
    }

    .arrows {
        position: absolute;
        bottom: 51px;
        left: 50%;
        transform: translateX(-50%);
        width: 1110px;
        display: flex;
        justify-content: space-between;

        @include respond-to(sm) {
            width: 93%;
            bottom: 15px;
            left: 50%;
        }

        .arrowLeft svg,
        .arrowRight svg {
            @include respond-to(sm) {
                width: 18px;
                height: 13px;
            }
        }
    }

    .arrowLeft {
        color: $white;
        transform: rotate(180deg);
        cursor: pointer;
    }

    .arrowRight {
        cursor: pointer;
        color: $white;
    }
</style>

<style lang="scss">
    .wrapper {
        position: relative;

        .carousel-indicators {
            margin-bottom: 11px;
        }

        .carousel-indicators li {
            width: 70px;
            margin-right: 15px;
            margin-left: 15px;
            background-color: $milk;
            opacity: 1;

            &.active {
                background-color: $skyblue;
            }

            @include respond-to(sm) {
                width: 30px;
                margin-right: 6px;
                margin-left: 6px;
                height: 2px;
            }
        }
    }
</style>