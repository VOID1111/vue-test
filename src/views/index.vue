<template>
  <div class="main">
    <div class="lr_block">
      <div class="left_block">
        <div class="cont_block">
          <div class="margin_field">
            <label class="top-label">Название проекта</label>
            <Input placeholder="Введите название проекта*"></Input>
          </div>
          <div class="margin_field">
            <label class="top-label">Название проекта</label>
            <Input placeholder="Введите название проекта*"></Input>
          </div>
          <div class="margin_field">
            <label class="top-label">Выберите базу для обзвона</label>
            <Select placeholder="Выберите базу для обзвона" :items="db_call" label="name"></Select>
          </div>
          <div class="margin_field">
            <label class="top-label">Дата и время запуска проекта</label>
            <ul class="list_radio">
              <li>
                <label class="container">Начать сразу после запуска рассылки
                  <input type="radio" value="1" v-model="radio">
                  <span class="checkmark"></span>
                </label>
              </li>
              <li>
                <label class="container">Начать в указанное время
                  <input type="radio" value="2" v-model="radio">
                  <span class="checkmark"></span>
                </label>
              </li>
            </ul>

            <div v-if="radio === '2'" class="set_time">
              <Input placeholder="Дата"></Input>
              <Select placeholder="Часы" :items="hour"></Select>
              <Select placeholder="Минуты" :items="min"></Select>
            </div>
          </div>
          <div class="margin_field">
            <label class="top-label">Время совершения звонков</label>
            <div class="time_call">
              <div class="time_call_type">
                <label class="top-label">Не раньше</label>
                <div class="time_call_type_cont">
                  <Select placeholder="Часы" :items="hour"></Select>
                  <Select placeholder="Минуты" :items="min"></Select>
                </div>
              </div>
              <div class="time_call_type">
                <label class="top-label">Не позднее</label>
                <div class="time_call_type_cont">
                  <Select placeholder="Часы" :items="hour"></Select>
                  <Select placeholder="Минуты" :items="min"></Select>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="right_block">
        <div class="cont_block">
          <div class="margin_field">
            <label class="top-label">Параметры звонков</label>
            <div class="inline_data">
              <span class="text">
                Сколько раз перезвонить если абонент не ответил
              </span>
              <Select placeholder="Минуты" :items="min"></Select>
            </div>
            <div class="inline_data">
              <span class="text">
                Интервал между повторными звонками если абонент не ответил
              </span>
              <Select placeholder="Минуты" :items="min"></Select>
            </div>
          </div>
          <div class="margin_field">
            <label class="top-label">Дополнительные настройки</label>
            <ul class="list_radio checkbox">
              <li>
                <input type="checkbox" id="1param" value="1param" v-model="checkedNames">
                <label for="1param">Распознать автоответчик</label>
              </li>
              <li>
                <input type="checkbox" id="2param" value="2param" v-model="checkedNames">
                <label for="2param">Интелектуальная задержка</label>
              </li>
              <li>
                <input type="checkbox" id="3param" value="3param" v-model="checkedNames">
                <label for="3param">Записывать разговоры</label>
              </li>
            </ul>
            <!-- <input type="checkbox" id="1param" value="1param" v-model="checkedNames">
            <label for="1param">Распознать автоответчик</label>
            <input type="checkbox" id="2param" value="2param" v-model="checkedNames">
            <label for="2param">Интелектуальная задержка</label>
            <input type="checkbox" id="3param" value="3param" v-model="checkedNames">
            <label for="3param">Записывать разговоры</label> -->
          </div>
        </div>
      </div>
    </div>
    <div class="action_block">
      <div class="btns">
        <Button text="Сохранить" color="#727272"></Button>
        <Button text="Отменить" color="#727272"></Button>
      </div>
    </div>
  </div>
</template>

<script>
import Button from '@/components/button.vue'
import Input from '@/components/input.vue'
import Select from '@/components/select.vue'
import Radio from '@/components/radio.vue'

export default {
  name: 'index',
  components: {
    Input,
    Select,
    Button,
    Radio
  },
  data() {
    return {
      hour: [1, 2, 3, 4],
      min: [10, 20, 30, 40, 50],
      radio: '2',
      db_call: [
        {id: 1, name: 'Домашняя'},
        {id: 2, name: 'Городская'},
        {id: 3, name: 'Мировая'}
      ]
    }
  },
  created() {},
  methods: {},
  computed: {}
}
</script>

<style scoped>
.main {
  max-width: 1000px;
  width: 100%;
}

.lr_block {
  display: flex;
  justify-content: space-between;
}
.lr_block .left_block, .right_block {
  width: 50%;
  height: 100%;
}
.cont_block {
  padding: 30px 30px;
  padding-bottom: 0;
}

.action_block {
  width: 94%;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 3%;
}
.action_block .btns {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 10px;
}

.margin_field {
  margin-bottom: 25px;
}

.top-label {
  display: inline-block;
  font-family: sans-serif;
  font-size: 0.93em;
  padding-bottom: 7px;
}

.list_radio {
  padding: 0;
  margin: 0;
  padding-top: 3px;
}
.list_radio li {
  padding: 0;
  margin: 0;
  list-style: none;
  margin-bottom: 5px;
  font-family: sans-serif;
  font-size: 0.85em;
}

.checkbox li label{
  padding-left: 5px;
  font-family: sans-serif;
  font-size: 0.90em;
}



.container {
  display: block;
  position: relative;
  padding-left: 25px;
  margin-bottom: 12px;
  cursor: pointer;
  font-family: sans-serif;
  font-weight: 500;
  font-size: 0.95em;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.container input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
}

.checkmark {
  position: absolute;
  top: 0;
  left: 0;
  height: 13px;
  width: 13px;
  background-color: #eee;
  border-radius: 50%;
}

.container:hover input ~ .checkmark {
  background-color: #ccc;
}

.container input:checked ~ .checkmark {
  background-color: grey;
  display: flex;
  justify-content: center;
  align-items: center;
}

.checkmark:after {
  content: "";
  position: absolute;
  display: none;
}

.container input:checked ~ .checkmark:after {
  display: block;
}



.set_time {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 10px;
}

.time_call {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 13px;
}
.time_call_type_cont {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 5px;
}

.inline_data {
  display: grid;
  grid-template-columns: 3fr 1.3fr;
  grid-gap: 5px;
  margin-bottom: 15px;
}
.inline_data .text {
  color: #5d5a5a;
  font-family: sans-serif;
  font-size: 0.83em;
}
</style>
