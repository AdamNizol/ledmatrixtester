<template>
  <div class="displayContainer">
    <h3>{{bytes}}</h3>
  </div>
</template>

<script>
export default {
  name: 'ColourPicker',
  props: {
    value: Array
  },
  computed: {
    bits: function(){
      let result = "";

      let colBits = ["", "",""]
      for(let i = 0; i < 32; i++){
        for(let j=1; j<4; j++){
          for(let y = 0; y < 16; y++){
            if(this.value[i+(y*32)][j] == "0"){
              colBits[j-1] += "0"
            }else{
              colBits[j-1] += "1"
            }
          }
        }
      }

      for(let j = 0; j < colBits.length; j++){
        result += colBits[j];
      }

      return result;
    },
    bytes: function(){
      let result = ""

      for(let i = 0; i < this.bits.length/8 ; i++){
        let byteInBits = this.bits.substr(8*i,8);
        let hexByte = parseInt(byteInBits,2).toString(16);
        if(hexByte.length < 2){ hexByte = "0"+hexByte }
        result += hexByte+" "
      }

      return result
    }

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.displayContainer{
  width: 80vw;
  border: 2px solid black;
}
</style>
