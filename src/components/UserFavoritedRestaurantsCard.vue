<template>
  <div class="card">
      <div class="card-header">
        <strong>{{favoritedRestaurants.length}}</strong> 收藏的餐廳
      </div>
      <div class="card-body">
          <router-link 
            v-for="favoritedRestaurant in favoritedRestaurants"
            :key="favoritedRestaurant.id"
            :to="{name: 'restaurants-show', params: {id: favoritedRestaurant.id}}"
          >
            <img :src="favoritedRestaurant.image"
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
      favoritedRestaurants: []
    }
  },
  created() {
    this.fetchfavoritedRestaurants()
  },
  methods: {
    fetchfavoritedRestaurants() {
      this.favoritedRestaurants.push(...this.user.profile.FavoritedRestaurants)
    }
  }
}
</script>