<template>
  <div>
    <v-layout wrap>
      <v-flex text-xs-center class="wrapper">
        <v-textarea
          v-model="text"
          outline
          name="input-7-1"
          label="原文"
          rows="10"
          placeholder="テキストを入力"
        />
        <v-btn flat icon @click="masking">
          <v-icon>
            swap_horiz
          </v-icon>
        </v-btn>
        <v-textarea
          v-model="res"
          outline
          name="input-7-1"
          label="結果"
          readonly
          rows="10"
          placeholder="マスキング"
        />
      </v-flex>
    </v-layout>
    <v-data-table
      :headers="headers"
      :items="desserts"
      class="elevation-1"
    >
      <template v-slot:items="props">
        <td>{{ props.item.name }}</td>
        <td>{{ props.item.lCalories }}</td>
        <td>{{ props.item.sCalories }}</td>
      </template>
    </v-data-table>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      text: undefined,
      res: undefined,
      headers: [
        {
          text: '固有名詞',
          align: 'left',
          sortable: false,
          value: 'name'
        },
        { text: '大分類', value: 'lCalories' },
        { text: '小分類', value: 'sCalories' }
      ],
      desserts: []
    }
  },
  methods: {
    async masking() {
      const uri = 'https://masking-api.herokuapp.com/mask'
      // const uri = 'http://localhost:5000/mask'
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
      this.res = res.data.text
      for (const key in res.data.proper) {
        const obj = {
          name: key,
          lCalories: res.data.proper[key][0],
          sCalories: res.data.proper[key][1]
        }
        this.desserts.push(obj)
      }
    }
  }
}
</script>

<style lang="stylus">
.wrapper
  display flex
</style>
