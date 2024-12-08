<script setup lang="ts">
import { ref } from 'vue';
import { Alert, useWebApp } from 'vue-tg';

// Получаем данные о пользователе
const webApp = useWebApp();
const initData = webApp.initData;

// Функция для декодирования и извлечения данных
const getUserData = (initData: string) => {
  const params = new URLSearchParams(initData);
  const userJson = params.get('user'); // Получаем строку JSON из параметра 'user'
  return userJson ? JSON.parse(decodeURIComponent(userJson)) : null; // Декодируем и парсим JSON
};

const userData = getUserData(initData); // Извлекаем данные о пользователе
const userId = ref(userData ? userData.id : null); // Извлекаем ID пользователя

</script>

<template>
  <main>
<!--    Main Page-->
    <Alert message="Kirill Baran"/>
    Score: {{score}}<br>
    PassiveScore When You Online: {{passiveScore}}<br>
    ScoreUp: {{scoreUp}}<br>
    {{scoreUpdate}}<br><br>
    <button @click="mainBtn">Click to UP YOUR SCORE!</button><br><br>
    <!--    <Alert message="Hello TgMiniApp!!"/>-->

    Your ID: {{userId}}
  </main>
</template>
<script lang="ts">

export default {
  components: {
    // Alert
  },
  data() {
    return {
      score: 0,
      scoreUp: 1,
      passiveScore: 10,
    }
  },
  methods: {
    mainBtn: function () {
      this.score+= this.scoreUp
    }
  },
  computed: {
    scoreUpdate: function () {
      setInterval((id: 2) => {
        this.score += this.passiveScore
        clearInterval(id)
      }, 2000)
    }
  }
}
</script>
