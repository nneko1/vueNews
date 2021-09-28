<template>
  <div>
    <ul class="jobs-list">
      <li v-for="(user, userKey) in this.$store.state.jobs" :key="userKey" class="post">
        <div class="points">
          {{ user.points }}
        </div>
        <div>
          <p class="jobs-title">
            <a :href="user.url">
              {{ user.title }}
            </a>
          </p>
          <small class="link-text">
            {{ user.time_ago }},  
            <router-link :to="`/user/${user.user}`">
              {{ user.domain }}
            </router-link>
          </small>
        </div>
      </li>
    </ul>
    <!-- <p v-for="(user, userKey) in this.$store.state.jobs" :key="userKey">
      <a :href="user.url">
        {{ user.title }}
      </a>
      <small>
        {{ user.time_ago }}, {{ user.domain }}
      </small>
    </p> -->
  </div>
</template>

<script>

export default {
  created() {
    this.$store.dispatch("FETCH_JOBS")
  }
}
</script>

<style scoped>
.jobs-list {
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
.jobs-title {
  margin: 0;
}
.link-text {
  color: #828282;
}
</style>