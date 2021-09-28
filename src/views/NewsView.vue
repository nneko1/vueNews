<template>
  <div>
    <ul class="news-list">
      <li v-for="(user, userKey) in this.$store.state.news" :key="userKey" class="post">
        <div class="points">
          {{ user.points }}
        </div>
        <div>
          <p class="news-title">
            <a :href="user.url">
              {{ user.title }}
            </a>
          </p>
          <small class="link-text">
            {{ user.time_ago }} by 
            <router-link :to="`/user/${user.user}`">
              {{ user.user }}
            </router-link>
          </small>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>

export default {
  created() {
    this.$store.dispatch("FETCH_NEWS")
  }
}
</script>

<style scoped>
.news-list {
  margin: 0;
  padding: 0;
}
.post {
  list-style: none;
  display: flex;
  align-items: center;
  border-bottom: 1px solid #eee;
}
.points {
  width: 80px;
  height: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #42b883
}
.news-title {
  margin: 0;
}
.link-text {
  color: #828282;
}
</style>