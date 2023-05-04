<template>
  <div class="header">
    <div>
      <img :src="avatars[src]" alt="" class="avatar" />
    </div>
    <div class="user__info">
      <h2 class="name">{{ name }}</h2>
      <p class="status">{{ status }}</p>
    </div>
  </div>
</template>
<script>
export default {
  name: "Header",
  props: ["src", "name", "status"],
  data() {
    return {
      avatars: {
        user1: require('../assets/img/stick1.png'),
        user2: require('../assets/img/sticker2.png'),
      }
    };
  },
};
</script>

<style>
/* .header {
  width: 400px;
  height: 112px;
  
  border-radius: 10px 10px 0 0;
}
.avatar {
  width: 50px;
  height: 50px;
  margin: 31px 10px 31px 20px;
}
.user__info {
  display: flex;
  flex-direction: column;
  gap: 2px;
}
.user__info .name {
  font-weight: 500;
  font-size: 18px;
  line-height: 14px;
  color: #ffffff;
}
.user__info .status {
  font-weight: 300;
  font-size: 14px;
  line-height: 14px;
  color: #ffffff;
} */
</style>