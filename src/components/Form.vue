<template>
    <div>

    <form>
        <label for="#title">Title</label>
        <input type="text" id="title" v-model="note.title" class="form-control">
        <label for="#description">Description</label>
        <textarea name="" id="description" class="form-control" v-model="note.description"></textarea>
        <button class="btn btn-primary btn-block" @click="addNote" type="button" :disabled="!isNoteReady(note)">Add</button>
    </form>

    <!-- The card should be a separate component -->
    <section class="notes">
        <div v-for="(note, i) in reverse" v-bind:key="note" class="overflow-hidden">
            <h3>{{note.title}}</h3>
            <h5>{{note.date}}</h5>
            <p>{{note.description}}</p>
            <button type="button" class="btn btn-link float-right" @click="deleteNote(i)">Delete</button>
        </div>
    </section>
    </div>

    
</template>

<script>
export default {
    name: 'Form',
    data() {
        return {
            note: {
                title: '',
                description: ''
            },
            notes: []
        }
    },
    computed: {
        reverse: function() {
            return this.notes.slice(0).reverse();
        }
    },
    methods: {
        addNote: function() {
            let {title, description} = this.note;
            if(this.isNoteReady(this.note)) {
                this.notes.push({
                    title,
                    description,
                    date: new Date(Date.now()).toLocaleString()
                });
                this.note = {title:'', description:''}
                document.getElementById('title').focus()
            }
        },
        deleteNote: function(i) {
            let index = this.notes.length -1 - i;
            this.notes.splice(index, 1);
            this.note = {}
        },
        isNoteReady: function(note) {
            return (note.title !== '' && note.description !== '')
        }
    }
}
</script>

<style scoped>
label {font-size: 0.9em; color: #333}
.form-control {margin-bottom: 1em}
.notes div {
    margin: 1em 0;
    padding: 5px 10px;
    box-shadow: 0 2px 3px 0 rgba(0,0,0,0.35);
    border-radius: 3px;
    font-size: 1em;
}
h5 {
    color: #666;
    font-size: .8em;
    font-style: italic;
}
.btn-link {font-size: 0.8em; color: red}
</style>