<template>
<div>
<h1 class="test">Producer</h1>
  <form @submit.prevent="publish">
    <div>
      <label for="username">User name</label>
      <input type="text" name="username" id="username" v-model="messageModel.username">
    </div>
    <div>
      <label for="message">Your Message</label>
      <input type="text" name="username" id="message" v-model="messageModel.message">
    </div>
    <button type="submit">Publish</button>
  </form>
</div>
</template>

<script>
import axios from "axios";
export default {
  name:'ProducerComponent',
  data(){
    return {
      messageModel: {
        message:'',
        username:'',
      },
    }
  },
  methods:{
    publish(){
      axios.post('http://localhost:8050/producer/publish',this.messageModel).
      then(response => console.log(response))
          .catch(error=>console.log(error))
    }
  }
}

</script>

<style>
.test{
  color: blue;
}
</style>
