<template>
  <div class="item-list">
    <div class="item-container">
      <div
        v-for="item in selectedItems"
        :key="item.id"
        class="item"
        @click="moveItem(item, 'selected', 'available')"
      >
        {{ item.id }}
      </div>
      <p id="info">selected: {{ selectedItems.length }} / 6</p>
    </div>
    <div class="item-container">
      <div
        v-for="item in availableItems"
        :key="item.id"
        class="item"
        @click="moveItem(item, 'available', 'selected')"
      >
        {{ item.id }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      availableItems: [
    {
        "id": 1,
        "name": "Shoes 1"
    },
    {
        "id": 2,
        "name": "Shoes 2"
    },
    {
        "id": 3,
        "name": "Shoes 3"
    },
    {
        "id": 4,
        "name": "Shoes 4"
    },
    {
        "id": 5,
        "name": "T-shirt 1"
    },
    {
        "id": 6,
        "name": "T-shirt 2"
    },
    {
        "id": 7,
        "name": "T-shirt 3"
    },
    {
        "id": 8,
        "name": "T-shirt 4"
    }
    ],
      selectedItems: [],
      maxSelection: 6,
    };
  },
  methods: {
    moveItem(item, from, to) {
      if (to === 'selected' && this.selectedItems.length >= this.maxSelection) {
        return;
      }
      if (from === 'available') {
        this.availableItems = this.availableItems.filter(i => i.id !== item.id);
        this.selectedItems.push(item);
      } else {
        this.selectedItems = this.selectedItems.filter(i => i.id !== item.id);
        this.availableItems.push(item);
      }
    },
  },
};
</script>

<style>
.items-list {

  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 20px;
}
.item-container {
  border: 1px solid black;
  width: 200px;
  height: 300px;
  display: flex;
  flex-wrap: wrap;
  align-content: start;
  padding: 5px;
  margin: 10px;
  position: relative;
}
.item {
  width: 40px;
  height: 40px;
  background-color: gray;
  border-radius: 10px;
  margin: 5px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}
.item-container p {
    position: absolute;
    bottom: 0;
    left: 0;
}
</style>
