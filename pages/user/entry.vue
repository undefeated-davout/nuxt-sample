<template>
  <div>
    名前：<input v-model="user.name" type="text" />
    <br />
    自己紹介：<input v-model="user.description" type="text" /> <br /><br />
    <button @click="moveConfirmPage()">確認画面へ</button>
    <br /><br />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import { userStore } from '~/store'

export default Vue.extend({
  data: () => ({
    user: {
      name: '',
      description: '',
    },
  }),
  methods: {
    moveConfirmPage() {
      userStore.create(this.user)
      this.$router.push('/user/confirm')
    },
  },
})
</script>

<style></style>
