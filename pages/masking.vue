<template>
  <v-layout wrap>
    <v-flex text-xs-center class="wrapper">
      <v-textarea
        outline
        name="input-7-1"
        label="原文"
        v-model="text"
        hint="Hint text"
      />
      <v-btn flat icon @click="masking">
        <v-icon >
          swap_horiz
        </v-icon>
      </v-btn>
      <v-textarea
        outline
        name="input-7-1"
        label="結果"
        v-model="res"
        readonly
      />
    </v-flex>
  </v-layout>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      text: undefined,
      res: undefined
    }
  },
  methods: {
    async masking() {
      // const uri = 'https://masking-api.herokuapp.com/mask'
      const uri = 'http://localhost:5000/mask'
      const header = {
        headers: {
          'Content-Type': 'application/json'
        }
      }
      if (!this.text) {
        return
      }
      const res = await axios
        .post(`${uri}`, JSON.stringify({ text: this.text }), header)
        .catch(error => {
          console.error(error)
        })
      this.res = res.data.Answer.Text
    }
  }
}
</script>

<style lang="stylus">
.wrapper
  display flex
</style>
