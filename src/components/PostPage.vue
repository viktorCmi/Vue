<template>
    <div class="post-page">
        <div class="post">
            <h1>{{ post.title }}</h1>
            <p>{{ post.body }}</p>
            <span>{{ formattedPostDate }}</span>
            <hr />
        </div>

        <div class="comments">
            <div v-for="comment in commentsList" :key="comment.id" :id="'comment-' + comment.id" class="comments__item">
                <h3>{{ comment.name }}</h3>
                <span>{{ comment.email }}</span>
                <p>{{ formatCommentText(comment.body) }}</p>
            </div>
        </div>
    </div>
</template>
  

<script>
export default {
    name: 'PostPage',
    data() {
        return {
            post: {
                id: 1,
                title: 'Eum et est occaecati',
                body: 'Ullam et saepe reiciendis voluptatem adipisci\nsit ...',
                postDate: new Date(),
            },
            commentsList: [
                {
                    "postId": 1,
                    "id": 1,
                    "name": "id labore ex et quam laborum",
                    "email": "Eliseo@gardner.biz",
                    "body": "laudantium enim quasi est quidem magnam voluptate ipsam eos\ntempora quo necessitatibus\ndolor quam autem quasi\nreiciendis et nam sapiente accusantium"
                },
                {
                    "postId": 1,
                    "id": 2,
                    "name": "quo vero reiciendis velit similique earum",
                    "email": "Jayne_Kuhic@sydney.com",
                    "body": "est natus enim nihil est dolore omnis voluptatem numquam\net omnis occaecati quod ullam at\nvoluptatem error expedita pariatur\nnihil sint nostrum voluptatem reiciendis et"
                },
                {
                    "postId": 1,
                    "id": 3,
                    "name": "odio adipisci rerum aut animi",
                    "email": "Nikita@garfield.biz",
                    "body": "quia molestiae reprehenderit quasi aspernatur\naut expedita occaecati aliquam eveniet laudantium\nomnis quibusdam delectus saepe quia accusamus maiores nam est\ncum et ducimus et vero voluptates excepturi deleniti ratione"
                },
                {
                    "postId": 1,
                    "id": 4,
                    "name": "alias odio sit",
                    "email": "Lew@alysha.tv",
                    "body": "non et atque\noccaecati deserunt quas accusantium unde odit nobis qui voluptatem\nquia voluptas consequuntur itaque dolor\net qui rerum deleniti ut occaecati"
                },
                {
                    "postId": 1,
                    "id": 5,
                    "name": "vero eaque aliquid doloribus et culpa",
                    "email": "Hayden@althea.biz",
                    "body": "harum non quasi et ratione\ntempore iure ex voluptates in ratione\nharum architecto fugit inventore cupiditate\nvoluptates magni quo et"
                }

            ],
        };
    },
    computed: {
        formattedPostDate() {
            const dateOptions = { year: 'numeric', month: 'long', day: 'numeric' };
            const timeOptions = { hour: 'numeric', minute: 'numeric', second: 'numeric' };

            const formattedDate = this.post.postDate.toLocaleDateString('ru-RU', dateOptions);
            const formattedTime = this.post.postDate.toLocaleTimeString('ru-RU', timeOptions);

            return `${formattedDate} ${formattedTime}`;
        },
    },
    methods: {
        formatCommentText(text) {
            const firstLetterUpper = text.charAt(0).toUpperCase() + text.slice(1);
            if (text.length > 20) {
                return firstLetterUpper + '...';
            }
            return firstLetterUpper;
        },
    },
    mounted() {
        setInterval(() => {

            this.post.postDate = new Date();
        }, 1000);
    },
};
</script>


  
<style scoped lang="scss" >
.post-page {
    background-image: url("https://abrakadabra.fun/uploads/posts/2022-02/1644361077_2-abrakadabra-fun-p-fon-dlya-saita-minimalizm-3.jpg");


}

.post {
    background-color: rgba($color: #ffffff, $alpha: 0.3)
}

.comments {
    background-color: rgba($color: #ffffff, $alpha: 0.3)
}

.comments__item {

    box-shadow: inset 0 0 3px #000,
        inset 0 0 3px #000,
        inset 0 0 3px #000;
    background-color: rgba($color: #ffffff, $alpha: 0.3);
    border-radius: 10px;
    padding-left: 5px;
}
</style>
  