<template>
  <div>
    <div>
      <h1>ToDoList</h1>
    </div>
    <div>
      <button @click="changeMode(0)">全て</button>
      <button @click="changeMode(1)">実行中のみ</button>
      <button @click="changeMode(2)">完了済のみ</button>
    </div>
    <div v-for="item in items" :key="item.name">
      <div
        v-if="
          mode == 0 ||
            (mode == 1 && item.status == false) ||
            (mode == 2 && item.status == true)
        "
      >
        <div class="item" :class="{ red: item.status == false }">
          <div class="name">名前: {{ item.name }}</div>
          <div v-if="item.status == false">実行中</div>
          <div v-if="item.status == true">完了済</div>
          <div>
            <button @click="finish(item)">完了</button>
          </div>
        </div>
      </div>
    </div>
    <div>
      <label>
        課題
        <input type="text" v-model="newItemName" />
      </label>
      <button @click="addItem">課題追加</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "ToDoList",
  data() {
    return {
      items: [
        { name: "宿題", status: false },
        { name: "精進", status: false }
      ],
      newItemName: "",
      newItemStatus: false,
      mode: 0
    };
  },
  methods: {
    addItem() {
      this.items.push({ name: this.newItemName, status: false });
      this.newItemName = "";
    },
    finish(item) {
      item.status = true;
      this.item.splice();
    },
    changeMode(num) {
      this.mode = num;
      this.mode.splice();
    }
  }
};
</script>

<style>
.red {
  color: red;
}
</style>
