<template>
    <div class="container">
        <ul className="nav">
            <router-link to="/">Домашняя страница</router-link>
            <router-link to="/chat">Чат</router-link>
            <router-link to="/test">Подгрузка API дынных</router-link>
            
        </ul>
    </div>
</template>

<script>
export default {
    name: 'NavComp'
}

</script>

<style scoped>
    .container {
        background-color: darkkhaki;
        height: 70px;
        display: flex;
        justify-content: center;
    }

    .nav {
        width: 1290px;
        height: 100%;
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 30px;
        background-color: #ffb2ee;
        
        
       
    }
    .nav a{
        color: rgb(52, 2, 65);
        text-decoration: none;
        font-size: 1.2em;
        text-transform: uppercase;
        font-family: 'Comic Sans MS', cursive, sans-serif;
        font-weight: bold;
        

       
        
        
    }
   .nav a:hover {
        color: #ffffff;
    }
    


    
    
</style>