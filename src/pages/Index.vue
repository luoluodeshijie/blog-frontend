<template>
    <Layout>
        <!-- Page Header-->
        <header
            class="masthead"
            :style="{
                backgroundImage: `url(${GRIDSOME_API_URL + general.cover.url})`
            }"
        >
            <div class="container position-relative px-4 px-lg-5">
                <div class="row gx-4 gx-lg-5 justify-content-center">
                    <div class="col-md-10 col-lg-8 col-xl-7">
                        <div class="site-heading">
                            <h1>{{ general.title }}</h1>
                            <span class="subheading">{{ general.subtitle }}</span>
                        </div>
                    </div>
                </div>
            </div>
        </header>

        <!-- Main Content-->
        <div class="container px-4 px-lg-5">
            <div class="row gx-4 gx-lg-5 justify-content-center">
                <div class="col-md-10 col-lg-8 col-xl-7">
                    <!-- Post preview-->
                    <div class="post-preview" v-for="edge in $page.posts.edges" :key="edge.node.id">
                        <g-link :to="'/post/' + edge.node.id">
                            <h2 class="post-title">{{ edge.node.title }}</h2>
                            <h3 class="post-subtitle">{{ edge.node.sub_title }}</h3>
                        </g-link>
                        <p class="post-meta">
                            Posted by
                            <a href="#!">{{ edge.node.create_by.username }}</a>
                            on {{ edge.node.created_at }}
                        </p>
                        <p>
                            <span v-for="tag in edge.node.tags" :key="tag.id">
                                <g-link :to="'/tag/' + tag.id">{{ tag.title }}</g-link>
                                &nbsp;&nbsp;
                            </span>
                        </p>
                        <hr class="my-4" />
                    </div>
                    <!-- <div class="d-flex justify-content-end mb-4"><a class="btn btn-primary text-uppercase" href="#!">Older Posts →</a></div> -->
                    <Pager :info="$page.posts.pageInfo" />
                </div>
            </div>
        </div>

        <!-- Main Content -->
        <!-- <div class="container">
            <div class="row">
                <div class="col-lg-8 col-md-10 mx-auto">
                    <div class="post-preview" v-for="edge in $page.posts.edges" :key="edge.node.id">
                        <a href="post.html">
                            <h2 class="post-title">{{ edge.node.title }}</h2>
                        </a>
                        <p class="post-meta">Posted by
                            <a href="#">{{ edge.node.created_by.firstname + edge.node.created_by.lastname }}</a>
                            on {{ edge.node.created_at }}
                        </p>
                        <p>
                            <span v-for="tag in edge.node.tags" :key="tag.id">
                                <g-link :to="'/tag/' + tag.id">{{ tag.title }}</g-link>
                                &nbsp;&nbsp;
                            </span>
                        </p>
                    </div>
                    <hr>
                    <div class="clearfix">
                        <a class="btn btn-primary float-right" href="#">Older Posts &rarr;</a>
                    </div>
                    <Pager :info="$page.posts.pageInfo" />
                </div>
            </div>
        </div> -->

    </Layout>
</template>

<page-query>
query ($page: Int) {
    posts: allStrapiPost (perPage: 2, page: $page) @paginate {
        pageInfo {
            totalPages
            currentPage
        }
        edges {
            node {
                id
                title
                sub_title
                create_by {
                    id
                    username
                }
                tags {
                    id 
                    title
                }
                created_at
            }
        }
    }

    general: allStrapiGeneral {
        edges {
            node {
                id
                title
                subtitle
                cover {
                    url
                }
            }
        }
    }
}
</page-query>

<script>
import { Pager } from 'gridsome'

export default {
    metaInfo: {
        title: 'Hello, world!'
    },
    name: 'HomePage',
    components: {
        Pager
    },
    computed: {
        general () {
            return this.$page.general.edges[0].node
        }
    }
}
</script>

<style>

</style>
