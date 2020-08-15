<template>
  <div class="container">
    <div class="frame">
      <form action="" @submit.prevent="registerUser" novalidate>
        <transition name="slide-fade">
          <div v-show="step === 1" class="step">
            <h1 class="frame__title">
              Регистрация
            </h1>
            <div class="form">
              <div class="form__left">

                <div class="form__group" :class="{ 'form-group--error': $v.formReg.surname.$error }">
                  <label class="form__label" for="surname"><span class="form__name">Фамилия</span></label>
                  <input class="form__input" type="text" id="surname" 
                  @blur="$v.formReg.surname.$touch()"
                  v-model="formReg.surname">
                  
                  <div class="error" v-if="!$v.formReg.surname.required">Поле обязательно для заполнения</div>
                  <div class="error" v-if="!$v.formReg.surname.alpha">Фамилия не может содержать цифры или символы</div>
                </div>

                <div class="form__group" :class="{ 'form-group--error': $v.formReg.name.$error }">
                  <label class="form__label" for="name"><span class="form__name">Имя</span></label>
                  <input class="form__input" type="text" id="name"
                  @blur="$v.formReg.name.$touch()"
                  v-model="formReg.name">
                  <div class="error" v-if="!$v.formReg.name.required">Поле обязательно для заполнения</div>
                  <div class="error" v-if="!$v.formReg.name.alpha">Имя не может содержать цифры или символы</div>
                </div>

                <div class="form__group">
                  <label class="form__label" for="father">Отчество</label>
                  <input class="form__input" type="text" id="father">
                </div>

                <div class="form__group" :class="{ 'form-group--error': $v.formReg.birth.$error }">
                  <label class="form__label " for="birth"><span class="form__name">Дата рождения</span></label>
                  <input class="form__input form__date" type="date" id="birth" 
                  @blur="$v.formReg.birth.$touch()"
                  v-model="formReg.birth">

                  <div class="error" v-if="!$v.formReg.birth.required">Поле обязательно для заполнения</div>
                </div>

                <div class="form__group" :class="{ 'form-group--error': $v.formReg.tel.$error }">
                  <label class="form__label" for="tel"><span class="form__name">Номер телефона</span></label>
                  <input class="form__input" type="tel" id="tel" 
                  @blur="$v.formReg.tel.$touch()"
                  v-model="formReg.tel">
                  <div class="error" v-if="!$v.formReg.tel.required">Поле обязательно для заполнения</div>
                  <div class="error" v-if="!$v.formReg.tel.numeric">Неверный формат номера телефона</div>
                  <div class="error" v-if="!$v.formReg.tel.minLength">Неверный формат номера телефона</div>
                  <div class="error" v-if="!$v.formReg.tel.maxLength">Неверный формат номера телефона</div>
                  <div class="error error-tel" v-if="!(formReg.tel[0] === '7')">Номер должен начинаться с 7</div>
                </div>

                <div class="form__group">
                  <label class="form__label" for="sex">Пол</label>
                  <select class="form__input form__select" name="" id="sex">
                    <option class="form__option" disabled></option>
                    <option class="form__option">Мужской</option>
                    <option class="form__option">Женский</option>
                  </select>
                </div>

                <div class="form__group">
                  <label class="form__label form__checkTitle" for=""><span class="form__name">Группа клиентов</span></label>
                  <div class="multiselect">
                    <label class="check" for="vip" >
                      <input id="vip" class="form__input check__main" value="vip" type="checkbox" v-model="checkedNames">
                      <span class="check__box"></span>
                      VIP
                    </label>
                    <label class="check" for="prob">
                      <input id="prob" class="form__input check__main" value="prob" type="checkbox" v-model="checkedNames">
                      <span class="check__box"></span>
                      Проблемные
                    </label>
                    <label class="check" for="oms">
                      <input id="oms" class="form__input check__main" value="oms" type="checkbox" v-model="checkedNames">
                      <span class="check__box"></span>
                      ОМС
                    </label>
                    <div class="error" v-if="(!checkedNames[0])">Поле обязательно для заполнения</div>
                  </div>
                </div>

                <div class="form__group">
                  <label class="form__label" for="doctor">Лечащий врач</label>
                  <select class="form__input form__select" name="doctor" id="">
                    <option class="form__option" value="" selected disabled></option>
                    <option class="form__option" value="">Иванов</option>
                    <option class="form__option" value="">Захаров</option>
                    <option class="form__option" value="">Чернышева</option>
                  </select>
                </div>

                <div class="form__group">
                  <label class="form__label form__checkTitle" for="">СМС оповещение</label>
                  <div class="multiselect">
                    <label class="check" for="sms">
                      <input id="sms" class="form__input check__main" type="checkbox">
                      <span class="check__box"></span>
                      Не отправлять СМС
                    </label>
                  </div>
                </div>

              </div> <!-- FORM__LEFT -->
              <div class="form__right">

                <div class="form__group">
                  <label class="form__label" for="index">Индекс</label>
                  <input class="form__input" type="text" id="index">
                </div>

                <div class="form__group">
                  <label class="form__label" for="country">Страна</label>
                  <input class="form__input" type="text" id="country">
                </div>

                <div class="form__group">
                  <label class="form__label" for="region">Область</label>
                  <input class="form__input" type="text" id="region">
                </div>

                <div class="form__group" :class="{ 'form-group--error': $v.formReg.city.$error }">
                  <label class="form__label" for="city"><span class="form__name">Город</span></label>
                  <input class="form__input" type="text" id="city"
                  @blur="$v.formReg.city.$touch()"
                  v-model="formReg.city">

                  <div class="error" v-if="!$v.formReg.city.required">Поле обязательно для заполнения</div>
                  <div class="error" v-if="!$v.formReg.city.alpha">Название города не может содержать цифры или символы</div>
                </div>

                <div class="form__group">
                  <label class="form__label" for="street">Улица</label>
                  <input class="form__input" type="text" id="street">
                </div>

                <div class="form__group">
                  <label class="form__label" for="home">Дом</label>
                  <input class="form__input" type="text" id="home">
                </div>

              </div> <!-- FORM__RIGHT -->
            </div> <!-- FORM DIV -->
            <button @click="nextStep" :disabled="disabledBtn" class="btn" type="button">Далее</button>
            <h1 class="frame__req">
            *Поле обязательное для заполнения
            </h1>
          </div> <!-- STEP -->
        </transition>

        <transition name="slide-fade">
          <div v-show="step === 2" class="step">
            <h1 class="frame__title">
              Паспорт
            </h1>

            <div class="form">
              <div class="form__left">

                <div class="form__group">
                  <label class="form__label" for=""><span class="form__name">Тип документа</span></label>
                  <select class="form__input form__select" name="" id="" v-model="selected">
                    <option class="form__option" selected disabled></option>
                    <option class="form__option" value="passport">Паспорт</option>
                    <option class="form__option" value="birth">Свидетельство о рождении</option>
                    <option class="form__option" value="drive">Вод. удостоверение</option>
                  </select>

                  <div class="error" v-if="!selected">Поле обязательно для заполнения</div>
                </div>

                <div class="form__group">
                  <label class="form__label" for="series">Серия</label>
                  <input class="form__input" type="text" id="series">
                </div>

                <div class="form__group">
                  <label class="form__label" for="number">Номер</label>
                  <input class="form__input" type="text" id="number">
                </div>
              </div> <!-- FORM__LEFT -->

              <div class="form__right">

                <div class="form__group">
                  <label class="form__label" for="given">Кем выдан</label>
                  <input class="form__input" type="text" id="given">
                </div>

                <div class="form__group" :class="{ 'form-group--error': $v.formReg.givenDate.$error }">
                  <label class="form__label " for="givenDate"><span class="form__name">Дата выдачи</span></label>
                  <input class="form__input form__date" type="date" id="givenDate"
                  @blur="$v.formReg.givenDate.$touch()"
                  v-model="formReg.givenDate">

                  <div class="error" v-if="!$v.formReg.givenDate.required">Поле обязательно для заполнения</div>
                </div>

              </div>
            </div>
            <button @click="backStep" class="btn" type="button">Назад</button>
            <button class="btn" type="submit" :disabled="disabledSend">Отправить</button>
            <h1 class="frame__req">
            *Поле обязательное для заполнения
            </h1>
          </div> <!-- STEP -->
        </transition>
      </form>
    </div> <!-- FRAME -->

    <transition name="slide-fade">
    <div class="registered" v-if="registered">
      <div class="registered__box">
        <h1 class="registered__text">
          Поздравляем! <br>
          Вы успешно зарегистрированы!
        </h1>
        <div class="close" @click="close">X</div>
      </div>
    </div>
    </transition>
  </div> <!-- CONTAINER -->
</template>



<script>
import { required, helpers, numeric, minLength, maxLength } from 'vuelidate/lib/validators'
const alpha = helpers.regex('alpha', /^[a-zA-Zа-яёА-ЯЁ]*$/)

export default {
  data() {
    return {
      checkedNames: [],
      selected: '',
      registered: false,
      step: 1,
      formReg: {
        surname: '',
        name: '',
        birth: '',
        tel: '',
        city: '',
        givenDate: '',
        selected: ''
      }
    }
  },
  computed: {
    disabledBtn() {
      return this.$v.formReg.surname.$invalid ||
             this.$v.formReg.name.$invalid ||
             this.$v.formReg.tel.$invalid ||
             this.$v.formReg.city.$invalid ||
             this.$v.formReg.birth.$invalid ||
             !this.checkedNames[0]
    },
    disabledSend() {
      return this.$v.formReg.givenDate.$invalid ||
             !this.selected
    }
  },
  methods: {
    nextStep() {
      this.step ++
    },
    backStep() {
      this.step --
    },
    registerUser() {
      console.log('Пользователь зарегистрирован');
      this.registered = true;
    },
    close() {
      this.registered = false;
    }
  },
  validations: {
    formReg: {
        surname: {
          required,
          alpha
        },
        name: {
          required,
          alpha
        },
        birth: {
          required
        },
        tel: {
          required,
          numeric,
          minLength: minLength(11),
          maxLength: maxLength(11)
        },
        city: {
          required,
          alpha
        },
        givenDate: {
          required
        },
        selected: {

        }
      }
  },
}
</script>

<style lang='scss'>
*,
*::before,
*::after {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    background-image: url("../assets/1.jpg");
    background-size: cover;
    background-repeat: no-repeat;
    font-family: 'Roboto', sans-serif;
    font-size: 18px;
}

label {
    display: block;
}

.container {
    max-width: 60%;
    min-height: 80vh;
    margin: 0 auto;
    padding-top: 50px;
    padding-bottom: 50px;

    .frame {
        background-color: rgba(0, 0, 0, .4);
        border-radius: 10px;
        padding: 50px;
        color: #ffffff;

        &__title {
            font-weight: 400;
        }

        .form {
            margin-top: 20px;
            display: flex;

            &__date {
                height: 37px;
            }

            &__left {
                width: 50%;
            }
            
            
            &__right {
                width: 50%;
            }


            &__label {
                margin-top: 15px;
            }

            &__name {
                    position: relative;

                    &::before {
                        content: '*';
                        position: absolute;
                        top: 0;
                        left: 100%;
                    }
                }

            &__input {
                width: 80%;
                margin-top: 10px;
                padding: 7px;
                border: none;
                border-radius: 10px;
                font-size: 20px;
                background-color: rgba(255, 255, 255, .3);
                outline: none;
                color: #ffffff;
            }

            .form__select {
                width: 80%;
            }

            &__option {
                color: #000000;
            }

            .check {
                display: inline;
                margin-right: 10px;

                &__box {
                    width: 20px;
                    height: 20px;
                    display: inline-block;
                    background-color: #ffffff;
                    position: relative;

                    &::before {
                        opacity: 0;
                        content: '✔';
                        color: #2629e2;
                        font-size: 23px;
                        position: absolute;
                        top: 50%;
                        left: 50%;
                        transform: translate(-50%, -50%);
                        transition: opacity 0.2s linear;
                    }
                }
            }
        }

        &__req {
            margin-top: 20px;
            font-size: 14px;
        }

    }

    .check__main {
        display: none;
    }

    .check__main:checked ~ .check__box::before {
        opacity: 1;
    }

    .form__checkTitle {
        margin-bottom: 17px;
    }

    .multiselect {
        margin-bottom: 20px;
    }
}

.btn {
  font-size: 20px;
  background-color: #007bff;
  color: #ffffff;
  padding: 10px 20px;
  border: none;
  outline: none;
  border-radius: 5px;
  margin-top: 15px;
  margin-right: 10px;
  cursor: pointer;

  &:hover {
    background-color: hsl(211, 100%, 65%);
  }

  &:disabled {
    background-color: hsl(211, 100%, 75%);
    cursor:default
  }
}

@keyframes shakeError {
  0% {
      transform: translateX(0);
  }

  15% {
      transform: translateX(0.375rem);
  }
  30% {
      transform: translateX(-0.375rem);
  }
  45% {
      transform: translateX(0.375rem);
  }
  60% {
      transform: translateX(-0.375rem);
  }
  75% {
      transform: translateX(0.375rem);
  }
  90% {
      transform: translateX(-0.375rem);
  }
  100% {
      transform: translateX(0);
  }
}

.form-group--error {
  animation-name: shakeError;
  animation-fill-mode: forwards;
  animation-duration: .6s;
  animation-timing-function: ease-in-out;
  color: #d33a1f
}

.form__group {
  position: relative;
  margin-bottom: 25px;
}

.error {
  color: #d33a1f;
  font-size: 13px;
  font-weight: 700;
  position: absolute;

  &-tel {
    top: 117%;
  }
}

.container .frame .form__input {
  border: 2px solid rgba(40, 6, 96, 0)
}

.frame .form-group--error .form__input{
  border: 2px solid #d33a1f;
}

.registered {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  display: flex;
  justify-content: center;
  align-items: center;

  &__box {
    background-color: #ffffff;
    text-align: center;
    padding: 100px;
    position: relative;
    max-width: 80%;

    .close {
      position: absolute;
      right: 5%;
      top: 10%;
      font-weight: 700;
      cursor: pointer;
    }
  }
}

@media screen and (max-width: 1154px) {
    .container {
        max-width: 90%;
    }
}

@media screen and (max-width: 975px) {
    .registered__box {
        padding: 50px;
    }
}

@media screen and (max-width: 768px) {
    .container .frame .form {
        display: block;
    }

    .container .frame .form__left {
        width: 100%;
    }

    .container .frame .form__right {
        width: 100%;
    }

    .container .frame {
      padding: 20px 0;
      text-align: center;
    }

    .error {
      left: 11%;
    }
}

@media screen and (max-width: 570px) {
    .registered .registered__box .registered__text{
        font-size: 20px;
    }
}

@media screen and (max-width: 528px) {
    .registered__box{
        padding: 30px;
    }
}

.slide-fade-enter-active {
  transition: all .3s ease;
}
.slide-fade-enter {
  transform: translateX(10px);
  opacity: 0;
}

</style>