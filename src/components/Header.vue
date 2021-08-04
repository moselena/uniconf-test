<template>
    <div>
        <div class="wrapper"
             @mouseleave="onMouseOut">
            <div class="topMenu">
                <b-container>
                    <b-row>
                        <b-col>
                            <div class="topWrapper">
                                <a class="linkTop"
                                   href="#">
                                    Режим работы
                                </a>
                                <a class="linkTop"
                                   href="#">
                                    Правила посещения
                                </a>
                            </div>
                        </b-col>
                    </b-row>
                </b-container>
            </div>
            <div class="menu">
                <b-container>
                    <b-row>
                        <b-col>
                            <div class="head">
                                <a class="logo"
                                   href="#">
                                    LOGOTYPE
                                </a>
                                <nav class="menuLinkWrapper">
                                    <div class="linkWrapper"
                                         v-for="({text, link}, index) in menuItems"
                                         :key="index">
                                        <a class="link"
                                           :href="link"
                                           @mouseover="() => onMouseOver(index)">
                                            {{ text }}</a>
                                    </div>
                                </nav>
                                <div class="actions">
                                    <a href="#"
                                       class="linkBold">
                                        Регистрация
                                    </a>
                                    <a href="#"
                                       class="linkBold">
                                        Вход
                                    </a>
                                </div>
                            </div>
                        </b-col>
                    </b-row>
                </b-container>
            </div>
            <div class="subMenuContainer"
                 :class="{ subMenuContainerOpen: showSubmenu }">
                <div class="subMenu">
                    <b-container>
                        <b-row>
                            <b-col>
                                <div class="menuLinkWrapper">
                                    <div :style="{width: widthResize}" />
                                    <div style="max-width: 450px">
                                        <a v-for="{text, link} in activeSubMenu"
                                           :key="text"
                                           class="subMenuLink"
                                           :href="link">
                                            {{ text }}
                                        </a>
                                    </div>
                                </div>
                            </b-col>
                        </b-row>
                    </b-container>
                </div>
            </div>
        </div>
        <div class="mobWrapper">
            <div class="topMenuMob">
                <a class="logo"
                   href="#">
                    LOGOTYPE
                </a>
                <div @click="open">
                    <img src="../assets/images/burger.svg"
                         v-if="!mobMenuOpen">
                    <img src="../assets/images/close.svg"
                         v-else>
                </div>
            </div>
        </div>
        <div :class="{ active: mobMenuOpen}"
             class="mobMenuWrapper">
            <nav class="menuLinkWrapper">
                <div class="linkWrapper"
                     v-for="({text, link}, index) in menuItems"
                     :key="index">
                    <a class="link"
                       :href="link">
                        {{ text }}</a>
                </div>
            </nav>
            <div class="linkMobWrapper">
                <a href="#"
                   class="linkMob bold">
                    Вход
                </a>
                <a href="#"
                   class="linkMob bold">
                    Регистрация
                </a>
                <a class="linkMob"
                   href="#">
                    Режим работы
                </a>
                <a class="linkMob"
                   href="#">
                    Правила посещения
                </a>
            </div>
        </div>
    </div>
</template>
<script>
    export default {
        name: 'Header',
        data() {
            return {
                activeIndex: null,
                showSubmenu: false,
                mobMenuOpen: false,
                activeSubMenu: [],
                menuItems: [
                    {
                        text: 'Меню',
                        link: '#',
                        subMenuItems: [
                            {
                                text: 'Меню',
                                link: '#',
                            },
                            {
                                text: 'Меню',
                                link: '#',
                            },
                            {
                                text: 'Меню',
                                link: '#',
                            },
                            {
                                text: 'Меню',
                                link: '#',
                            },
                            {
                                text: 'Меню',
                                link: '#',
                            },
                            {
                                text: 'Меню',
                                link: '#',
                            },
                            {
                                text: 'Меню',
                                link: '#',
                            },
                        ],
                    },
                    {
                        text: 'Меню',
                        link: '#',
                    },
                    {
                        text: 'Меню',
                        link: '#',
                        subMenuItems: [
                            {
                                text: 'Меню',
                                link: '#',
                            },
                            {
                                text: 'Меню',
                                link: '#',
                            },
                            {
                                text: 'Меню',
                                link: '#',
                            },
                        ],
                    },
                    {
                        text: 'Меню',
                        link: '#',
                        subMenuItems: [{ text: 'Раздел в разработке' }],
                    },
                    {
                        text: 'Меню',
                        link: '#',
                        subMenuItems: [
                            {
                                text: 'Меню',
                                link: '#',
                            },
                            {
                                text: 'Меню',
                                link: '#',
                            },
                        ],
                    },
                    {
                        text: 'Меню',
                        link: '#',
                        subMenuItems: [
                            {
                                text: 'Меню',
                                link: '#',
                            },
                            {
                                text: 'Меню',
                                link: '#',
                            },
                            {
                                text: 'Меню',
                                link: '#',
                            },
                            {
                                text: 'Меню',
                                link: '#',
                            },
                        ],
                    },
                ],
            };
        },
        computed: {
            widthResize() {
                return !this.activeIndex
                    ? '213px'
                    : 213 + 110 * this.activeIndex + 'px';
            },
        },
        methods: {
            onMouseOver(index) {
                if (this.activeIndex !== index) {
                    this.activeIndex = index;
                    if (this.menuItems[index].subMenuItems) {
                        this.showSubmenu = true;
                        this.activeSubMenu = this.menuItems[index].subMenuItems;
                    } else {
                        this.showSubmenu = false;
                        this.activeSubMenu = [];
                    }
                } else {
                    if (this.menuItems[index].subMenuItems) {
                        this.showSubmenu = true;
                    }
                }
            },
            onMouseOut() {
                this.showSubmenu = false;
            },
            open() {
                this.mobMenuOpen = !this.mobMenuOpen;
            },
        },
    };
</script>
<style lang="scss" scoped>
    .wrapper {
        width: 100%;
        position: fixed;
        top: 0;
        right: 0;
        left: 0;
        z-index: 18;
        display: block;

        @include respond-to(sm) {
            display: none;
        }
    }

    .topMenu {
        background-color: $lightgray;
    }

    .topWrapper {
        height: 40px;
        display: flex;
        justify-content: space-between;
        align-items: center;

        .linkTop {
            text-decoration: none;
            font-size: 14px;
            line-height: 18px;
            cursor: pointer;
            color: $black;
            font-weight: normal;

            &:link &:visited &:active {
                color: $black;
            }

            &:hover {
                color: $black;
                opacity: 0.5;
            }
        }
    }

    .menu {
        background-color: $white;
        padding: 46px 0 0;
    }

    .head {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding-bottom: 32px;
    }

    .logo {
        font-size: 20px;
        line-height: 24px;
        color: $black;
        text-decoration: none;
        font-weight: bold;
    }

    .menuLinkWrapper {
        display: flex;
        align-items: center;

        @include respond-to(sm) {
            flex-direction: column;
            padding: 38px 0 0;
        }

        .linkWrapper {
            width: 110px;

            @include respond-to(sm) {
                margin-bottom: 25px;
                width: 100%;
                display: flex;
                justify-content: center;
            }

            .link {
                color: $black;
                font-weight: normal;
                font-size: 16px;
                line-height: 19px;
                display: inline;
                position: relative;
                cursor: pointer;

                &:last-child {
                    margin-right: 0;
                }

                &:hover {
                    font-weight: bold;
                    color: $black;
                }

                &::after {
                    content: '';
                    position: absolute;
                    right: 0;
                    width: 0;
                    bottom: -5px;
                    background: #000;
                    height: 4px;
                    transition-property: width;
                    transition-duration: 0.3s;
                    transition-timing-function: ease-out;
                }
                &:hover:after,
                &:active:after {
                    left: 0;
                    right: auto;
                    width: 100%;
                }
            }
        }
    }

    .actions {
        display: flex;

        a:first-child {
            margin-right: 25px;
        }
    }

    .linkBold {
        font-weight: 600;
        font-size: 12px;
        line-height: 15px;
        color: $black;

        &:hover {
            opacity: 0.5;
        }
    }

    .subMenuContainer {
        position: absolute;
        width: 100%;
        transition: 0.3s;
        overflow: hidden;
        height: 0;

        &.subMenuContainerOpen {
            height: 100%;
        }
    }

    .subMenu {
        padding: 36px 0 33px;
        background-color: $white;
        border-top: 1px solid $lightasphalt;

        .subMenuLink {
            color: $black;
            font-weight: normal;
            font-size: 14px;
            line-height: 18px;
            margin-right: 40px;
        }
    }

    .mobWrapper {
        display: none;

        @include respond-to(sm) {
            position: fixed;
            width: 100%;
            top: 0;
            left: 0;
            right: 0;
            z-index: 18;
            padding: 20px 15px 24px;
            display: flex;
            flex-direction: column;
            background-color: $white;
        }
    }

    .topMenuMob {
        display: flex;
        justify-content: space-between;
    }

    .mobMenuWrapper {
        background-color: $white;
        position: fixed;
        top: 44px;
        left: -100%;
        bottom: 0;
        right: 0;
        width: 100%;
        z-index: 18;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        text-align: center;
        transition: 0.3s;
    }

    .active {
        left: 0;
    }

    .linkMobWrapper {
        display: flex;
        flex-direction: column;
    }

    .linkMob {
        font-size: 14px;
        line-height: 18px;
        color: $black;
        margin-bottom: 10px;

        &:nth-child(2) {
            margin-bottom: 40px;
        }

        &:nth-child(4) {
            margin-bottom: 20px;
        }
    }

    .bold {
        font-weight: 600;
    }
</style>