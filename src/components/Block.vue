<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        Click Me
    </div>
</template>

<script>
    export default{
        props: ['delay'],
        data(){
            return {
                showBlock: false,
                timer: null,
                reactionTime: 0,
            }
        },
        mounted() {
            setTimeout(()=>{
                this.showBlock = true;
                console.log("Delay:", this.delay)
                this.startTimer()
            }, this.delay)
        },
        updated(){
            console.log("Block Updated")
        },
        unmounted(){
            console.log("Block Unmounted")
        },
        methods:{
            startTimer(){
                this.timer = setInterval(()=>{
                    this.reactionTime += 10
                }, 10)
            },
            stopTimer(){
                clearInterval(this.timer)
                this.$emit('endGame', this.reactionTime)
            }

        }
    }

</script>

<style>

    .block{
        width: 80%;
        border-radius: 20px;
        color: whitesmoke;
        background: #0faf87;
        text-align: center;
        padding: 100px 0;
        margin: 40px 0;
    }

</style>