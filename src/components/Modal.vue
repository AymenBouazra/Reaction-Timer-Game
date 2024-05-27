<template>
    <div class="backdrop" @click.self="closeModal">
        <div class="modal">
            <div v-if="tryies.length > 0">
                <h1>Attempts</h1>
                <table>
                    <thead>
                        <th>#</th>
                        <th>Score(ms)</th>
                        <th>Rank</th>
                    </thead>
                    <tbody>
                        <tr v-for="(score,index) in tryies">
                            <td>{{ index +1 }}</td>
                            <td>{{ score }} </td>
                            <td>{{ rank(score) === 1 ? 'Best' : rank(score) }}</td>
                        </tr>
                    </tbody>
                </table>
            </div>
            <h1 v-show="tryies.length === 0">No attempts yet, please click the Start button to play!</h1>
        </div>
    </div>
</template>
<script>
export default {
    props:['tryies'],
    methods:{
        closeModal(){
            this.$emit('close');
        },
        rank(score){
            if (this.tryies.length>0) {
                const sortedArray = [...this.tryies].sort((a, b) => a - b);
            return sortedArray.indexOf(score) + 1;
            }
            return null
        }
    }
}
</script>
<style>
    .backdrop {
        position: fixed;
        background-color: rgba(0, 0, 0, 0.5);
        margin: 0;
        padding: 0;
        top: 0;
        width: 100%;
        height: 100%;
    }
    .modal {
        width: 600px;
        border-radius: 20px;
        background:white;
        color: #444;
        text-align: center;
        padding: 50px 50px;
        margin: 100px auto;
    }
    table{
        width: 100%;
        margin-top: 20px;
        border: 1px solid #cccccc;
    }
    td,th{
        border: 1px solid #cccccc;
    }
    th{
        background-color: #444;
        color:#f0f0f0
        }
    td:first-child{
        width: 100px;
    }
</style>