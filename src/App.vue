<template>
<div class="app">
<h1>New Social</h1>
<div>{{message}}</div>
<Post :text=message />
<div v-for="post in posts" :key="post.id"><Post :text=post.text /></div>
</div>
</template>

<script>
import Post from '@/components/PostComponent.vue'

export default {
  name: 'App',
  components: {
    Post
  }, 
  data(){
    return{
      message: 'Hello everyone around here',
      posts:[
        {id: 1,
        text: 'Hey, how its going on'},
        {id: 2,
        text: 'Pretty good, thanks for asking',
        },
        {id: 3,
        text: 'Dont forget about me!'}
      ]
    }
  }
}
</script>

<style>
</style>
