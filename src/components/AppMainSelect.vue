<template>
<div class="col-12">
    <select class="form-control" name="genere" id="genere" v-model="optionValue" @change="changeSelect">
        <option value="">Filtra per Genere</option>
        <option :value="genere" v-for="(genere,index) in albumGenre" :key="index">{{genere}}</option>
    </select>
</div>
</template>

<script>
export default {
    name:'AppMainSelect',
    data(){
        return{
            optionValue:''
        }
    },
    props:['albumGenre'],
    
    methods:{
        changeSelect(){
            this.$emit('genreSearch', this.optionValue)
        }
    }
}
</script>

<style lang="scss" scoped>
@import '../style/variables.scss';
select{
    text-align: center;
    background-color: #1D2D3B!important;
    color:$main-text-color;
    &:focus{
        color:$main-text-color;
        background-color:$header-bg-color;
    }
}
</style>