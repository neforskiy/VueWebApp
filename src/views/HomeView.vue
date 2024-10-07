<script setup lang="ts">
import { Alert, useWebApp } from 'vue-tg'
const user = useWebApp().initData
let UserDataSTR = JSON.stringify(decodeURIComponent(user)).replace('user=', '');
UserDataSTR = UserDataSTR.replace(/}.*$/, '}');
// console.log(JSON.parse(UserDataSTR.slice(1, -1)));
console.log(UserDataSTR.slice(2, -1));
UserDataSTR = UserDataSTR.slice(2, -1);
UserDataSTR = UserDataSTR.replace("\\", '');
alert(UserDataSTR);

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

    You are: {{}}
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
