<template>
  <div class="hello">
    <div class="row">
      <div v-for="(option, optionIndex) in options" @click="setCol(option)" class="colOption" :style="'background-color: '+option" >
        <h2 v-if="value == option" >★</h2>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ColourPicker',
  props: {
    value: String
  },
  data(){
    return {
      options: [
        "#000",
        "#00F",
        "#0F0",
        "#0FF",
        "#F00",
        "#F0F",
        "#FF0",
        "#FFF"
      ],
    }
  },
  methods: {
    setCol(newOption){
      this.$emit('input', newOption);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.colOption{
  display: flex;
  align-items: center;
  justify-content: center;
  width: 2.84em;
  height: 3em;
  border: 0.33em solid #888;
  border-left: 0;
  cursor: pointer;
  &:first-of-type {
    border-left: 0.33em solid #888;
  }

  >h2{
    text-align: center;
    color: #000;
    font-size: 2.5em;
    margin: 0;
    padding: 0;
    -webkit-text-stroke: 0.03em #ccc;
  }

}
.row{
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
}
</style>
