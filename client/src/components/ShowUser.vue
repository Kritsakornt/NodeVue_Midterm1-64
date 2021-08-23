<template>
  <div>
    <h1>Show Camera details</h1>
    <p>ลำดับที่ : {{ user.id }}</p>
    <p>ชื่อ : {{ user.name }} <!-- - {{ user.lastname }}--> </p>
    <p>สเปค : {{ user.email }}</p>
    <p>ราคา : {{ user.password }}</p>
    <p><button type="button" onclick="history.back();" value="Back">กลับหน้าแรก</button></p>
  </div>
</template>
<script>
import UserService from "@/services/UsersService";
export default {
  data() {
    return {
      user: null,
    };
  },
  async created() {
    try {
      let userId = this.$route.params.userId;
      this.user = (await UserService.show(userId)).data;
    } catch (error) {
      console.log(error);
    }
  },
};
</script>
<style scoped>
</style>