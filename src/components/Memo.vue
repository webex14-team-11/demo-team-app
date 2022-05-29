<template>
  <div id="app" class="memo-list">
    <h1>Vue メモアプリ</h1>
    <ul class="memo-list__container">
      <li v-for="(memo, index) in memos" v-bind:key="index" class="memo">
        <div class="memo__checkbox">
          <input type="checkbox" v-model="memo.isDone" />
        </div>
        <div v-if="memo.isDone" class="memo__text memo__text--done">
          {{ index }}:{{ memo.text }}
        </div>
        <div v-else class="memo__text">{{ index }}:{{ memo.text }}</div>
        <button v-on:click="deleteMemo(index)" class="memo__delete">
          削除
        </button>
      </li>
    </ul>
    <div class="add-memo-field">
      <input class="add-memo-field__input" type="text" v-model="inputMemo" />
      <button class="add-memo-field__button" v-on:click="addMemo">追加</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputMemo: "",
      memos: [],
    }
  },
  methods: {
    addMemo() {
      if (this.inputMemo !== "") {
        const memo = { text: this.inputMemo, isDone: false }
        this.memos.push(memo)
      }
    },
    deleteMemo(index) {
      this.memos.splice(index, 1)
    },
  },
}
</script>
