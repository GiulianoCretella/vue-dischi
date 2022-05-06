<template>
<header class="d-flex align-items-center">
    <div class="logo_container">
        <img class="img-fluid" src="../assets/logo.png" alt="">
    </div>
</header>
</template>

<script>
export default {
    name:'AppHeader'
}
</script>

<style lang="scss" scoped>
@import '../style/general.scss';
header{
    background-color: $header-bg-color;
    height: 80px;
   .logo_container{
       width: 80px;
       padding: 10px;
   }
}
</style>