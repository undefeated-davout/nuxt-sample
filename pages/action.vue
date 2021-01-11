<template>
  <div>
    <div class="container">{{ name }}{{ world }}</div>
    <button @click="changeTextHello()">{{ btnNameHello }}</button>
    <button @click="changeTextBye()">{{ btnNameBye }}</button>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

@Component
export default class ActionComponent extends Vue {
  private name: string = 'こんにちは'
  private world: string = '世界'
  private btnNameHello: string = 'こんにちは'
  private btnNameBye: string = 'さようなら'

  private changeTextHello(): void {
    this.name = 'こんにちは'
  }

  private changeTextBye(): void {
    this.name = 'さようなら'
  }
}
</script>

<style></style>
