<template>
  <div class="container">
    <transition name="fade" mode="out-in">
      <component
        :is="screens[screenPosition]"
        :currQuestion="currQuestion"
        :result="result"
        @goTo="handleGoTo"
        @setQuestion="handSetQuestion"
        @getResult="handleGetResult"
        @startOver="handleStartOver"
      />
    </transition>
  </div>
</template>

<script>
import appInitial from './components/initial.vue';
import appConfirm from './components/confirm.vue';
import appResult from './components/result.vue';

export default {
  components: { 
    appInitial,
    appConfirm,
    appResult
  },
  data(){
    return{
      currQuestion: '',
      screens: ['appInitial', 'appConfirm', 'appResult'],
      screenPosition: 0,
      result: '',
      resultList: ['Yes', 'No', 'Maybe', 'Not sure...try again', 'Ask a friend', 'Call the police', 'Call your mom...']
    }
  },
  methods:{
    handleGoTo(position){
      this.screenPosition = position;
    },
    handSetQuestion(question){
      this.currQuestion = question;
    },
    getRandomValue(){
      return this.resultList[Math.floor(Math.random() * (this.resultList.length))];
    },
    generateResult(){
      let random = this.getRandomValue();
      if(this.random !== '' && this.result === random){
        this.generateResult();
      }
      this.result = random;
    },
    handleGetResult(){
      this.generateResult();
    },
    handleStartOver(){
      this.result = '';
      this.question = '';
      this.screenPosition = 0;
    }
  }
}
</script>

<style>
  @import './assets/style.css';

  .fade-enter-from {
    opacity: 0;
  }

  .fade-enter-active {
    transition: 0.5s;
  }

  .fade-enter-to {
    opacity: 1;
  }

  .fade-leave-from {
    opacity: 1;
  }

  .fade-leave-active {
    transition: .5s;
  }

  .fade-leave-to {
    opacity: 0;
  }
</style>
