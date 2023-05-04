<template>
  <main class="main">
    <TransitionGroup name="list">
    <div class="chatItem" v-for="(mess, index) in message" :key="index">
      <div class="chatItem__body" :class="{
        send: mess.sendId == sendId,
        get:  mess.sendId != sendId,
        photo: mess.photo?.length > 0 && mess.body.length == 0,
        'photo-text': mess.photo?.length > 0 && mess.body.length > 0,
       }">
        <span class="chatItem__time">{{ mess.time }}</span>
        <div class="chatItem__text">
          <img :src="mess.photo" v-if="mess.photo?.length > 0" alt="">
          <p>{{ mess.body }}</p>
        </div>
      </div>
    </div>

    </TransitionGroup>
    
  </main>
</template>

<script>
export default {
  name: "Main",
  props: {
    message: Array,
    sendId: Number 
  },
};
</script>

<style>
</style>