<template>
    <div class="wrapper">
        <b-container>
            <b-row>
                <b-col xs="12"
                       sm="6">
                    <a href=#>
                        <h3 class="heading">
                            о&nbsp;компании
                        </h3>
                    </a>
                </b-col>
                <b-col xs="12"
                       sm="6">
                    <p class="text">
                        Что-то более продвинутое делается с помощью покадровой анимации —
                        когда для разных состояний объекта (стоит, идет, в прыжке, атакует)
                        создается несколько спрайтов (двумерное изображение), которые
                        сменяют друг друга с определенным интервалом.
                    </p>
                    <div class="buttonWrapper">
                        <button type="button"
                                class="btn">
                            подробнее
                            <img src="../assets/images/left-arrow.svg"
                                 class="arrow">
                        </button>
                    </div>
                </b-col>
            </b-row>
            <b-row>
                <b-col>
                    <div class="news">
                        <div class="headingWrapper">
                            <a href=#>
                                <h3 class="heading">
                                    Новости
                                </h3>
                            </a>
                            <a href=#
                               class="allNews">
                                Все новости
                            </a>
                        </div>
                        <b-row>
                            <b-col xs="12"
                                   sm="6"
                                   order="2"
                                   order-sm="1">
                                <div style="background: black;">
                                    <div class="img first" />
                                    <p class="number">1</p>
                                </div>
                            </b-col>
                            <b-col xs="12"
                                   sm="6"
                                   order="1"
                                   order-xs="2">
                                <div style="background: black;">
                                    <div class="img second" />
                                    <p class="number">2</p>
                                </div>
                            </b-col>
                        </b-row>
                        <b-row>
                            <b-col>
                                <div style="background: black;">
                                    <div class="img third" />
                                    <p class="number">3</p>
                                </div>
                            </b-col>
                        </b-row>
                        <div v-if="showMore">
                            <b-row>
                                <b-col xs="12"
                                       sm="6"
                                       order="1"
                                       order-sm="1">
                                    <div style="background: black;">
                                        <div class="img first" />
                                        <p class="number">4</p>
                                    </div>
                                </b-col>
                                <b-col xs="12"
                                       sm="6"
                                       order="2"
                                       order-xs="2">
                                    <div style="background: black;">
                                        <div class="img second" />
                                        <p class="number">5</p>
                                    </div>
                                </b-col>
                            </b-row>
                            <b-row>
                                <b-col>
                                    <div style="background: black;">
                                        <div class="img third" />
                                        <p class="number">6</p>
                                    </div>
                                </b-col>
                            </b-row>
                        </div>
                    </div>
                </b-col>
            </b-row>
            <b-row>
                <b-col>
                    <div class="centerer">
                        <button type="button"
                                class="btn"
                                @click="add">
                            {{ text }}
                        </button>
                    </div>
                </b-col>
            </b-row>
        </b-container>
    </div>
</template>
<script>
    export default {
        name: 'Main',
        data() {
            return {
                showMore: false,
            };
        },
        computed: {
            text() {
                return this.showMore ? 'скрыть' : 'показать еще';
            },
        },
        methods: {
            add() {
                this.showMore = !this.showMore;
            },
        },
    };
</script>
<style lang="scss" scoped>
    .wrapper {
        padding-top: 70px;

        @include respond-to(sm) {
            padding-top: 20px;
        }
    }

    .heading {
        text-transform: uppercase;
        font-size: 32px;
        line-height: 39px;
        color: $black;
        font-weight: bold;
        margin-bottom: 0;

        @include respond-to(sm) {
            margin-bottom: 10px;
            font-size: 16px;
            line-height: 19px;
            width: 100%;
            text-align: center;
        }
    }

    .text {
        font-size: 16px;
        line-height: 26px;
        color: $black;
        font-weight: normal;
        margin-bottom: 50px;

        @include respond-to(sm) {
            font-size: 10px;
            line-height: 13px;
            margin-bottom: 0;
        }
    }

    .buttonWrapper {
        display: flex;
        align-items: center;
        margin-top: 20px;
    }

    .btn {
        background: none;
        border: none;
        padding: 0;
        text-transform: uppercase;
        font-size: 14px;
        line-height: 18px;
        color: $black;
        font-weight: 600;

        &:focus {
            outline: none;
            box-shadow: none;
        }

        @include respond-to(sm) {
            font-size: 10px;
            line-height: 13px;
            width: 100%;
            text-align: center;
        }
    }

    .arrow {
        color: $black;
        width: 18px;
        height: 13px;
        margin-left: 16px;

        @include respond-to(sm) {
            margin-left: 6px;
        }
    }

    .news {
        display: flex;
        flex-direction: column;
        padding-top: 80px;

        @include respond-to(sm) {
            padding-top: 30px;
        }
    }

    .headingWrapper {
        display: flex;
        justify-content: space-between;
        padding-bottom: 30px;

        @include respond-to(sm) {
            padding-bottom: 10px;
            justify-content: center;
        }
    }

    .allNews {
        @extend .text;
        padding-top: 20px;
        margin-bottom: 0;

        @include respond-to(sm) {
            display: none;
        }
    }

    .img {
        position: relative;
        background-position: center center;
        background-size: cover;
        height: 300px;
        margin-bottom: 30px;
        padding-top: 63px;
        opacity: 0.46;

        @include respond-to(sm) {
            height: 200px;
            margin-bottom: 20px;
        }
    }

    .number {
        position: absolute;
        top: 40px;
        left: 50%;
        transform: translateX(-50%);
        color: rgba(247, 247, 247, 0.6);
        font-size: 161px;
        line-height: 196px;
        font-weight: bold;

        @include respond-to(sm) {
            font-size: 95px;
            line-height: 116px;
        }
    }

    .first {
        background-image: url('../assets/images/img_1.jpg');
    }

    .second {
        background-image: url('../assets/images/img_2.jpg');
    }

    .third {
        background-image: url('../assets/images/img_3.jpg');
    }

    .centerer {
        display: flex;
        padding: 50px 0 0;
        justify-content: center;

        @include respond-to(sm) {
            padding: 0;
        }
    }
</style>