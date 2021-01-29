<template>
  <div class="displayContainer">
    <h3>{{byteDat}}</h3>
  </div>
</template>

<script>
export default {
  name: 'ColourPicker',
  props: {
    value: Array
  },
  computed: {

    //right now its: RR RR GG GG BB BB RR RR GG GG BB BB
    //should be:     RR RR RR RR GG GG GG GG BB BB BB BB

    byteDat: function(){
      let result = "";

      for(let i = 0; i < 32; i++){

        let colBits = ""
        for(let j=1; j<4; j++){
          for(let y = 0; y < 16; y++){
            if(this.value[i+(y*32)][j] == "0"){
              colBits += "0"
            }else{
              colBits += "1"
            }
          }
        }

        for(let k = 0; k < colBits.length/8 ; k++){
          let byteInBits = colBits.substr(8*k,8);
          console.log(parseInt(byteInBits,2))
          console.log(byteInBits)
          let hexByte = parseInt(byteInBits,2).toString(16);
          if(hexByte.length < 2){ hexByte = "0"+hexByte }
          result += hexByte+" "
          //result += byteInBits
        }


      }

      return result;
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
