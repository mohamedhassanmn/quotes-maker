<template>
    <div>
        <p>{{len/10}}/ 10 </p>
        <div class="container">
            <div :style="{width:len +'%'}" class="progressBar">
            </div>
        </div>
    </div>
    
</template>

<script>
export default {
    data(){
       return{
           length:100
       } 
    },
    props:["len"]
}
</script>

<style scoped>
    .container{
        margin:50px;
        width:90vw;
        height:10px;
        border:1px solid #000;
    }
    .progressBar{
        height:100%;
        background:#ccc;
    }

</style>