<template>
    <div class="realtime">
        <input type="text" v-model="user.name">
        <button @click="postData()">add</button>
        <ul v-for="(user,idx) in users" :key="idx">
            <li>{{user.name}}</li>
        </ul>
    </div>
</template>

<script>
export default {
    name:'realtimeData',
    data(){
        return{
            user:{
                name:null
            },
            users:[]
        }
    },
    methods:{
        postData(){
            this.$http.post('https://get-data-5e4e7-default-rtdb.firebaseio.com/data.json',this.user)
            .then(response=>{
                console.log(response)
            })
        },
        // getData(){
        //     this.$$http.get('https://get-data-5e4e7-default-rtdb.firebaseio.com/data.json')
        //     .then(response=>{
        //         return response.json()
        //     })
        //     .then(data=>{
        //         let a = []
        //     })  
        // },
        getData(){

        }
    },
    created(){
        this.getData
    }
}
</script>

<style>

</style>