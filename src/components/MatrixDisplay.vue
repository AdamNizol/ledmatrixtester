<template>
  <div class="matrixContainer">
    <div class="toolbar">
      <ColourPicker v-model="selectedCol" />
      <button @click="fillMatrix(selectedCol)">FILL</button>
      <button @click="fillMatrix('#000')">CLEAR</button>
    </div>
    <div class="grid">
      <div class="pixel" v-for="(pixel, pixelIndex) in value" @click="pixelClicked(pixelIndex)" :style="'background-color: '+pixel" ></div>
    </div>
  </div>
</template>

<script>
import ColourPicker from './ColourPicker.vue'

export default {
  name: 'MatrixDisplay',
  components: {
    ColourPicker
  },
  props: {
    value: Array
  },
  data(){
    return{
      selectedCol: "#FFF"
    }
  },
  methods: {
    pixelClicked(pixelIndex){
      let newArr = [...this.value];
      newArr[pixelIndex] = this.selectedCol
      this.$emit('input',newArr);
    },
    fillMatrix(col){
      let newMatrix = [];
      for(let i = 0; i < 32*16; i++){
        newMatrix.push(col)
      }
      this.$emit('input',newMatrix);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.matrixContainer{
  display: flex;
  flex-direction: column;
  align-items: center;
  .toolbar{
    display: flex;
    flex-direction: row;
    button {
      margin-left: 0.7em;
      width: 5em;
      font-weight: bold;
      cursor: pointer;
    }
  }
}
.grid{
  display: flex;
  width: 80vw;
  border: 1px solid black;
  flex-wrap: wrap;
  .pixel{
    width: 2.5vw;
    height: 2.5vw;
    border: 1px solid black;
    box-sizing: border-box;
    cursor:pointer;
  }
}
</style>
