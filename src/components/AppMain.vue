<template>
    <section class="container">
        <div class="row">
            <app-main-select @genreSearch="setChangeSelect($event)" :albumGenre="genere" />
            <div class="col colonne py-3 gy-0 d-flex" v-for="(album,index) in filteredAlbumList" :key="index">
                <app-card :item="album"/>
            </div>
        </div>
    </section>
</template>

<script>

import axios from 'axios';
import AppCard from './AppCard.vue';
import AppMainSelect from './AppMainSelect.vue';

export default {
    name:'AppMain',
    components:{
        AppCard,
        AppMainSelect,
    },
    data(){
        return{
            apiPath:'https://flynn.boolean.careers/exercises/api/array/music',
            albumList:[],
            loading:false,
            genere:[],
            genereSelected:'',
        }
    },
    methods:{
        setChangeSelect(val){
            this.genereSelected = val;
        }
    },
    computed:{
        filteredAlbumList(){
            if(this.genereSelected === ''){
                return this.albumList;
            }
            return this.albumList.filter((album)=>{
                return album.genre === this.genereSelected
            })
        }
    },
    created(){
        this.loading = true;
        axios.get(this.apiPath).then((res)=>{
            this.albumList = [...res.data.response];
            this.albumList.forEach((item)=>{
                if(!this.genere.includes(item.genre)){
                    this.genere.push(item.genre)
                }
            })
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
    .colonne{
        flex:0 0 calc(100% / 5);
    }

</style>