<template >
    <div class="block" v-if="showblock" @click="stopTimer">
        Click me
    </div>
</template>
<script>
export default {
    props:['delay'],
    data(){
        return {
            showblock: false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted(){
        setTimeout(() => {
            this.showblock = true
            this.startTimer()
        },this.delay )
    },
    updated(){

    },
    unmounted(){

    },
    methods:{
        startTimer(){
            this.timer = setInterval(() => {
                this.reactionTime += 10
            },10)
        },
        stopTimer(){
            clearInterval(this.timer)
            this.$emit("end",this.reactionTime)
        }
    }
}
</script>
<style >
.block {
    width: 400px;
    border-radius: 20px;
    background:#2453fe;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>