<template>
  <v-container fluid class="fullContainer">
    <v-layout column text-xs-center justify-center align-center class="center-layout">
      <v-flex xs12>
        <div class="display-2">Order sent!</div>
        <br>
        <br>
        <div class="headline">You wait a while <em>ah</em></div>
      </v-flex>

      <v-flex xs12 class="mt-5">
        <v-btn nuxt large flat to="/">{{ '< Back' }}</v-btn>
      </v-flex>
    </v-layout>
    <div class="bottomBtn">
      <div class="footer">A one day build by <a href="https://sshawn.com" target="_blank">Shawn</a></div>
    </div>
  </v-container>
</template>

<style scoped>
.center-layout {
  position: relative;
  top: 20%;
}

.fullContainer { 
  background-color: #E9B070;
  background-image: url('~/static/img/aeropress.gif');
  background-position: bottom;
  background-repeat: no-repeat;
  background-size: 30%;
}

@media screen and (max-width: 700px) {
  .fullContainer {
    background-size: 80%;
  }
}

.footer {
  font-size: 16px;
  text-align: center;
  color: #fff;
}
</style>
