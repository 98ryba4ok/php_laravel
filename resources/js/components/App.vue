<script>
    export default {
    data() { return { msg: null } },
        created() {
            window.Echo.channel('channel-name').listen('NewArticleEvent', (name) => {
                console.log(name);
                this.msg=name.article;
                // alert('Добавлена новая статья!');
            })
        }
    }
</script>

<template> 
    <div v-if="msg != null" class="alert alert-success" role="alert">
        Добавлена новая статья <strong><a :href="`/article/${msg.id}`">{{ msg.name }}</a></strong>
    </div>
</template>
