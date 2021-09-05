<template>
  <div class="block" v-if="enableBlock" @click="endTimer">
      Click me
  </div>
</template>

<script>
export default {
    props: ['delay'],
   
    data() {
       return {
           enableBlock: false,
           timer: null,
           reactionTime: 0
       }
   },
    mounted() {
       setTimeout(() => {
            this.enableBlock = true
            this.startTimer()
            console.log(this.delay)
        },
        this.delay)
   },

   methods: {
       startTimer() {
         this.timer = setInterval(() => {
             this.reactionTime = this.reactionTime + 10
         }, 10);
       },

       endTimer() {
         clearInterval(this.timer)  
         this.$emit('endGame', this.reactionTime)
         console.log(this.reactionTime)
       }
   }
    
    }
</script>

<style>
    .block {
        width: 400px;
        border-radius: 20px;
        background: rgb(131, 131, 245);
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
  }
</style>