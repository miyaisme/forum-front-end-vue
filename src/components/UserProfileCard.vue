<template>
  <div class="card mb-3">
    <div class="row no-gutters">
      <div class="col-md-4">
        <img :src="user.profile.image" height="300px" />
      </div>
      <div class="col-md-8">
        <div class="card-body">
          <h5 class="card-title">{{ user.profile.name }}</h5>
          <p class="card-text">
            {{ user.profile.email }}
          </p>
          <ul class="list-unstyled list-inline">
            <li>
              <strong>{{ user.profile.Comments.length }}</strong> 已評論餐廳
            </li>
            <li>
              <strong>{{ user.profile.FavoritedRestaurants.length }}</strong>
              收藏的餐廳
            </li>
            <li>
              <strong>{{ user.profile.Followings.length }}</strong> followings
              (追蹤者)
            </li>
            <li>
              <strong>{{ user.profile.Followers.length }}</strong> followers
              (追隨者)
            </li>
          </ul>
          <p></p>
          <form action="/following/3" method="POST" style="display: contents">
            <button
              v-if="user.isFollowed"
              @click.stop.prevent="unFollow"
              type="button"
              class="btn btn-danger"
            >
              取消追蹤
            </button>
            <button
              v-else
              @click.stop.prevent="follow"
              type="submit"
              class="btn btn-primary"
            >
              追蹤
            </button>
          </form>
          <p></p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    initialUser: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      user: this.initialUser,
    };
  },
  methods: {
    follow() {
      this.user.isFollowed = true;
    },
    unFollow() {
      this.user.isFollowed = false;
    },
  },
};
</script>