<template>
  <div class="chat__window">
    <div class="user">
      <Header :src="'user1'" :name="'Александр'" :status="'Онлайн'" />
      <Main :sendId="1" :message="message" />
      <Type :sendId="1" @new-mess="newMess" />
    </div>
    <div class="user">
      <Header :src="'user2'" :name="'Евгений'" :status="'Онлайн'" />
      <Main :sendId="2" :message="message" />
      <Type :sendId="2" @new-mess="newMess" />
    </div>
  </div>
</template>

<script>
import Header from "@/components/Header.vue";
import Main from "@/components/Main.vue";
import Type from "@/components/Type.vue";

export default {
  name: "App",
  components: {
    Header,
    Main,
    Type,
  },
  data() {
    return {
      message: [],
    };
  },
  created() {
    const messStorage = localStorage.message
      ? JSON.parse(localStorage.message)
      : [];
    this.message = messStorage;
  },
  methods: {
    newMess(mess) {
      this.message.push(mess);
      localStorage.message = JSON.stringify(this.message);
    },
  },
};
</script>

<style>
</style>
