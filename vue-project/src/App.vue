<template>
  <div class="container">
    <app-header :list="list" />
    <app-footer :list="list"/>

  </div>
</template>

<script>
import Header from './Components/Header.vue';
import Footer from './Components/Footer.vue';

export default{
  data(){
    return{
      list:[]
    }
  },
  components: {
    AppHeader: Header,
    AppFooter: Footer
  }
}

</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body{
  min-height: 100vh;
  overflow: hidden;
}
</style>
