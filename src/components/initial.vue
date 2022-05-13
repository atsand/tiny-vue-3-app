<template>
  <div class="">
    <h1>Ask a question</h1>
    <div class="mb-3">
      <input
        name="question"
        type="text"
        class="form-control"
        id="question"
        v-model="questionText"
      />
    <button
      class="btn animate__animated animate__fadeIn"
      v-if="questionText"
      @click="submit"
    >Next</button>
    <div 
        class="error animate__animated animate__fadeIn"
        v-if="error"
    >Question must be at least six characters</div>
    </div>
  </div>
</template>

<script>

export default{
  data() {
    return{
      questionText: '',
      error: false,
    }
  },
  methods:{
    submit(event){
      event.preventDefault();
      if(this.questionText.length <= 5){
        this.error = true;
      } else{
        this.error = false;
        this.$emit('goTo', 1);
        this.$emit('setQuestion', this.questionText);
      }
    }
  }
}
</script>