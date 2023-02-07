<script>
    import { store } from '../store.js';
    export default {
        name: 'SearchForm',
        data() {
            return {
                store
            };
        }
    }
</script>

<template>
    
    <div class="w-50 mx-auto d-flex justify-content-center">
        <form action="" @submit.prevent="$emit('search')">
            <div class="row">
               
                <div class="col-auto">
                    <select
                        v-model="store.nameType"
                        name="type"
                        class="form-select"
                        aria-label="Select status">
                        <option selected value="">Select type</option>
                        <option value="skill card">skill card</option>
                        <option value="spell card">spell card</option>
                        <option value="trap card">trap card</option>
                    </select>
                </div>
                <div class="col-auto">
                    <button type="submit" class="btn btn-primary">
                        Search
                    </button>
                </div>
                <div class="col-auto">
                    <button type="reset" @click="$emit('clear')" class="btn btn-warning">
                        Reset
                    </button>
                </div>
            </div>
        </form>
    </div>

</template>

<style lang="scss" scoped>
</style>