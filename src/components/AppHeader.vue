<script>
    import axios from 'axios';
    import { store } from '../store.js';
    import SearchForm from './SearchForm.vue';
    export default {
        name: 'AppHeader',
        components:{
            SearchForm
        },
        data(){
            return{
                store
            }
        },
        methods:{
            getCharacters() {
            
                axios
                    .get('https://db.ygoprodeck.com/api/v7/cardinfo.php', {
                        params: {
                            type: this.store.nameType,
                        
                        }
                    })
                    .then((response) => {
                        this.store.results = response.data.data.slice(0,58);
                        
                    });
            },
            resetSearch() {
            
                this.store.nameType = '';
                
                this.getCharacters();
            }
        },
        created() {
            this.getCharacters();

        }
    }
</script>

<template>

    <header>

        <div class="container">
            <h1 >
               YUGI OH 
            </h1>
            <p>
                SELEZIONA IL TIPO
            </p>

            <SearchForm  @search="getCharacters" @clear="resetSearch"/>
        </div>

    </header>

</template>

<style lang="scss" scoped>
</style>