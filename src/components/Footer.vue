<template>
    <div class="wrapper">
        <b-container>
            <b-row>
                <b-col xs="12"
                       sm="3">
                    <div class="left">
                        <a class="logo"
                           href="#">
                            LOGOTYPE
                        </a>
                        <p class="text adress">
                            г. Москва, метро Бауманская, ул. Бауманская, дом 44
                        </p>
                        <a class="phone"
                           href="tel:+7 000 000 00 00">+7 000 000 00 00</a>
                    </div>
                </b-col>
                <b-col xs="12"
                       sm="9">
                    <div class="right">
                        <div class="hide" />
                        <nav class="linkWrapper">
                            <a v-for="{text, link} in menuItems"
                               :key="text"
                               :to="link"
                               class="link">
                                {{ text }}
                            </a>
                        </nav>
                        <div class="socialWrapper">
                            <div class="social">
                                <p class="text">
                                    Мы в соц. сетях
                                </p>
                                <div class="svgWrapper">
                                    <a href="https://www.facebook.com/"><img src="../assets/images/facebook-letter-logo.svg"
                                             class="svg"></a>
                                    <a href="https://ok.ru/"><img src="../assets/images/odnoklassniki.svg"
                                             class="svg"></a>
                                    <a href="https://www.instagram.com/"><img src="../assets/images/instagram-logo.svg"></a>
                                </div>
                            </div>
                            <div class="subscription">
                                <p class="text textIndents">
                                    Подписка на новости
                                </p>
                                <b-form class="form">
                                    <b-form-input class="input"
                                                  id="input"
                                                  type="email"
                                                  placeholder="example@mail.com"
                                                  required></b-form-input>
                                    <button type="submit"
                                            class="btn">Ok</button>
                                </b-form>
                            </div>
                        </div>
                    </div>
                </b-col>
            </b-row>
        </b-container>
    </div>
</template>
<script>
    export default {
        name: 'Footer',
        data() {
            return {
                menuItems: [
                    {
                        text: 'О компании',
                        link: '#',
                    },
                    {
                        text: 'Партнёрская программа',
                        link: '#',
                    },
                    {
                        text: 'Реклама',
                        link: '#',
                    },
                    {
                        text: 'Пресс-центр',
                        link: '#',
                    },
                    {
                        text: 'Вакансии',
                        link: '#',
                    },
                    {
                        text: 'Помощь',
                        link: '#',
                    },
                    {
                        text: 'Правила',
                        link: '#',
                    },
                ],
            };
        },
    };
</script>
<style lang="scss" scoped>
    .wrapper {
        padding: 46px 0 32px;
        background-color: $lightgray;

        @include respond-to(sm) {
            padding: 20px 0 36px;
            text-align: center;
        }
    }

    .left {
        display: flex;
        flex-direction: column;
    }

    .logo {
        font-size: 20px;
        line-height: 24px;
        color: $black;
        text-decoration: none;
        font-weight: bold;
    }

    .linkWrapper {
        display: flex;
        margin-top: 20px;

        .link {
            color: $black;
            font-weight: normal;
            font-size: 14px;
            line-height: 18px;
            margin-right: 24px;
            cursor: pointer;

            &:hover {
                opacity: 0.5;
            }

            &:last-child {
                margin-right: 0;
            }

            @include respond-to(sm) {
                margin-right: 0;
                margin-bottom: 8px;
            }
        }

        @include respond-to(sm) {
            flex-direction: column;
            margin-top: 26px;
        }
    }

    .adress {
        margin-top: 20px;
        max-width: 217px;

        @include respond-to(sm) {
            margin: 10px auto 0;
        }
    }

    .socialWrapper {
        display: flex;
        justify-content: space-between;
        margin-top: 37px;

        @include respond-to(sm) {
            margin-top: 31px;
            flex-direction: column;
        }
    }

    .form {
        display: flex;
    }

    .social {
        display: flex;
        flex-direction: column;
    }

    .subscription {
        display: flex;
        flex-direction: column;
    }

    .phone {
        color: $black;
        margin-top: 60px;
        font-weight: 600;
        font-size: 14px;
        line-height: 18px;

        @include respond-to(sm) {
            margin-top: 20px;
        }
    }

    .text {
        color: $black;
        font-weight: normal;
        font-size: 14px;
        line-height: 18px;
        margin-bottom: 0;
    }

    .right {
        padding-left: 97px;

        @include respond-to(sm) {
            padding-left: 0;
        }
    }

    .hide {
        height: 24px;

        @include respond-to(sm) {
            display: none;
        }
    }

    .textIndents {
        margin-bottom: 10px;

        @include respond-to(sm) {
            margin-bottom: 15px;
        }
    }

    .input {
        width: 289px;
        height: 32px;
        margin-right: 11px;
    }

    .btn {
        background-color: $skyblue;
        color: $white;
        border-radius: 2px;
        font-size: 14px;
        width: 70px;
        height: 30px;
        margin: auto;

        &:hover {
            color: $white;
            opacity: 0.5;
        }

        &:focus {
            box-shadow: none;
        }
    }

    .svgWrapper {
        height: 13px;
        align-items: center;
        margin-top: 16px;

        @include respond-to(sm) {
            margin-top: 19px;
            margin-bottom: 39px;
        }
    }

    .svg {
        margin-right: 12px;
    }
</style>