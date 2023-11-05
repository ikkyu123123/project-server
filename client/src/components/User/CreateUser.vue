<template>
  <div>
    <h1>Create User</h1>
    <form v-on:submit.prevent = "createUser">
      <p>ชื่อ:คาสิโน <input type="text" v-model="user.name"></p>
      <p>เจ้าของ<input type="text" v-model="user.lastname"></p>
      <p>ที่ตั้ง <input type="text" v-model="user.email"></p>
  
      <p><button type="submit">create user</button></p>
    </form>
  </div>
</template>

<script>
import UsersService from "@/services/UsersService";

export default {
  data() {
    return {
      user: {
        name: "",
        lastname: "",
        email: "",
     
        status: "active"
      }
    };
  },
  methods: {
    async createUser(){
      try{
        await UsersService.post(this.user)
        this.$router.push('/users')
      }catch(err){
        console.log(err)
      }
    }
  }
};
</script>

<style></style>
