<template>
    <div class="app">
        <form @submit.prevent>
            <h4>Создание поста</h4>
            <input v-bind:value="title" @input="title = $event.target.value" class="input" type="text" placeholder="Заголовок">
            <input v-bind:value="body" @input="body = $event.target.value" class="input" type="text" placeholder="Текст">
            <button @click="createPost">Добавить пост</button>
        </form>
        <div class="post" v-for="post in posts">
            <div><strong>Название:</strong> {{ post.title }}</div>
            <div><strong>Описание:</strong> {{ post.body }}</div>
        </div>
    </div>
</template>

<script>
    export default {
        data(){
            return {
                posts: [
                    {
                        id:1,
                        title:'Javascript',
                        body:'Описание поста 1'
                    },
                    {
                        id:2,
                        title:'Javascript',
                        body:'Описание поста 2'
                    },
                    {
                        id:3,
                        title:'Javascript',
                        body:'Описание поста 3'
                    },

                ],
                title: '',
                body: ''
                
            }
        },
        methods: {
            createPost(event) {
               
                const newPost = {
                    id: Date.now(),
                    title: this.title,
                    body: this.body,
                }
                this.posts.push(newPost);
                    },
            
         }
    }
</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    }

.post {
    padding: 15px;
    border: 3px solid green;
    margin-top: 20px;
}
</style>