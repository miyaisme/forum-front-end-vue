<template>
  <div class="container py-5">
    <NavTabs />
    <h1 class="mt-5">美食達人</h1>
    <hr />
    <div class="row text-center">
      <div v-for="user in users" :key="user.id" class="col-3">
        <router-link :to="{ name: 'user', params: { id: user.id } }">
          <img :src="user.image" width="140px" height="140px" />
        </router-link>
        <h2>{{ user.name }}</h2>
        <span class="badge badge-secondary"
          >追蹤人數：{{ user.FollowerCount }}</span
        >
        <p class="mt-3">
          <button
            v-if="user.isFollowed"
            @click.stop.prevent="deleteFollowed(user)"
            type="button"
            class="btn btn-danger"
          >
            取消追蹤
          </button>
          <button
            v-else
            @click.stop.prevent="addFollowed(user)"
            type="button"
            class="btn btn-primary"
          >
            追蹤
          </button>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import NavTabs from "../components/NavTabs.vue";

const dummyUser = {
  users: [
    {
      id: 1,
      name: "root",
      email: "root@example.com",
      password: "$2a$10$f9iezqnQrz8Yhgp7i28IY.Y/x9Wzz0bEllpvt2VQPfv8Xh.iPgIe6",
      isAdmin: true,
      image:
        "https://cdn.pixabay.com/photo/2017/07/18/23/23/user-2517433_1280.png",
      createdAt: "2022-01-29T09:01:55.000Z",
      updatedAt: "2022-01-29T09:01:55.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false,
    },
    {
      id: 2,
      name: "user1",
      email: "user1@example.com",
      password: "$2a$10$Np1TjcB/lNOL0dameGGBGekOjgjfWMAyVrBqMMjB9X0NITL1q8mYS",
      isAdmin: false,
      image:
        "https://cdn.pixabay.com/photo/2017/07/18/23/23/user-2517433_1280.png",
      createdAt: "2022-01-29T09:01:55.000Z",
      updatedAt: "2022-01-29T09:01:55.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false,
    },
    {
      id: 3,
      name: "user2",
      email: "user2@example.com",
      password: "$2a$10$HU/LrOlGJbxAJvkQWAgFk.A.Rvp.4PqhQYG.MFGYG8y/kM1El2.Fy",
      isAdmin: false,
      image:
        "https://cdn.pixabay.com/photo/2017/07/18/23/23/user-2517433_1280.png",
      createdAt: "2022-01-29T09:01:55.000Z",
      updatedAt: "2022-01-29T09:01:55.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false,
    },
  ],
};

export default {
  components: {
    NavTabs,
  },
  data() {
    return {
      users: [],
    };
  },
  created() {
    this.fetchUser();
  },
  methods: {
    fetchUser() {
      const { users } = dummyUser;
      this.users = users;
    },
    addFollowed(user) {
      user.isFollowed = true;
    },
    deleteFollowed(user) {
      user.isFollowed = false;
    },
  },
};
</script>