<template>
    <div class="root">
        {{text}}
        <input type="text" @input="checkinput" >
        <input type="text">
        {{ mail }}
        <div>asdasdads</div>
        <button
        v-for="user in users"
        :key="user"
        >{{user}}</button>
    </div>
</template>

<script>
export default {
    name: 'MyComponent',
    data() {
        return{
            text: 'hello world',
            password: '123',
            mail: "default",
            pages: 12,
            users: ["firstuser","secoduser"]
        }
    },
    
    methods: {
        checkinput(event) {
            this.mail = event.target.value
        }
    }
}
</script>