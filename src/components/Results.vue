<template>
    <div>
        Reaction time: <span class="score">{{ score }}</span> ms
        <p class="rank">{{ rank }}</p>
    </div>
</template>
<script>
export default {
    props: ['score'],
    data(){
       return {
            rank:null
       }
    },
    mounted(){
        if (this.score < 250) {
            this.rank = 'You are a fast clicker!'
        } else if (this.score < 400) {
            this.rank = 'You have rapid reflexes!'
        } else {
            this.rank = 'You are slow like a snail!'
        }
    }
}
</script>
<style>
.score{
font-size:1.2em;
color:#0faf87;
font-weight: bold;
}
.rank{
font-size:1.4em;
color:#0faf87;
font-weight: bold;
}
</style>