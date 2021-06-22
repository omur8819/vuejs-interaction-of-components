<template>
  <div class="wcol-md-6">
    <h3>Child Component 1</h3>
    <p>Inside User.vue First Child Component</p>
    <p>Best F1 pilot: {{ myName }}</p>
    <p>Best F1 pilot: {{ switchName() }}</p>
    <p>Age {{ age }}</p>
    <button @click="sendToParent">Send to parent</button>
  </div>
</template>

<script>
  
  import {eventBus} from '../main';
  export default{
    props: {
      myName: {
        type: String,
        required: true,
        default: "video",
      },
      age : String
    },
    methods: {
      switchName(){
        return this.myName.split("").reverse().join("");
      },
      sendToParent(){ 
        // this.$emit("dataChild", "Child'dan gelen data");
        // this.$emit("dataChild", {"name": "John", "surname": "Doe"});
        this.$emit("dataChild", ["name", "John", "surname", "Doe"]);
      },
    },
    created(){
      eventBus.$on("ageWasEdited", (age) => {
        this.age = age;
      })
    }
  } 
</script>

<style scoped>
  div {
    background-color: lightcoral;
    padding: 20px;
    border: 1px solid #666;
    display: inline-block;
  }
</style>
