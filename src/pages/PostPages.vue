MyInput
<template>
  <div class="container">
    <h1>Страница с постами</h1>
    <div class="app__btns">
      <MyButton @click="showDialog">Создать пост</MyButton>
      <MySelect v-model="selectedSort" :options="sortOptions"></MySelect>
    </div>
    <MyInput v-model="searchQuery" placeholder="Поиск..." />
    <MyDialog v-model:show="dialogVisible">
      <PostForm @create="createPost" />
    </MyDialog>
    <PostList
      :posts="sortedAndSearchedPosts"
      @remove="removePost"
      v-if="!isPostLoading"
    />
    <div class="mt-15" v-else>Идет загрузка</div>
    <PaginationPage :pages="totalPages" :page="page" @update="updatePage" />
  </div>
</template>

<script>
import PostForm from "@/components/PostForm";
import PostList from "@/components/PostList";
import PaginationPage from "@/components/PaginationPage";
import axios from "axios";

export default {
  components: {
    PostForm,
    PostList,
    PaginationPage,
  },

  data() {
    return {
      dialogVisible: false,
      posts: [],
      page: 1,
      limit: 10,
      totalPages: 0,
      selectedSort: "",
      searchQuery: "",
      sortOptions: [
        {
          value: "title",
          name: "По названию",
        },
        {
          value: "description",
          name: "По описание",
        },
      ],
      isPostLoading: false,
    };
  },
  methods: {
    showDialog() {
      this.dialogVisible = true;
    },
    createPost(post) {
      this.posts.push(post);
      this.dialogVisible = false;
    },
    updatePage(page) {
      this.page = page;
    },
    removePost(post) {
      this.posts = this.posts.filter((e) => e.id !== post.id);
    },

    async fetchPost() {
      try {
        this.isPostLoading = true;
        setTimeout(async () => {
          const response = await axios.get(
            "https://jsonplaceholder.typicode.com/posts?_limit=10",
            {
              params: {
                _page: this.page,
                _limit: this.limit,
              },
            }
          );
          this.totalPages = Math.ceil(
            response.headers["x-total-count"] / this.limit
          );
          this.posts = response.data;
          this.isPostLoading = false;
        }, 1000);
      } catch (e) {
        alert("Ошибка в запросе");
      }
    },
  },
  mounted() {
    this.fetchPost();
  },
  watch: {
    page() {
      this.fetchPost();
    },
  },
  computed: {
    sortedPosts() {
      return [...this.posts].sort((post1, post2) =>
        post1[this.selectedSort]?.localeCompare(post2[this.selectedSort])
      );
    },
    sortedAndSearchedPosts() {
      return this.sortedPosts.filter((post) =>
        post.title.toLowerCase().includes(this.searchQuery.toLowerCase())
      );
    },
  },
};
</script>
