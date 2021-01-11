<template>
  <div>
    店名：<input v-model="shop.shopName" type="text" />
    <br />
    店舗紹介：<input v-model="shop.description" type="text" /> <br /><br />
    <button @click="entryShop()">登録</button>
    <br /><br />
    <div v-if="entryDocId">
      FirestoreにDocId:{{ entryDocId }}で登録しました。
    </div>
    <div v-if="errorMessage">エラーメッセージ:{{ errorMessage }}</div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import firebase from '@/plugins/firebase'

export default Vue.extend({
  data: () => ({
    shop: {
      shopName: '',
      description: '',
    },
    entryDocId: '',
    errorMessage: '',
  }),
  methods: {
    entryShop() {
      this.errorMessage = ''
      if (!this.shop.shopName || !this.shop.description) {
        this.errorMessage = '店名と店舗紹介は必須です'
        return
      }

      const db = firebase.firestore()
      const dbShops = db.collection('shops')
      dbShops
        .add({
          shopName: this.shop.shopName,
          description: this.shop.description,
        })
        .then((ref) => {
          this.entryDocId = ref.id
          this.shop.shopName = ''
          this.shop.description = ''
        })
        .catch((err) => {
          this.errorMessage = err
        })
    },
  },
})
</script>

<style></style>
