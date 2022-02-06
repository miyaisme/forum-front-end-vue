<template>
  <div class="container py-5">
    <NavTabs />
    <h1 class="mt-5">
      人氣餐廳
    </h1>

    <hr>
    <div
      class="card mb-3"
      style="max-width: 540px;margin: auto;"
    >
      <div 
      v-for="restaurant in restaurants"
      :key="restaurant.id"
      class="row no-gutters">
        <div class="col-md-4">
          <a href="#">
            <img
              class="card-img"
              :src="restaurant.image"
            >
          </a>
        </div>
        <div class="col-md-8">
          <div class="card-body">
            <h5 class="card-title">
              <router-link 
            :to="{name: 'restaurants-show', params: {id: restaurant.id}}"
          >
            {{ restaurant.name }}
          </router-link>
            </h5>
            <span class="badge badge-secondary">收藏數：{{restaurant.FavoriteCount}}</span>
            <p class="card-text">
              {{restaurant.description}}
            </p>
            <router-link
              :to="{name: 'restaurants-show', params: {id: restaurant.id}}"
              class="btn btn-primary mr-2"
            >Show</router-link>

            <button
              v-if="restaurant.isFavorited"
              @click.stop.prevent="deleteFavorite(restaurant)"
              type="button"
              class="btn btn-danger mr-2"
            >
              移除最愛
            </button>
            <button
              v-else
              @click.stop.prevent="addFavorite(restaurant)"
              type="button"
              class="btn btn-primary"
            >
              加到最愛
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import NavTabs from '../components/NavTabs.vue'

const dummyData = {
  "restaurants": [
        {
            "id": 50,
            "name": "Nia Heidenreich",
            "tel": "(047) 047-0408 x39312",
            "address": "8256 Abdullah Ports",
            "opening_hours": "08:00",
            "description": "qui",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=19.614862343539485",
            "viewCounts": 0,
            "createdAt": "2022-01-29T09:01:55.000Z",
            "updatedAt": "2022-01-29T09:01:55.000Z",
            "CategoryId": 5,
            "FavoritedUsers": [],
            "isFavorited": false,
            "FavoriteCount": 0
        },
        {
            "id": 49,
            "name": "Ebony Hartmann",
            "tel": "1-841-863-4388",
            "address": "392 Francesca Extension",
            "opening_hours": "08:00",
            "description": "Minus nemo enim voluptatum. Impedit ipsam aperiam.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=48.113401531369846",
            "viewCounts": 0,
            "createdAt": "2022-01-29T09:01:55.000Z",
            "updatedAt": "2022-01-29T09:01:55.000Z",
            "CategoryId": 4,
            "FavoritedUsers": [],
            "isFavorited": false,
            "FavoriteCount": 0
        },
        {
            "id": 48,
            "name": "Mrs. Walton Toy",
            "tel": "938.633.3623 x639",
            "address": "5597 Schaefer Overpass",
            "opening_hours": "08:00",
            "description": "Rerum voluptates quis eius eius omnis non aperiam ",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=78.58754972626076",
            "viewCounts": 0,
            "createdAt": "2022-01-29T09:01:55.000Z",
            "updatedAt": "2022-01-29T09:01:55.000Z",
            "CategoryId": 1,
            "FavoritedUsers": [],
            "isFavorited": false,
            "FavoriteCount": 0
        },
        {
            "id": 47,
            "name": "Dr. Angeline Stracke",
            "tel": "260.737.8444 x8823",
            "address": "456 Bertram Walk",
            "opening_hours": "08:00",
            "description": "Fuga molestiae qui aut asperiores autem consequatu",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=5.0094034883021665",
            "viewCounts": 0,
            "createdAt": "2022-01-29T09:01:55.000Z",
            "updatedAt": "2022-01-29T09:01:55.000Z",
            "CategoryId": 4,
            "FavoritedUsers": [],
            "isFavorited": false,
            "FavoriteCount": 0
        },
        {
            "id": 46,
            "name": "Dedrick Kiehn",
            "tel": "1-604-938-2739 x90638",
            "address": "3958 Dooley Canyon",
            "opening_hours": "08:00",
            "description": "Qui inventore sequi nihil laboriosam assumenda fug",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=60.904663827966885",
            "viewCounts": 0,
            "createdAt": "2022-01-29T09:01:55.000Z",
            "updatedAt": "2022-01-29T09:01:55.000Z",
            "CategoryId": 4,
            "FavoritedUsers": [],
            "isFavorited": false,
            "FavoriteCount": 0
        },
        {
            "id": 45,
            "name": "Maximo Hegmann",
            "tel": "327.918.5721",
            "address": "349 Antonetta Street",
            "opening_hours": "08:00",
            "description": "Aliquid soluta id sint ut. Ut aut omnis laudantium",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=82.38653131026436",
            "viewCounts": 0,
            "createdAt": "2022-01-29T09:01:55.000Z",
            "updatedAt": "2022-01-29T09:01:55.000Z",
            "CategoryId": 4,
            "FavoritedUsers": [],
            "isFavorited": false,
            "FavoriteCount": 0
        },
        {
            "id": 44,
            "name": "Eula Barrows",
            "tel": "838.513.0997 x7058",
            "address": "58359 Parisian Expressway",
            "opening_hours": "08:00",
            "description": "eius non aut",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=76.6383938810415",
            "viewCounts": 0,
            "createdAt": "2022-01-29T09:01:55.000Z",
            "updatedAt": "2022-01-29T09:01:55.000Z",
            "CategoryId": 2,
            "FavoritedUsers": [],
            "isFavorited": false,
            "FavoriteCount": 0
        },
        {
            "id": 43,
            "name": "Mohamed Mante",
            "tel": "335.282.8457 x462",
            "address": "136 Bergnaum Field",
            "opening_hours": "08:00",
            "description": "Aliquid ut quibusdam magni et repellat. Asperiores",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=33.27606535140137",
            "viewCounts": 0,
            "createdAt": "2022-01-29T09:01:55.000Z",
            "updatedAt": "2022-01-29T09:01:55.000Z",
            "CategoryId": 5,
            "FavoritedUsers": [],
            "isFavorited": false,
            "FavoriteCount": 0
        },
        {
            "id": 42,
            "name": "Oma Bergnaum Sr.",
            "tel": "1-936-630-3286",
            "address": "1609 Prosacco Passage",
            "opening_hours": "08:00",
            "description": "Non quasi eum ea.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=18.812586294525936",
            "viewCounts": 0,
            "createdAt": "2022-01-29T09:01:55.000Z",
            "updatedAt": "2022-01-29T09:01:55.000Z",
            "CategoryId": 4,
            "FavoritedUsers": [],
            "isFavorited": false,
            "FavoriteCount": 0
        },
        {
            "id": 41,
            "name": "Hannah Huels",
            "tel": "607-400-0520 x132",
            "address": "909 Fiona Forge",
            "opening_hours": "08:00",
            "description": "ut",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=37.101332266987264",
            "viewCounts": 0,
            "createdAt": "2022-01-29T09:01:55.000Z",
            "updatedAt": "2022-01-29T09:01:55.000Z",
            "CategoryId": 3,
            "FavoritedUsers": [],
            "isFavorited": false,
            "FavoriteCount": 0
        }
    ]
}

export default {
  components: {
    NavTabs,
  },
  data() {
    return {
      restaurants: []
    }
  },
  created() {
    this.fetchData()
  },
  methods: {
    fetchData() {
      const {
        restaurants
      } = dummyData
      this.restaurants = restaurants
    },
    addFavorite(restaurant) {
      restaurant.isFavorited = true
    },
    deleteFavorite(restaurant) {
      restaurant.isFavorited = false
    }
  }
}
</script>