<template>
  <div>
    <h1>Numbri faktid</h1>
      <p>Huvitavad faktid iga numbri kohta</p>
      <input type="number" min="0" v-model="number">
        <input type="number" v-model="inc">


      <p>{{ data }}</p>
      
      
  </div>
</template>

<script>
    const axios= require('axios')
    
export default {
  name: 'Faktid',
  data () {
      return {
          data:'',
          number: 0,
          inc: 0
      }
  },
    methods: {
       getFact() {
               if(this.number !== '' && this.inc !== ''){
                let url=`http://numbersapi.com/${this.number}..${parseInt(this.number) + parseInt(this.inc)}`


                axios.get(url)
                .then(response => {
                    this.data= response.data
                })
                .catch(error => {
                    console.log(error)
                })
            }
       }
    },
    watch:{
        number() {
            this.getFact()
        },
      
        inc () {
            this.getFact()
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    * {
       background-color: beige;
        font-family: Verdana;
        padding:15px;
        
    }

</style>
