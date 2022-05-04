<template>
  <div class="c-wrap">
    <div class="c-chat">
      <Message
        v-for="m in messages"
        :key="m.text"
        :name="m.name"
        :text="m.text"
        owner
      />
    </div>
    <div class="c-form">
      <ChatForms/>
    </div>
  </div>
</template>

<script>
import { mapState } from "vuex";
import Message from "@/components/Message";
import ChatForms from "@/components/ChatForms";

export default {
  middleware: ["chat"],
  components: {
    Message,
    ChatForms
  },
  head() {
    return {
      title: `Комната ${this.user.room}`
    };
  },
  computed: mapState(["user", "messages"])
};
</script>

<style scoped>
.c-wrap {
  height: 100%;
  position: relative;
  overflow: hidden;
}
.c-form {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 80px;
  padding: 10px;
  background: #212121;
}
.c-chat {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  padding: 10px;
  bottom: 80px;
  overflow-y: auto;
}
</style>>