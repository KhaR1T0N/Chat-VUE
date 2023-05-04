<template lang="">
   <div class="type">
      <textarea rows="1" placeholder='Написать сообщение...' class="type__message" v-model="message"></textarea>
      <button class='type__btn' @click="window = true" v-if="message.length == 0">
        <img src="../assets/img/photo.png" alt="">
      </button>
      <button class='type__btn' @click="sendMess" v-else>
        <img src="../assets/img/send.png" alt="">
      </button>
      <div class="window" v-if="window" @click="window = false">
         <div class="window__main" @click.stop.prevent>
          <div class="window__title">
            Отправить картинку
          </div>
          <div class="window__from">
            <label>
              <span>URL</span>
              <input v-model = "photo" placeholder='URL'>
            </label>
            <label>
              <span>Комментарий</span>
              <textarea v-model="comment" placeholder='Комментарий'></textarea>
            </label>
          </div>
          <div class="window__footer">
            <button class="btn red" @click="window = false">Отмена</button>
            <button class="btn blue" @click="sendMessPhoto">ОТПРАВИТЬ</button>
          </div>
         </div>
      </div>
   </div> 

</template>
<script>
export default {
  name: "Type",
  props: {
    sendId: Number,
  },
  data() {
    return {
      message: "",
      photo: '',
      comment: '',
      window: false,
    };
  },
  methods: {
    sendMess() {
      const time = `${new Date().getHours()}:${new Date().getMinutes()}`;
      if (this.message.length > 0) {
        const mess = {};
        mess.body = this.message.trim();
        mess.sendId = this.sendId;
        mess.time = time;
        this.$emit("new-mess", mess);
        this.message = "";
      }
    },
    sendMessPhoto() {
      const time =  `${new Date().getHours()}:${new Date().getMinutes()}`;
      if (this.photo.length > 0) {
        const mess = {};
        mess.body = this.comment.trim();
        mess.photo = this.photo.trim();
        mess.sendId = this.sendId;
        mess.time = time;
        this.$emit("new-mess", mess);
        this.comment = this.photo = '';
        this.window = false;
      }
    },
  },
};
</script>
<style>
</style>