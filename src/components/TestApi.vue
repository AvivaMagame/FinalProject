<template>
    <div class="container">
        <div class="title">КОМАНДЫ</div>

        <div v-if="isLoad" class="loading">Загрузка данных...</div>
        <div v-else class="data">
            <div v-for="(el, i) in teamData" :key="el.city">
                {{ i + 1 }}. {{ el.abbreviation }} {{ el.city }}
                <img src="https://image.pngaaa.com/204/1714204-middle.png" alt="delete" style="width: 15px; height: 15px;" @click="removeTeam(el.id)">
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'TestApi',

    data() {
        return {
            teamData: [],
            isload: true
        }
    },

    methods: {
        removeTeam(id) {
            this.teamData = this.teamData.filter((el) => el.id !== id);
        }
    },

    mounted() {
        const url = "https://free-nba.p.rapidapi.com/teams?page=0";
        const options = {
            method: "GET",
            headers: {
            "X-RapidaPI-Key": "488f437511msh2d3854838388c55p13692cjsn135921cfebdf",
            "X-RapidaPI-Host": "free-nba.p.rapidapi.com",
            },
        };

        fetch(url, options)
            .then((res) => res.json())
            .then((res) => {
                this.teamData = res.data;
                if (this.teamData !== '')
                    this.isLond = false;
            })
    }
}

</script>

<style>
    .container {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        color: rgb(52, 2, 65);
        margin: .3em 0;
        list-style: none;
        padding: 0;
        font-family: 'Comic Sans MS', cursive, sans-serif;
        
        
        
    }

    .title {
        
        font-size: 30px;
        color: rgb(52, 2, 65);
        margin: 10px;
        font-family: 'Comic Sans MS', cursive, sans-serif;
        position: relative;
        display: block;
        

        
    }

    .date {
        padding: 20px;
        position: relative;
        
        
    }

    .loading {
        padding-bottom: 20px;
    }

    img {
        cursor: pointer;
        margin-left: 15px;
    }

   
   

   


</style>