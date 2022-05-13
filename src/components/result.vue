<template>
  <div class="">
    <h3>Your answer is:</h3>
    <div class="mb-3">
      <div class="viewer">{{result}}</div>
      <hr/>
      <button
        class="btn animate__animated animate__rubberBand animate__delay-1s"
        @click="startOver"
      >Start over</button>
      <button
        class="btn animate__animated animate__rubberBand animate__delay-1s"
        @click="getResult"
      >Decide again</button>    
    </div>
  </div>
</template>

<script>
export default{
  props: {
    result: {
      type: String,
      default: ''
    }
  },
  mounted(){
    this.getResult();
  },
  data() {
    return {

    }
  },
  methods:{
    startOver(){
      this.$emit('startOver');
    },
    getResult(){
      this.$emit('getResult');
    }
  }
}

</script>

<style>

</style>