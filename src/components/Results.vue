<template>
    <p class="block"> Reaction Time: {{score}}ms </p>
    <p class="rank" v-show="score!=0" > Your a {{ rank }}</p>
</template>

<script>
export default {
    props: ['score'],
    data(){
        return {
            rank : null,
        }
    },
    methods:{
        getRank(){
            
                if ( this.score <= 400 ){
                    this.rank = 'Ninja!'
                } else {
                    this.rank = 'slowpoke!'
                }
        
        }
    },
    created(){
        this.getRank()
    }
}
</script>
<style>
    .rank{
        padding:20px 100px;
        border-radius:6px;
        width:400px;
        margin: 0 auto;
        background: #d3d3d3;
        font-size: 30px;
        color: #ff0000;
        font-weight: bold;
    }
</style>