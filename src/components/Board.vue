<template>
  <div class = "select-color" style = "padding: 10px 0">
    <p>Выбрать цвет</p>
    <input @change="getColor(color, 1, $event)" type = "color">
    <input @change="getColor(color, 2, $event)" type = "color">
  </div>
  <div class = "board">
    <div
      v-for="(i,index) in array"
      :key="index"
      class = "board-item"
      @mousedown = "startDraw(index,$event)"
      @mouseup = "stopDraw()"
      @mousemove = "setColor(index)"
      :style="(i.color ? 'background-color:'+i.color : '') + (i.color ? ';border: 1px solid '+i.color : '')"
    >
    </div>
  </div>
</template>

<script>
const array = []
const count = 1548
for (let i = 0; i !== count; i++) {
  array.push({
    color: null
  })
}

export default {
  name: 'Board',
  data () {
    return {
      colorFirst: '#000000',
      colorSecond: '#000000',
      array: array,
      draw: false,
      activeMouse: 1
    }
  },
  methods: {
    getColor (object, num, e) {
      if (num === 1) {
        this.colorFirst = e.target.value
      }
      if (num === 2) {
        this.colorSecond = e.target.value
      }
    },
    setColor (index) {
      if (this.draw) {
        if (this.activeMouse === 1) {
          this.array[index].color = this.colorFirst
        }
        if (this.activeMouse === 3) {
          this.array[index].color = this.colorSecond
        }
      }
    },
    startDraw (index, e) {
      this.draw = true
      if (e.which) {
        this.activeMouse = e.which
      }
      if (this.activeMouse === 1) {
        this.array[index].color = this.colorFirst
      }
      if (this.activeMouse === 3) {
        this.array[index].color = this.colorSecond
      }
    },
    stopDraw (index) {
      this.draw = false
    }
  }
}
</script>

<style>
  .board {
    display: flex;
    flex-wrap: wrap;
    background-color: rgba(155, 155, 155, 0.502);
  }

  .board-item {
    width :20px;
    height:20px;
    border:1px solid rgb(255, 255, 255);
    background-color: white;
  }

  .board-item:hover {
    opacity: 0.5;
  }
</style>
