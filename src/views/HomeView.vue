<script setup lang="ts">
import { Alert, useWebApp } from 'vue-tg'
const user = useWebApp().initData
function AlertFunc(){
  return "<Alert message='Кирилл Баран'/>"
}
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

    You are: {{JSON.stringify(String(decodeURIComponent(user)))}}
  </main>
</template>
<script lang="ts">

export default {
  components: {
    Alert
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
