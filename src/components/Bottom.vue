<template>
    <div class="wrapper">
        <b-container>
            <b-row>
                <b-col>
                    <div class="head">
                        <p class="text"
                           href="#">
                            &copy; ООО «Глобус», 2016 — 2019
                        </p>
                        <div class="docs">
                            <a href="#"
                               class="link">
                                Политика конфиденциальности
                            </a>
                            <a href="#"
                               class="link">
                                Cookies
                            </a>
                        </div>
                    </div>
                </b-col>
            </b-row>
        </b-container>
    </div>
</template>
<script>
    export default {
        name: 'Bottom',
    };
</script>
<style lang="scss" scoped>
    .wrapper {
        background-color: $darkblue;
    }

    .head {
        height: 60px;
        display: flex;
        justify-content: space-between;
        align-items: center;

        .text {
            font-size: 12px;
            line-height: 15px;
            color: $lightgray;
            font-weight: normal;
            margin: 0;

            @include respond-to(sm) {
                display: none;
            }
        }

        .docs {
            display: flex;

            a:first-child {
                margin-right: 30px;
            }
            @include respond-to(sm) {
                width: 100%;
                justify-content: space-between;
            }
        }

        .link {
            text-decoration: none;
            font-size: 12px;
            line-height: 15px;
            cursor: pointer;
            color: $lightgray;
            font-weight: normal;

            &:link &:visited &:active {
                color: $lightgray;
            }

            &:hover {
                color: $white;
                opacity: 0.5;
            }
        }
    }
</style>