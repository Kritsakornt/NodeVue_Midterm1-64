<template>
<div>
    <h1>Edit Camera details</h1>
    <form v-on:submit.prevent = "editUser">
        <p>ชื่อ : <input type="text" size="60" v-model="user.name"></p>
        <!-- <p>lastname : <input type="text" v-model="user.lastname"> --></p>
        <p>สเปค : <input type="text" style="width:500px;" v-model="user.email"></p>
        <p>ราคา : <input type="text" height="" size="15" v-model="user.password"></p>
        <p><button type="submit">แก้ไขรายละเอียดกล้อง</button></p>
    </form>
    <hr>
    <div>
        <p>ชื่อ : {{user.name}}</p>
        <!-- <p>lastname: {{user.lastname}}</p> -->
        <p>สเปค : {{user.email}}</p>
        <p>ราคา : {{user.password}}</p>
    </div>
</div>
</template>
<script>import UsersService from '@/services/UsersService'

export default {
    data(){
        return{
            user:{
                name: '',
                lastname: '',
                email: '',
                password: '',
                status: 'active'
            }
        }
    },
    methods:{
        async editUser(){
            try{
                await UsersService.put(this.user)
                this.$router.push({
                    name: 'users'
                })

            }catch(error){
                console.log(error)
            }
        }
    }, 
    async created(){
        try{
            let userId = this.$route.params.userId
            this.user = (await UsersService.show(userId)).data
        }catch(error){
            console.log(error)
        }
    }
}
</script>
<style scoped>


</style>