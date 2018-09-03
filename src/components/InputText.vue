<template>
<div id="quote-inp">
    <input type="text" class="center" :placeholder="placeholder" @keyup.enter="addedQuote" v-model="quote">
    <a class="button" @click="addedQuote">Add</a>
</div>
</template>
<script>
export default {
    props:{
        placeholder: {default: "Enter text here.."}
    },
    data: function() {
        return {
            quote:"",
        }
    },
    methods: {
        addedQuote() {
            if(this.quote != "")
             this.$emit('entered',this.quote)
             this.quote = ""
            
        }
    }
}
</script>
<style scoped>
input[type=text] {
  border: none;
  background-color: none;
  outline: 0;
  font-size: 25px;
  width: 300px;
  height: 30px;
}

input[type=text]:focus {
  border: none;
  background-color: none;
  outline: 0;
  width: 300px;
  height: 30px;
}

.center { 
  height: 40px;
  width: 300px; 
  overflow: auto;
}
label {
    text-align: left!important;
}
#quote-inp {
    margin: 20px auto 20px;
}
</style>
