<script>
    import AppHeader from './components/AppHeader.vue';
    import AppMain from './components/AppMain.vue';
    import AppFooter from './components/AppFooter.vue';
    import axios from "axios";
    import { store } from './store.js';
    export default {
      name:"App",
      components:{
        AppHeader,
        AppMain,
        AppFooter
      },
      data() {
            return {
                store
            }
        },  
        created() {
            axios
                .get('https://db.ygoprodeck.com/api/v7/cardinfo.php')
                .then((response) => {
                    this.store.results = response.data.data.slice(0,12);
                    
                });
        }
    };

</script>

<template>
  <AppHeader />
  <AppMain />
  <AppFooter />
</template>

<style lang="scss" >
@import "./styles/main.scss";
</style>
