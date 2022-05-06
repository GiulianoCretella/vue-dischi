<template>
    <section class="container">
        <div class="row">
            <div class="col colonne py-3 gy-0 d-flex" v-for="(album,index) in albumList" :key="index">
                <app-card :item="album"/>
            </div>
        </div>
    </section>
</template>

<script>
import axios from 'axios';
import AppCard from './AppCard.vue'
export default {
    name:'AppMain',
    components:{
        AppCard,
    },
    data(){
        return{
            apiPath:'https://flynn.boolean.careers/exercises/api/array/music',
            albumList:[],
            loading:false,
        }
    },
    created(){
        this.loading = true;
        axios.get(this.apiPath).then((res)=>{
            this.albumList = [...res.data.response];
            this.loading = false;
            console.log(this.albumList)
        }).catch((error)=>{
            this.loading = false;
            console.log(error);
        })

    }
}
</script>

<style lang="scss" scoped>
@import '../style/general.scss';

.colonne{
    flex-basis:calc(100% / 5);
}

</style>