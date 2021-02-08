<template>
    <form action="#" class="form" @submit.prevent="submit()">
        <div class="form__header">
            <div class="form__title">Регистрация</div>
            <div class="form__discription">Уже есть аккаунт? <a href="#">Войти</a></div>
        </div>
        <div class="form__row-name">
            <v-text-field
            label="Имя"
            placeholder="Введите Ваше имя"
            v-model.trim="$v.form.name.$model"
            :message="$v.form.name.$error ? 'Введено не корректное значение': ''"
            ></v-text-field>
        </div>
        <div class="form__row-email">
            <v-text-field
            label="Еmail"
            placeholder="Введите ваш email"
            v-model.trim="$v.form.email.$model"
            :message="$v.form.email.$error ? 'Введено не корректное значение': ''"
            ></v-text-field>
        </div>
        <div class="form__row-phone">
            <v-text-field
            label="Номер телефона"
            placeholder="Введите номер телефона"
            v-model.trim="$v.form.phone.$model"
            :message="$v.form.phone.$error ? 'Введено не корректное значение': ''"
            ></v-text-field>
        </div>
        <div class="form__row-language">
            <v-drop-down
            label="Язык"
            :options="form.options"
            v-model = "form.selected"
            ></v-drop-down>
        </div>
        <div class="form__row-agreement">
            <v-check-box v-model="$v.form.agreement.$model">Принимаю  <a href="#" class="bold">условия</a> использования</v-check-box>
        </div>
        <div class="form__row-btn-reg">
            <v-button :disabled="$v.form.$invalid">Зарегистрироваться</v-button>
        </div>
    </form>
</template>

<script>
import VButton from './vButton.vue'
import VCheckBox from './vCheckBox.vue'
import VDropDown from './vDropDown.vue'
import vTextField from './vTextField.vue'

import { validationMixin } from 'vuelidate'

const ValidName = (val) => /^[a-zA-Zа-яёА-Я\s\-]+$/.test(val)
const ValidPhone = (val) => /^\+[0-9\+\-\(\)]{11,11}$/.test(val)




import { required, email } from '../../node_modules/vuelidate/lib/validators'

export default {
  mixins: [validationMixin],
  components: { vTextField, VDropDown, VCheckBox, VButton },
  data(){
      return {
          form:{
              name:'',
              email:'',
              phone:'',
              agreement: false,
              selected : {id:0, value:'Язык'},
              options:[
                  {id:1,value:'Русский'},
                  {id:2,value:'Английский'},
                  {id:3,value:'Китайский'},
                  {id:4,value:'Испанский'}
              ]
          }
      }
  },
  validations: {
      form: {
          name : {
            required,
            ValidName
          },
          email: {
              required,
              email
          },
          phone: {
             ValidPhone
          },
          agreement: {
             valid: function() {return this.form.agreement == true}
          }
      }
  },
  methods: {
    submit() {
      console.log(this.form)
      alert("Form send")
    //   this.$v.form.$touch()
    }
  }

}
</script>

<style lang="scss">
    .form {
        padding: 40px 30px;
        box-sizing: border-box;
        background: #FFFFFF;
        box-shadow: 0px 12px 24px rgba(44, 39, 56, 0.02), 0px 32px 64px rgba(44, 39, 56, 0.04);
        border-radius: 24px;
        width: 460px;

        &__header {
        font-family: IBM Plex Sans;
        color: #2C2738;
        margin-bottom: 58px;
        }

        &__title{
            font-style: normal;
            font-weight: bold;
            font-size: 34px;
            line-height: 44px;
            padding-bottom: 8px;
        }

        &__discription {
            font-style: normal;
            font-weight: normal;
            font-size: 16px;
            line-height: 22px;

        }

        a {
                color: #0880AE;
                text-decoration: none;
        }

        .bold {
            font-weight: 500;
        }

        &__row-name, &__row-email, &__row-phone, &__row-language, {
            margin-top: 8px;
        }

        &__row-agreement, &__row-btn-reg{
            margin-top: 34px;
        }
    }

    @media (max-width: 460px){
        .form {
            width: 320px;
        }
    }

</style>