<template>
  <div class="col-md-s6">
    <h3>Child Component 2</h3>
    <p>Inside User.vue 2. Child Component</p>
    <p>Best F1 driver : {{ name2 }}</p>
    <p>Age {{ age }}</p>
    <button @click="changeAge">Change Age</button>
  </div>
</template>

<script>
  import {eventBus} from '../main';

  export default{
    props: [
      "name2", "age"
    ],
    methods: {
      changeAge(){
        this.age = 40;
        // this.$emit("ageWasEdited", this.age)
        // eventBus.$emit("ageWasEdited", this.age);
        eventBus.changeAge(this.age)
      }
    }
  }
</script>

<style scoped>
  div {
    background-color: lightgoldenrodyellow;
    padding: 20px;
    border: 1px solid #666;
    display: inline-block;
  }
</style>

