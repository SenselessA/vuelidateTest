<template>
  
  <div class="main-form">
    <form
    method="post"
  >

    <fieldset>
      <legend>Информация о клиенте:</legend>

      <p class="form-group" :class="{ 'form-group--error': $v.surname.$error }">
        <label for="surname">Фамилия*</label>
        <input v-model="surname" type="text" id="surname" name="surname"
        class="form__input" 
        :class="{ error: $v.surname.$error }"
        @change="$v.surname.$touch()"
        >
      </p>

      <p class="form-group" :class="{ 'form-group--error': $v.name.$error }">
        <label for="name">Имя*</label>
        <input type="text" name="name" v-model="name"
        class="form__input"
        :class="{ error: $v.name.$error }"
        @change="$v.name.$touch()">
      </p>

      <p>
        <label for="patronymic">Отчество</label>
        <input type="text" name="patronymic" v-model="patronymic">
      </p>

      <p>
        <label for="DOB">Дата рождения*</label>
        <input type="date" name="DOB" v-model="DOB">
      </p>

      <p>
        <label for="tel">Номер телефона*</label>
        <input type="tel" name="tel" v-model="tel">
      </p>

      <p>
        <label for="gender">Пол</label>
        <input type="text" name="gender" v-model="gender">
      </p>

      <p>
        <label for="client_group">Группа клиентов*</label>
        <select multiple size="3" name="client_group" v-model="client_group">
          <option value="VIP">VIP</option>
          <option value="Проблемные">Проблемные</option>
          <option value="ОМС">ОМС</option>
        </select>
      </p>

      <p>
        <label for="attending_doctor">Лечащий врач</label>
        <select name="attending_doctor" v-model="attending_doctor">
          <option value="Иванов">Иванов</option>
          <option value="Захаров">Захаров</option>
          <option value="Чернышева">Чернышева</option>
        </select>
      </p>

      <p>
        <label for="send_check">Не отправлять СМС</label>
        <input type="checkbox" name="send_check" v-model="send_check">
      </p>

    </fieldset>

    <fieldset>
      <legend>Адрес:</legend>

      <p>
        <label for="postcode">Индекс</label>
        <input type="text" id="postcode" name="postcode" v-model="postcode">
      </p>

      <p>
        <label for="country">Страна</label>
        <input type="text" id="country" name="country" v-model="country">
      </p>

      <p>
        <label for="region">Область</label>
        <input type="text" id="region" name="region" v-model="region">
      </p>

      <p>
        <label for="city">Город*</label>
        <input type="text" id="city" name="city" v-model="city">
      </p>

      <p>
        <label for="street">Улица</label>
        <input type="text" id="street" name="street" v-model="street">
      </p>
      <p>

        <label for="house">Дом</label>
        <input type="text" id="house" name="house" v-model="house">
      </p>

    </fieldset>

    <fieldset>
      <legend>Паспорт:</legend>

      <p>
        <label for="document_type">Тип документа*</label>
        <select name="document_type" v-model="document_type">
          <option value="Паспорт">Паспорт</option>
          <option value="Свидетельство о рождении">Свидетельство о рождении</option>
          <option value="Вод. удостоверение">Вод. удостоверение</option>
        </select>
      </p>

      <p>
        <label for="passport_series">Серия</label>
        <input type="text" id="passport_series" name="passport_series" v-model="passport_series">
      </p>

      <p>
        <label for="passport_region">Область</label>
        <input type="text" id="passport_region" name="passport_region" v-model="passport_region">
      </p>

      <p>
        <label for="passport_ID">Номер</label>
        <input type="text" id="passport_ID" name="passport_ID" v-model="passport_ID">
      </p>

      <p>
        <label for="issued_by">Кем выдан</label>
        <input type="text" id="issued_by" name="issued_by" v-model="issued_by">
      </p>

      <p>
        <label for="date_of_issue">Дата выдачи*</label>
        <input type="text" id="date_of_issue" name="date_of_issue" v-model="date_of_issue">
      </p>
    </fieldset>
    
    <p>*Поле обязательное для заполнения.</p>

    <input
      type="submit"
      value="Отправить"
    >
  </form>

  </div>
</template>

<script>
import { required, minLength, maxLength, numeric, between } from 'vuelidate/lib/validators';
export default {
  name: 'FormComponent',
  props: {
    
  },
  data(){
    return {
      surname: '',
      name: '',
      patronymic: '',
      DOB: '',
      tel: '',
      gender: '',
      client_group: [],
      attending_doctor: '',
      send_check: '',
      postcode: '',
      country: '',
      region: '',
      city: '',
      street: '',
      house: '',
      document_type: '',
      passport_series: '',
      passport_region: '',
      passport_ID: '',
      issued_by: '',
      date_of_issue: ''
    }
  },
  validations: {
    surname: {
      required
    },
    name: {
      required
    },
    DOB: {
      required
    },
    tel: {
      required,
      minLength: minLength(11),
      maxLength: maxLength(11),
      numeric,
      regex: /^7\d{10}$/
    },
    client_group: {
      required
    },
    city: {
      required
    },
    document_type: {
      required
    },
    date_of_issue: {
      required
    }

  },
  methods: {

  }
}
</script>


<style scoped lang="sass">

$form-bg: #f8f4e5
$form-shadow: #ffa580
$form-primary-highlight: #95a4ff
$form-secondary-highlight: #ffc8ff
$font-size: 14pt
$font-face: 'Fjalla One'
$font-color: #2A293E

fieldset 
  border: none

legend 
  font-size: 30px
  margin-bottom: 20px

.main-form
  background: $form-bg
  padding: 50px 100px
  border: 2px solid rgba(0,0,0,1)
  box-shadow: 15px 15px 1px $form-shadow, 15px 15px 1px 2px rgba(0,0,0,1)

input
  display: block
  width: 100%
  font-size: $font-size
  line-height: $font-size * 2
  font-family: $font-face
  margin-bottom: $font-size * 2
  border: none
  border-bottom: 5px solid rgba(0,0,0,1)
  background: $form-bg
  min-width: 250px
  padding-left: 5px
  outline: none
  color: rgba(0,0,0,1)
  
input:focus
  border-bottom: 5px solid $form-shadow
  
button
  display: block
  margin: 0 auto
  line-height: $font-size * 2
  padding: 0 20px
  background: $form-shadow
  letter-spacing: 2px
  transition: .2s all ease-in-out
  outline: none
  border: 1px solid rgba(0,0,0,1)
  box-shadow: 3px 3px 1px $form-primary-highlight, 3px 3px 1px 1px rgba(0,0,0,1)
  
  &:hover
    background: rgba(0,0,0,1)
    color: white
    border: 1px solid rgba(0,0,0,1)
  
::selection 
  background: $form-secondary-highlight

input:-webkit-autofill,
input:-webkit-autofill:hover, 
input:-webkit-autofill:focus
  border-bottom: 5px solid $form-primary-highlight
  -webkit-text-fill-color: $font-color
  -webkit-box-shadow: 0 0 0px 1000px $form-bg inset
  transition: background-color 5000s ease-in-out 0s

input
  &.error
    border-color: red
  
</style>
