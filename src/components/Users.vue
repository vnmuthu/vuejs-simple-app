<template>
    <div class="user-list" id="registration">
        <div class="users">
            <h2>Register Here!</h2>
            <hr>
            <div class="row" v-for = "(user, index) in users" :key = "index" :id = "index" v-if = "!user.registered">
                <div class="username">{{ user.name }}</div>
                <div class="age">{{ user.age }}</div>
                <button @click="registerUser(user)">Register</button>
            </div>
        </div>
        <div class="registered">
            <h2>Registered Users - {{ totalRegisteredCount }}</h2>
            <hr>
            <div class="row" v-for = "(user, index) in users" :key = "index" :id = "index" v-if = "user.registered">
                <div class="username">{{ user.name }}</div>
                <div class="age">{{ user.age }}</div>
                <button @click="unRegisterUser(user)">Unregister</button>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'app',
        data() {
            return {
                registrations: [],
                users: [
                    {id: 1, name: 'Alex', age: 23, registered: false},
                    {id: 2, name: 'Babu', age: 31, registered: false},
                    {id: 3, name: 'Cira', age: 6, registered: false},
                    {id: 4, name: 'David', age: 29, registered: false},
                    {id: 5, name: 'Mary', age: 25, registered: false},
                    {id: 6, name: 'Philip', age: 3, registered: false},
                    {id: 7, name: 'Shruti', age: 25, registered: false}
                ]
            }
        },
        computed: {
            totalRegisteredCount() {
                let total = 0;

                this.users.forEach(function (user) {
                    if(user.registered) {
                        total += 1;
                    }
                });

                return total;
            }
        },
        methods: {
            registerUser: function(user) {
                this.$emit('User Registered', user);
                user.registered = true;
            },
            unRegisterUser: function(user) {
                this.$emit('User Unregistered', user);
                user.registered = false;
            }
        }
    }
</script>

<style lang="scss">
.user-list {
    width: 100%;
    display:inline-block;
}
.users {
    width: 30%;
    display: inline-block;
    float: left;
}
.registered {
    width: 30%;
    display:inline-block;
    padding-left: 50px;
    box-sizing: border-box;
}
.row {
    width: 100%;
    display: block;
    padding: 10px 20px;
}
.username {
    width: 30%;
    display: inline-block;
}
.age {
    width: 30%;
    display: inline-block;
}
button {
    background-color: lightgoldenrodyellow;
    padding: 10px 20px;
}
</style>

