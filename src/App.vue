<template>
  <div id="app">
    <h1>スマートロック</h1>
    <button class="btn-lg btn-primary" @click="openAlert">開ける</button>
    <button class="btn-lg btn-danger" @click="closeAlert">閉める</button>
  </div>
</template>

<script>
import Obniz from 'obniz';

export default {
  name: 'App',
  data: () => {
    return {
      obniz: null,
    };
  },
  created: function () {
    this.obniz = new Obniz(process.env.VUE_APP_OBNIZ_ID);
  },
  methods: {
    openAlert () {
      this.obniz.display.clear();
      this.obniz.display.print('Open');
      this.$swal('開けたよ');
    },
    closeAlert (){
      this.obniz.display.clear();
      this.obniz.display.print('Close');
      this.$swal('閉めたよ');
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
