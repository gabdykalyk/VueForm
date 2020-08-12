<template>
    <div class="container">
    <div class="frame">
      <h1 class="frame__title">
        Регистрация
      </h1>
      <form action="" >
        <div class="form">
          <div class="form__left">
            <label class="form__label" for=""><span class="form__name">Фамилия</span></label>
            <input class="form__input" type="text" required>
            <label class="form__label" for=""><span class="form__name">Имя</span></label>
            <input class="form__input" type="text" required>
            <label class="form__label" for="">Отчество</label>
            <input class="form__input" type="text">
            <label class="form__label " for=""><span class="form__name">Дата рождения</span></label>
            <input class="form__input form__date" type="date" required>
            <label class="form__label" for=""><span class="form__name">Номер телефона</span></label>
            <input class="form__input" type="tel" required>
            <label class="form__label" for="">Пол</label>
            <select class="form__input form__select" name="" id="">
              <option class="form__option" value="" selected disabled></option>
              <option class="form__option" value="">Мужской</option>
              <option class="form__option" value="">Женский</option>
            </select>
            <label class="form__label form__checkTitle" for=""><span class="form__name">Группа клиентов</span></label>
            <div class="multiselect">
              <label class="check" for="vip" >
                <input id="vip" class="form__input check__main" type="checkbox" required>
                <span class="check__box"></span>
                VIP
              </label>
              <label class="check" for="prob">
                <input id="prob" class="form__input check__main" type="checkbox" required>
                <span class="check__box"></span>
                Проблемные
              </label>
              <label class="check" for="oms">
                <input id="oms" class="form__input check__main" type="checkbox" required>
                <span class="check__box"></span>
                ОМС
              </label>
            </div>
            <label class="form__label" for="">Лечащий врач</label>
            <select class="form__input form__select" name="" id="">
              <option class="form__option" value="" selected disabled></option>
              <option class="form__option" value="">Иванов</option>
              <option class="form__option" value="">Захаров</option>
              <option class="form__option" value="">Чернышева</option>
            </select>
            <label class="form__label form__checkTitle" for="">СМС оповещение</label>
            <div class="multiselect">
              <label class="check" for="sms">
                <input id="sms" class="form__input check__main" type="checkbox" required>
                <span class="check__box"></span>
                Не отправлять СМС
              </label>
            </div>

          </div>
          <div class="form__right">
            <label class="form__label" for="">Индекс</label>
            <input class="form__input" type="text">
            <label class="form__label" for="">Страна</label>
            <input class="form__input" type="text">
            <label class="form__label" for="">Область</label>
            <input class="form__input" type="text">
            <label class="form__label" for=""><span class="form__name">Город</span></label>
            <input class="form__input" type="text" required>
            <label class="form__label" for="">Улица</label>
            <input class="form__input" type="text">
            <label class="form__label" for="">Дом</label>
            <input class="form__input" type="text">
          </div>
        </div>
        <h1 class="frame__title">
          Паспорт
        </h1>
        <div class="form">
          <div class="form__left">
            <label class="form__label" for=""><span class="form__name">Тип документа</span></label>
            <select class="form__input form__select" name="" id="" required>
              <option class="form__option" value="" selected disabled></option>
              <option class="form__option" value="">Паспорт</option>
              <option class="form__option" value="">Свидетельство о рождении</option>
              <option class="form__option" value="">Вод. удостоверение</option>
            </select>
            <label class="form__label" for="">Серия</label>
            <input class="form__input" type="text">
            <label class="form__label" for="">Номер</label>
            <input class="form__input" type="text">
          </div>
          <div class="form__right">
            <label class="form__label" for="">Кем выдан</label>
            <input class="form__input" type="text">
            <label class="form__label " for=""><span class="form__name">Дата выдачи</span></label>
            <input class="form__input form__date" type="date" required>
          </div>
        </div>
        <button>Отправить</button>
      </form>
      <h1 class="frame__req">
        *Поле обязательное для заполнения
      </h1>
    </div>
    
  </div>
</template>

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

@media screen and (max-width: 1154px) {
    .container {
        max-width: 90%;
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
}

</style>