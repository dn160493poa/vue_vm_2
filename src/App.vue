<template>
    <div class="card">
        <h1>{{ title }}</h1>
        <div class="form-control">
            <input type="text" v-model="inputValue" :placeholder="placeholder" @keypress.enter="addNote" >
        </div>
        <button @click="addNote" class="btn">ADD</button>
        <hr>
        <div v-if="notes.length">
            <ul class="list">
                <li v-for="(note, idx) in notes" class="list-item">
                    {{ idx+1 }}. {{ note }}
                    <button @click="delNote(idx)" class="btn danger">X</button>
                </li>
                <hr>
                <li class="list-item">
                    <strong>All count: {{ notes.length }}</strong>
                </li>
            </ul>
        </div>
        <div v-else>Notes not found</div>
    </div>

</template>

<script>

export default {
    name: 'App',
    components: {},

    data(){
        return{
            title: 'Список заметок',
            placeholder: 'Ввеедите название заметок',
            inputValue: '',
            notes: []
        }
    },

    methods:{
        addNote(){
            if(this.inputValue){
                this.notes.push(this.inputValue)
                this.inputValue = ''
            }
        },

        delNote(idx){
            this.notes.splice(idx, 1)
        }
    }

}
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
