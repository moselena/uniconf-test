<template>
    <b-container>
        <div v-if="firstStep"
             class="wrapperFirstStep">
            <div class="block" />
            <div class="img">
                <svg xmlns="http://www.w3.org/2000/svg"
                     width="21"
                     height="21"
                     viewBox="0 0 21 21">
                    <path id="RSS"
                          d="M4.76,16.233a2.762,2.762,0,0,1,0,3.926h0a2.791,2.791,0,0,1-3.942,0,2.765,2.765,0,0,1,0-3.927h0a2.786,2.786,0,0,1,3.942,0Zm0,0h0ZM.818,20.16h0ZM0,7.141v4.01a9.78,9.78,0,0,1,6.947,2.886A9.8,9.8,0,0,1,9.83,20.993h0V21h4.026a13.826,13.826,0,0,0-4.066-9.792A13.809,13.809,0,0,0,0,7.141ZM.01,0V4.008A17.011,17.011,0,0,1,16.98,21H21A20.945,20.945,0,0,0,14.842,6.161,20.926,20.926,0,0,0,.01,0Z"
                          fill="#14a5da" />
                </svg>
            </div>
            <h4 class="heading">подпишитесь на рассылку</h4>
            <b-form @submit="onSubmit"
                    class="form"
                    :novalidate="true">
                <div class="inputs">
                    <b-form-group id="input-group-1"
                                  class="formGroup"
                                  maxlength="40">
                        <label label="Имя"
                               v-if="!errors.name"
                               label-for="input-1">Имя</label>
                        <div v-if="errors.name"
                             class="error">{{ errors.name }}</div>
                        <b-form-input id="input-1"
                                      v-model="form.name"
                                      placeholder="Введите имя"
                                      @input="() => onChange('name')"
                                      :class="{ inputError: !!errors.name }"></b-form-input>
                    </b-form-group>
                    <b-form-group id="input-group-2"
                                  class="formGroup formGroup_noLabel">
                        <div v-if="errors.email"
                             class="error emailError">{{ errors.email }}</div>
                        <b-form-input id="input-2"
                                      v-model="form.email"
                                      type="email"
                                      placeholder="example@mail.com"
                                      @input="() => onChange('email')"
                                      :class="{ inputError: !!errors.email }"></b-form-input>
                    </b-form-group>
                </div>
                <div v-if="errors.comments"
                     class="error commentsError">{{ errors.comments }}</div>
                <b-form-textarea id="textarea"
                                 class="textarea"
                                 v-model="form.comments"
                                 placeholder="Комментарии"
                                 @input="() => onChange('comments')"
                                 :class="{ textareaError: !!errors.comments }"></b-form-textarea>
                <button type="submit"
                        class="btn">подписаться</button>
            </b-form>
        </div>
        <div v-else
             class="wrapper">
            <svg xmlns="http://www.w3.org/2000/svg"
                 width="61"
                 height="61"
                 viewBox="0 0 61 61">
                <g transform="translate(15.555 19.307)">
                    <path style="fill: #3dcc89;"
                          d="M135.182,135.04l-14.762,15.036-7.564-7.595-4.056,4.057,11.925,11.9,19.154-18.575Z"
                          transform="translate(-108.8 -135.04)" />
                </g>
                <path style="fill: #3dcc89;"
                      d="M30.5,0A30.5,30.5,0,1,0,61,30.5,30.5,30.5,0,0,0,30.5,0Zm0,55.48A24.98,24.98,0,1,1,55.48,30.5,24.98,24.98,0,0,1,30.5,55.48Z" />
            </svg>
            <p class="greetings">Уважаемый, {{ form.name }}, спасибо за подписку!</p>
        </div>
    </b-container>
</template>

<script>
    export default {
        data() {
            return {
                form: {
                    email: '',
                    name: '',
                    comments: '',
                },
                errors: {
                    email: '',
                    name: '',
                    comments: '',
                },
                firstStep: true,
            };
        },
        computed: {
            hasErrors() {
                return (
                    this.errors.name || this.errors.email || this.errors.comments
                );
            },
        },
        methods: {
            onSubmit(event) {
                event.preventDefault();
                Object.keys(this.form).map(key => this.getErrors(key));

                if (this.hasErrors) {
                    return;
                }

                this.firstStep = false;
            },
            onReset(event) {
                event.preventDefault();
                this.form.email = '';
                this.form.name = '';
                this.form.comments = '';
            },
            onChange(name) {
                this.getErrors(name);
            },
            validEmail(email) {
                var re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
                return re.test(String(email).toLowerCase());
            },
            validName(name) {
                let re = /[0-9]+/;
                return re.test(name);
            },
            getNameError() {
                return !this.form.name
                    ? 'Заполните поле'
                    : this.validName(this.form.name)
                    ? 'Цифры в имени недопустимы'
                    : '';
            },
            getEmailError() {
                return !this.form.email
                    ? 'Заполните поле'
                    : !this.validEmail(this.form.email)
                    ? 'Укажите корректный email'
                    : '';
            },
            getCommentError() {
                return !this.form.comments ? 'Заполните поле' : '';
            },
            getErrors(name) {
                switch (name) {
                    case 'name':
                        if (!this.form.name || this.validName(this.form.name)) {
                            this.errors.name = this.getNameError();
                        } else {
                            this.errors.name = '';
                        }
                        break;
                    case 'email':
                        if (!this.form.email || !this.validEmail(this.form.email)) {
                            this.errors.email = this.getEmailError();
                        } else {
                            this.errors.email = '';
                        }
                        break;
                    case 'comments':
                        if (!this.form.comments) {
                            this.errors.comments = this.getCommentError();
                        } else {
                            this.errors.comments = '';
                        }
                        break;
                }
            },
        },
    };
</script>
<style lang="scss" scoped>
    .wrapperFirstStep {
        position: relative;
        border: 1px solid $skyblue;
        margin-top: 77px;
        margin-bottom: 60px;
        padding: 42px 0 33px;
        display: flex;
        align-items: center;
        flex-direction: column;

        @include respond-to(sm) {
            padding: 30px 35px 35px;
            margin-top: 31px;
            margin-bottom: 40px;
        }
    }

    .wrapper {
        margin-top: 77px;
        margin-bottom: 60px;
        padding: 135px 0;
        display: flex;
        align-items: center;
        flex-direction: column;
        box-shadow: 0px 0px 10px $lightasphalt;

        @include respond-to(sm) {
            margin-top: 31px;
            padding: 159px 16px 210px;
        }

        svg {
            @include respond-to(sm) {
                width: 40px;
                height: 40px;
            }
        }
    }

    .heading {
        text-align: center;
        margin-bottom: 27px;
        font-weight: 600;
        font-size: 20px;
        line-height: 24px;

        @include respond-to(sm) {
            font-size: 12px;
            line-height: 15px;
            margin-bottom: 22px;
        }
    }

    .form {
        display: flex;
        justify-content: center;
        flex-direction: column;
        max-width: 570px;
    }

    .block {
        border-radius: 10px;
        padding: 20px;
        position: absolute;
        color: $white;
        top: -20px;
        left: -20px;

        &:after {
            content: '';
            position: absolute;
            border: 40px solid transparent;
            border-left: 40px solid $lightblue;
            border-top: 40px solid $lightblue;
        }

        @include respond-to(sm) {
            &:after {
                border: 24px solid transparent;
                border-left: 24px solid $lightblue;
                border-top: 24px solid $lightblue;
            }
        }
    }

    .img {
        position: absolute;
        top: 11px;
        left: 12px;

        @include respond-to(sm) {
            top: 0;
            left: 7px;
        }

        svg {
            @include respond-to(sm) {
                width: 12px;
                height: 12px;
            }
        }
    }

    .formGroup {
        position: relative;
        margin-bottom: 45px;

        label {
            padding-left: 20px;
            font-size: 12px;
            color: $black;
            margin-bottom: 6px;
        }

        @include respond-to(sm) {
            margin-bottom: 30px;
        }

        &.formGroup_noLabel {
            padding-top: 28px;

            @include respond-to(sm) {
                padding-top: 0;
                margin-bottom: 30px;
            }
        }

        input {
            width: 270px;
            height: 40px;
            font-size: 14px;

            &:focus {
                outline: none;
                box-shadow: none;
                border-color: $skyblue;
                background: $lightblue;
            }

            &.inputError {
                border-color: $error;
            }

            @include respond-to(sm) {
                width: 220px;
            }
        }
    }

    .error {
        color: $error;
        font-size: 12px;
        line-height: 15px;
        margin-bottom: 4px;
        padding-top: 9px;
        padding-left: 20px;

        @include respond-to(sm) {
            padding-top: 0;
        }
    }

    .emailError {
        position: absolute;
        padding-top: 0;
        top: 8px;

        @include respond-to(sm) {
            top: -17px;
        }
    }

    .commentsError {
        position: absolute;
        padding-top: 0;
        top: 188px;

        @include respond-to(sm) {
            top: 209px;
        }
    }

    .inputs {
        display: flex;
        justify-content: space-between;

        @include respond-to(sm) {
            flex-direction: column;
        }
    }

    .textarea {
        width: 570px;
        height: 128px;
        resize: none;
        font-size: 14px;

        &.textareaError {
            border-color: $error;
        }

        &:focus {
            box-shadow: none;
            border-color: $skyblue;
            background: $lightblue;
        }

        @include respond-to(sm) {
            width: 220px;
        }
    }

    .btn {
        background-color: $skyblue;
        color: $white;
        border-radius: 2px;
        font-size: 14px;
        width: 270px;
        height: 40px;
        margin: 20px auto 33px;

        &:hover {
            color: $white;
        }

        &:focus {
            box-shadow: none;
        }

        @include respond-to(sm) {
            width: 220px;
            margin: 20px auto 0;
        }
    }

    .greetings {
        font-size: 20px;
        line-height: 24px;
        text-transform: uppercase;
        font-weight: 600;
        margin-top: 25px;
        text-align: center;

        @include respond-to(sm) {
            font-size: 12px;
            line-height: 15px;
        }
    }
</style>