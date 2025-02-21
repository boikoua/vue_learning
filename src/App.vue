<script setup>
import { ref } from 'vue';

const message = ref('Hello');

const userName = ref('');

const name = ref('');
const surname = ref('');
const fatherName = ref('');

function getUserName(userInput) {
  if (!userInput.trim()) return;

  const prepareName = userInput.split(' ');

  name.value = prepareName[0];
  surname.value = prepareName[1];
  fatherName.value = prepareName[2];

  userName.value = '';
}

const dataTextarea = ref('');
const arrayStrings = ref([]);

function stringToArray(value) {
  if (!value.trim()) return;

  arrayStrings.value = value.split(' ');
}

const checked = ref(true);

const answersArray = ref([]);

const isDisabled = ref(true);
</script>

<template>
  <input type="text" v-model="message" />
  <br />
  <p>{{ message.toUpperCase() }}</p>
  <hr />

  <input type="text" v-model="userName" />
  <button @click="getUserName(userName)">Send</button>
  <p>Имя: {{ name }}</p>
  <p>Фамилия: {{ surname }}</p>
  <p>Отчетсво: {{ fatherName }}</p>

  <div>
    <textarea name="" id="" v-model="dataTextarea"></textarea>
    <br />
    <br />
    <button @click="stringToArray(dataTextarea)">Send</button>

    <ul v-show="arrayStrings.length">
      <li v-for="(item, index) in arrayStrings" :key="index">{{ item }}</li>
    </ul>
  </div>

  <hr />

  <input type="checkbox" v-model="checked" />
  <br />
  <br />
  <p v-show="checked">
    Lorem ipsum dolor, sit amet consectetur adipisicing elit. Modi at saepe cumque dolorum aliquid
    quibusdam eligendi exercitationem molestias similique architecto.
  </p>

  <hr />

  <input type="checkbox" v-model="answersArray" value="HTML" /> HTML
  <input type="checkbox" v-model="answersArray" value="CSS" /> CSS
  <input type="checkbox" v-model="answersArray" value="JS" /> JS

  <ul>
    <li v-for="item of answersArray" :key="item">{{ item }}</li>
  </ul>

  <hr />
  <input type="text" :disabled="isDisabled" />
  <button @click="() => (isDisabled = !isDisabled)">toggle</button>
</template>

<style scoped></style>
