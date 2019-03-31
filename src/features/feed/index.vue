<template>
  <div>
    <Loading />
    <div class="feed-list" v-if="!isLoading">
      <FeedList />
      <ArticleList />
      <singleArticle />
    </div>
    <br/>
    <!-- <a href="https://github.com/tjFogarty/feeds-app-fe" target="_blank" rel="noopener" class="title-bar__source-link">
      Merci à <i aria-hidden="true" class="fas fa-code" />
    </a> -->
  </div>
</template>

<script>
import { mapActions, mapState } from "vuex";
import ArticleList from "./ArticleList.vue";
import FeedList from "./FeedList.vue";
import SingleArticle from "./SingleArticle.vue";
import Loading from "@/components/Loading.vue";

export default {
  name: "FeedReader",

  components: { ArticleList, FeedList, SingleArticle, Loading },

  mounted() {
    this.getFeeds();
  },

  computed: {
    ...mapState(["isLoading"])
  },

  methods: {
    ...mapActions(["getFeeds"])
  }
};
</script>

<style scoped>
@media (min-width: 800px) {
  .feed-list {
    display: grid;
    grid-template-columns: 15% 22% 63%;
    grid-gap: 15px;
    align-items: start;
  }
}
</style>
