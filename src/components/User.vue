<template>
  <div class="container">
    <h1>Parent Component (User)</h1>
    <p>This is parent component</p>
    <button @click="changeName">Change Name</button>
    <button @click="changeName">Change Name</button>
    <p>Data coming from Child {{ childData }}</p>
    <p>Age : {{ age }}</p>
    <hr>
    <div class="row">
      <app-user-detail v-bind:myName="title" @dataChild="childData = $event" :age="age"></app-user-detail>
      <app-user-edit v-bind:name2="title2" :age="age" @ageWasEdited="age = $event"></app-user-edit>
    </div>
  </div>
</template>

<script>
  import UserDetail from './UserDetail.vue';
  import UserEdit from './UserEdit.vue';

  export default {
    components: {
      appUserDetail: UserDetail,
      appUserEdit: UserEdit,
    },
    data: function(){
      return{
        title: "Sebastian",
        title2: "Leclerc",
        childData: "",
        age: 25,
      }
    },
    methods: {
      changeName(){
        this.title = "Hamilton",
        this.title2 = "Raikonen"
      },
    }
  }
</script>

<style>
  div.container{
    margin-top: 30px;
    padding: 20px 40px;
    background-color: #6a8d99;
    border: 1px solid #666;
  }
  div.row {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
</style>
