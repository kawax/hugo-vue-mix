<template>
    <div class="container">
        <div class="row">
            <div class="col-md-8 col-md-offset-2">
                <h2>Filter Search</h2>

                <div>
                    <div class="radio-inline">
                        <label>
                            <input type="radio" v-model="filter.title" value="">
                            all
                        </label>
                    </div>
                    <div class="radio-inline">
                        <label>
                            <input type="radio" v-model="filter.title" value="title 1">
                            title 1
                        </label>
                    </div>
                    <div class="radio-inline">
                        <label>
                            <input type="radio" v-model="filter.title" value="title 2">
                            title 2
                        </label>
                    </div>
                    <div class="radio-inline">
                        <label>
                            <input type="radio" v-model="filter.title" value="title 3">
                            title 3
                        </label>
                    </div>
                </div>

                <div>
                    <div class="radio-inline">
                        <label>
                            <input type="radio" v-model="filter.name" value="">
                            all
                        </label>
                    </div>
                    <div class="radio-inline">
                        <label>
                            <input type="radio" v-model="filter.name" value="name 1">
                            name 1
                        </label>
                    </div>
                    <div class="radio-inline">
                        <label>
                            <input type="radio" v-model="filter.name" value="name 2">
                            name 2
                        </label>
                    </div>
                    <div class="radio-inline">
                        <label>
                            <input type="radio" v-model="filter.name" value="name 3">
                            name 3
                        </label>
                    </div>
                </div>

                <div class="panel panel-default" v-for="post in search()">
                    <div class="panel-heading">
                        <h3 class="panel-title">{{ post.title }}</h3>
                    </div>
                    <div class="panel-body">
                        {{ post.content }}
                    </div>
                    <div class="panel-footer">{{ post.name }}</div>

                </div>
            </div>
        </div>
    </div>
</template>

<script>

    export default {
        data() {
            return {
                posts: require('../../../data/posts.json'),
                filter: {
                    title: "",
                    name: "",
                    content: ""
                },
            }
        },
        methods: {
            search() {
                console.log(_.omitBy(this.filter, _.isEmpty));

                return _.filter(this.posts, _.omitBy(this.filter, _.isEmpty));
            }
        }
    }
</script>
