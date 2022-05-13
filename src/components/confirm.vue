<template>
  <div class="">
    <h3>Your question is:</h3>
    <div class="mb-3">
      <div class="viewer">{{currQuestion}}</div>
      <hr/>
      <button
        class="btn animate__animated animate__rubberBand animate__delay-1s"
        @click="getAdvice"
      >Get advice</button>
      <button
        class="btn animate__animated animate__rubberBand animate__delay-1s"
        @click="newQuestion"
      >Ask new question</button>    
    </div>
  </div>
</template>

<script>

export default{
  props: {
    currQuestion: {
      type: String,
      default: ''
    }
  },
  data() {
    return{
      questionText: '',
    }
  },
  methods:{
    getAdvice(event){
      event.preventDefault();
      this.$emit('goTo', 2);
    },
    newQuestion(event){
      event.preventDefault();
      this.$emit('goTo', 0);
      this.$emit('setQuestion', '');
    }
  }
}
</script>