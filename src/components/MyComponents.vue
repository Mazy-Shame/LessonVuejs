<template>
    <div class="root">
        <input type="text" @input="findUser" :value="inputvalue" >
        <div 
        v-for="user in users"
        :key="user"
        >{{user}}</div>
    </div>
</template>

<script>
export default {
    name: 'MyComponent',
    data() {
        return{
            users: ["Масьянов Евгений","Егор Соколов","Женя Золотаревич","Даня Милохин"],
            input1: "1",
            users2: ["Масьянов Евгений","Егор Соколов","Женя Золотаревич","Даня Милохин"],
            inputvalue: ""
        }
    },
    
    methods: {
        findUser(event) {
            var userToFind = event.target.value
            this.inputvalue = userToFind
            if (userToFind == ""){
                this.users = []
                this.users2.forEach( (item) => {
                this.users.push(item)
          })
            }
            var sortMassive = []
            this.users.forEach( function(data) {
                if (data.indexOf(userToFind) != -1) {
                    sortMassive.push(data)
            }
          });
          this.users = []
          sortMassive.forEach( (item) => {
              this.users.push(item)
          })

        }
    }

    
    
}
</script>