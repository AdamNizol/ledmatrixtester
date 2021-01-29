<template>
  <div class="matrixContainer">
    <ColourPicker v-model="selectedCol" />
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
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.matrixContainer{
  display: flex;
  flex-direction: column;
  align-items: center;
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
