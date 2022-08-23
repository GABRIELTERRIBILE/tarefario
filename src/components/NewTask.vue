<template>
    <div class="new-task">
        <Message :msg="msg" v-show="msg" />
        <input v-model="name" @keydown.enter="add" type="text"
            class="form-element" placeholder="Nova tarefa?">
        <button class="form-element" @click="add">+</button>
    </div>
</template>

<script>
import Message from './Message.vue'
export default {
  components: { Message },
    data() {
        return {
            name: '',
            msg: ''
        }
    },
    methods: {
        add() {
            this.$emit('taskAdded', { name: this.name })
            this.name = ''
            this.msg = 'Tarefa cadastrada com sucesso!'
		setTimeout(() => this.msg = "", 5000);

       },

    }
}
</script>

<style>
    .new-task {
        margin: 35px;
    }

    .form-element {
        outline: none;
        font-size: 2rem;
        border: 1px solid rgb(255, 255, 255);
        padding: 5px 10px 8px;
        color: rgb(0, 0, 0);
    }

    input.form-element {
        width: 500px;
        background: rgba(253, 253, 253, 0.133);
        border-top-left-radius: 8px;
        border-bottom-left-radius: 8px;
    }

    button.form-element {
        border-left: none;
        background-color: #f8f8f8;
        border-top-right-radius: 8px;
        border-bottom-right-radius: 8px;
    }
</style>
