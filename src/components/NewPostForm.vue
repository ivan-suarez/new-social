<template>
    <div>
        <p>This is a form</p>
        <form @submit.prevent="poast">
            <input v-model="post.text" type ="text"/>
            <button>Post</button>
        </form>
    </div>
</template>

<script>
export default{
    data(){
        return{
            post:{
            text: ''

        }
        }
    },
    methods:{
        poast(){
            console.log(this.post)
            this.$emit('add-post', this.post)
        }
    }
}
</script>
