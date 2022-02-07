<template>
    <div class="card">
      <div class="card-header">
        <strong>{{commentedRestaurants.length}}</strong> 已評論餐廳
      </div>
      <div class="card-body">
          <router-link 
            v-for="restaurant in commentedRestaurants"
            :key="restaurant.id"
            :to="{name: 'restaurants-show', params: {id: restaurant.id}}"
          >
            <img :src="restaurant.Restaurant.image"
            width="60" height="60" class="avatar"
            >
          </router-link>
      </div>
    </div>
</template>

<script>
export default {
  props: {
    initialUser: {
      type: Object,
      required: true,
    }
  },
  data() {
    return {
      user : this.initialUser,
      commentedRestaurants: [],
    }
  },
  created() {
    this.fetchCommentedRestaurants()
  },
  methods: {
    fetchCommentedRestaurants() {
      this.commentedRestaurants.push(...this.user.profile.Comments)
    }
  }
}
</script>