<template>
   <div class="my_card rounded text-center align-items-stretch">
        <img class="img-fluid" :src="item.poster" alt="">
        <h3>{{item.title.toUpperCase()}}</h3>
        <div class="specifics">{{item.author}} <br> {{item.year}} </div>
    </div>
</template>

<script>
export default {
    name:'AppCard',
    props:{
        item:Object
    }
}
</script>

<style lang="scss">
@import '../style/variables.scss';
.my_card{
    width: 200px;
    padding: 15px;
    background-color:$card-color;
    h3{
        color:$main-text-color;
        margin-top: 10px;
        font-size: 1em;
    }
    .specifics{
        color:$secondary-text-color;
    }
}
</style>