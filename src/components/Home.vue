<template>
    <div>
        <div v-if="isAuth">
            <div>Добро пожаловать, <b>{{ username }}</b>!</div>
            <button @click="logout">Выйти</button>
        </div>

        <div v-else>
            <label>Введите ваше имя:</label>
            <input v-model="username" @keyup.enter="login">
            <button @click="login">Войти</button>
        </div>
    </div>
</template>

<script>
    export default{
        name: 'HomePage',

        data() {
            return {
                isAuth: false,
                username: ""
            }
        },

        created() {
            if (localStorage.getItem("isAuth")) {
                this.isAuth = true;
                this.username = localStorage.getItem("username");
            }
        },

        methods: {
            login() {
                if (this.username !== "") {
                    this.isAuth = true;

                    localStorage.setItem("isAuth", true);
                    localStorage.setItem("username", this.username);

                    this.$router.push({
                        name: 'Chat',
                        query: { username: this.username }
                    })
                } else {
                    alert('Пожалуйста, введите сообщение');
                }
            },

            logout() {
                this.isAuth = false;
                this.username ="";

                localStorage.removeItem("isAuth");
                localStorage.removeItem("username")
            }
        }
    }

</script>

<style scoped>
    div {
        padding: 30px;
        font-size: 22px;
        color: black;
        font-family: 'Comic Sans MS', cursive, sans-serif;

    }
    label {
        margin: 0 15px;
    }
    button {
        margin-left: 5px;
        
    }

</style>