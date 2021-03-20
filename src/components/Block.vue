<template>
    <div class="block" v-show="showBlock" @click="stopTimer" >
        <strong> Click me as fast as you can! </strong>
    </div>
</template>

<script>
export default {

    props: [ 'delay' ],
    emits: ['endGame'],
    name: 'Block',
    data(){
        return {
            showBlock : false,
            reactionTimer:  0,
            timer: null,
        }
    },
    methods:{
        startTimer(){
            this.timer = setInterval( () => {
                this.reactionTimer +=10
            }, 10)
        },  
        stopTimer(){
            clearInterval( this.timer )
            this.$emit('endGame', this.reactionTimer )

            console.log( this.reactionTimer )
          

        },
    },
    mounted(){
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay)
    },
    updated(){
        console.log( 'update')
    },

    
}
</script>

<style scoped>
    .block{
        width: 400px;
        padding:100px;
        margin:10px auto;
        background: #d3d3d3;
        border-radius: 5px;
        font-size: 20px;
    }
</style>