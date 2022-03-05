<template>
<div class="app">
<h1>New Social</h1>
<Form @add-post="addPost" />
<div>{{message}}</div>
<Post :text=message />
<div v-for="post in posts" :key="post.id"><Post :text=post.text /></div>
</div>
</template>

<script>
import Post from '@/components/PostComponent.vue'
import Form from '@/components/NewPostForm.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    Post, Form
  }, 
  data(){
    return{
      message: 'Hello everyone around here',
      posts:[
        {
        text: 'Hey, how its going on'},
        {
        text: 'Pretty good, thanks for asking',
        },
        {
        text: 'Dont forget about me!'}
      ]
    }
  },
  async mounted(){
    const response = await axios.get('http://localhost:3000/api/post')
    console.log(response.data)
    this.posts = response.data
  },
  methods:{
    async addPost(post){
     // let id = 0;
     // if(this.posts.length>0){
       // id = this.posts[this.posts.length-1].id+1;
      
      //this.posts=[...this.posts, post]
      const response = await axios.post('http://localhost:3000/api/post', {text: post.text})
      this.posts.push(response.data)
      
    }
  }
}
</script>

<style>
</style>
