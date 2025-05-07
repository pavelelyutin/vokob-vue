<template>
  <ul class="news__list list-reset">
    <!-- <li v-for="newsItem in news" :key="newsItem.id" class="news__card">
      <h3>{{ newsItem.title }}</h3>
    </li> -->
    <NewsCard v-for="newsItem in news" :key="newsItem.id" :news="newsItem" />
  </ul>
</template>

<script>
import NewsCard from './NewsCard.vue'
import axios from 'axios'
export default {
  components: {
    NewsCard,
  },
  data() {
    return {
      news: [],
      error: false,
      errorMessage: '',
    }
  },
  mounted() {
    this.fetchNews()
  },
  methods: {
    async fetchNews() {
      const authToken =
        'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwczovL3Rlc3Qub2tvYi52cm4ucnUvYXBpL2F1dGgvbG9naW4iLCJpYXQiOjE3NDY1MTk3MjYsImV4cCI6MTc0OTkwOTcyNiwibmJmIjoxNzQ2NTE5NzI2LCJqdGkiOiI2WU9JTDM2VnJ4OG9UV3htIiwic3ViIjoiMTYiLCJwcnYiOiIyM2JkNWM4OTQ5ZjYwMGFkYjM5ZTcwMWM0MDA4NzJkYjdhNTk3NmY3In0.Uq6nZ_FuocyJwf7JSLMJfiVvY7eWy28fFDGzvKQep0c'
      try {
        const response = await axios.get('https://test.okob.vrn.ru/api/news', {
          headers: {
            Authorization: `Bearer ${authToken}`,
          },
        })
        this.news = response.data.data
        console.log(response.data.data)
      } catch (error) {
        console.log('Error fetch: ', error)
        this.error = true
        this.errorMessage = 'Не удалось загрузить новости. Попробуйте позже'
      }
    },
  },
}
</script>

<style></style>
