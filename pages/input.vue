<template>
  <div>
    <input v-model="newMessage" type="text" />
    <br /><br />
    <button @click="addMessage()">追加</button>
    <button @click="deleteMessage()">古い順に削除</button>
    <br /><br />
    <div v-for="message in messages" :key="message.index">{{ message }}</div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

@Component
export default class InputComponent extends Vue {
  private newMessage: string = ''
  private messages: string[] = []

  private addMessage(): void {
    this.messages.push(this.newMessage)
    this.newMessage = ''
  }

  private deleteMessage(): void {
    if (this.messages.length > 0) {
      this.messages.splice(0, 1)
    }
  }
}
</script>

<style></style>
