<template>
  <div class="container py-5">
    <div>
      <h1>{{ name }}</h1>
      <span class="badge badge-secondary mt-1 mb-3">
        {{ category.name }}
      </span>
    </div>

    <hr>

    <ul>
      <li>評論數： {{ comments.length }} </li>
      <li>瀏覽次數： {{ viewCounts }} </li>
    </ul>

    <button
      type="button"
      class="btn btn-link"
      @click="$router.back()"
    >
      回上一頁
    </button>
  </div>
</template>

<script>
const dummyData = {
  "restaurant": {
        "id": 1,
        "name": "Royal Kirlin",
        "tel": "1-279-871-4558",
        "address": "779 Larry Grove",
        "opening_hours": "08:00",
        "description": "quasi",
        "image": "https://loremflickr.com/320/240/restaurant,food/?random=93.40570532027948",
        "viewCounts": 0,
        "createdAt": "2022-01-29T09:01:55.000Z",
        "updatedAt": "2022-01-29T09:01:55.000Z",
        "CategoryId": 1,
        "Category": {
            "id": 1,
            "name": "中式料理",
            "createdAt": "2022-01-29T09:01:55.000Z",
            "updatedAt": "2022-01-29T09:01:55.000Z"
        },
        "Comments": [
            {
                "id": 1,
                "text": "Commodi repellat recusandae exercitationem velit saepe.",
                "UserId": 2,
                "RestaurantId": 1,
                "createdAt": "2022-01-29T09:01:55.000Z",
                "updatedAt": "2022-01-29T09:01:55.000Z",
                "User": {
                    "id": 2,
                    "name": "user1",
                    "email": "user1@example.com",
                    "password": "$2a$10$Np1TjcB/lNOL0dameGGBGekOjgjfWMAyVrBqMMjB9X0NITL1q8mYS",
                    "isAdmin": false,
                    "image": null,
                    "createdAt": "2022-01-29T09:01:55.000Z",
                    "updatedAt": "2022-01-29T09:01:55.000Z"
                }
            },
            {
                "id": 51,
                "text": "Impedit culpa natus.",
                "UserId": 2,
                "RestaurantId": 1,
                "createdAt": "2022-01-29T09:01:55.000Z",
                "updatedAt": "2022-01-29T09:01:55.000Z",
                "User": {
                    "id": 2,
                    "name": "user1",
                    "email": "user1@example.com",
                    "password": "$2a$10$Np1TjcB/lNOL0dameGGBGekOjgjfWMAyVrBqMMjB9X0NITL1q8mYS",
                    "isAdmin": false,
                    "image": null,
                    "createdAt": "2022-01-29T09:01:55.000Z",
                    "updatedAt": "2022-01-29T09:01:55.000Z"
                }
            },
            {
                "id": 101,
                "text": "Ea culpa eligendi.",
                "UserId": 3,
                "RestaurantId": 1,
                "createdAt": "2022-01-29T09:01:55.000Z",
                "updatedAt": "2022-01-29T09:01:55.000Z",
                "User": {
                    "id": 3,
                    "name": "user2",
                    "email": "user2@example.com",
                    "password": "$2a$10$HU/LrOlGJbxAJvkQWAgFk.A.Rvp.4PqhQYG.MFGYG8y/kM1El2.Fy",
                    "isAdmin": false,
                    "image": null,
                    "createdAt": "2022-01-29T09:01:55.000Z",
                    "updatedAt": "2022-01-29T09:01:55.000Z"
                }
            }
        ]
    }
}

export default {
  data() {
    return {
      name: '',
      category: [],
      viewCounts: -1,
      comments: []
    }
  },
  created(){
    this.fetchData()
  },
  methods: {
    fetchData(){
      const {
        name,
        Category,
        viewCounts,
        Comments
      } = dummyData.restaurant
      this.name = name
      this.category = Category
      this.viewCounts = viewCounts
      this.comments = Comments
    }
  }
}
</script>