<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-8">
                <h2>Filter Search</h2>

                <div>
                    <div class="form-check form-check-inline">
                        <label>
                            <input class="form-check-input" type="radio" v-model="filter.title" value="">
                            all
                        </label>
                    </div>
                    <div class="form-check form-check-inline">
                        <label>
                            <input class="form-check-input" type="radio" v-model="filter.title" value="title 1">
                            title 1
                        </label>
                    </div>
                    <div class="form-check form-check-inline">
                        <label>
                            <input class="form-check-input" type="radio" v-model="filter.title" value="title 2">
                            title 2
                        </label>
                    </div>
                    <div class="form-check form-check-inline">
                        <label>
                            <input class="form-check-input" type="radio" v-model="filter.title" value="title 3">
                            title 3
                        </label>
                    </div>
                </div>

                <div>
                    <div class="form-check form-check-inline">
                        <label>
                            <input class="form-check-input" type="radio" v-model="filter.name" value="">
                            all
                        </label>
                    </div>
                    <div class="form-check form-check-inline">
                        <label>
                            <input class="form-check-input" type="radio" v-model="filter.name" value="name 1">
                            name 1
                        </label>
                    </div>
                    <div class="form-check form-check-inline">
                        <label>
                            <input class="form-check-input" type="radio" v-model="filter.name" value="name 2">
                            name 2
                        </label>
                    </div>
                    <div class="form-check form-check-inline">
                        <label>
                            <input class="form-check-input" type="radio" v-model="filter.name" value="name 3">
                            name 3
                        </label>
                    </div>
                </div>

                <div v-if="search.length">
                    <div class="card m-2" v-for="post in search">
                        <div class="card-header">
                            <h3>{{ post.title }}</h3>
                        </div>
                        <div class="card-body">
                            {{ post.content }}
                        </div>
                        <div class="card-footer">{{ post.name }}</div>
                    </div>
                </div>

                <div class="alert alert-danger" role="alert" v-else>
                    Not Found
                </div>

            </div>
        </div>
    </div>
</template>

<script>

    export default {
        data() {
            return {
                posts: require('../../data/posts.json'),
                filter: {
                    title: "",
                    name: "",
                    content: ""
                },
            }
        },
        computed: {
            search() {
                console.log(_.omitBy(this.filter, _.isEmpty));

                return _.filter(this.posts, _.omitBy(this.filter, _.isEmpty));
            }
        }
    }
</script>
