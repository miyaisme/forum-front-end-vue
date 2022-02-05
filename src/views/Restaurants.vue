<template>
  <div class="container py-5">
    <NavTabs />
    <RestaurantsNavPills :categories="categories" />

    <div class="row">
      <RestaurantCard
        v-for="restaurant in restaurants"
        :key="restaurant.id"
        :initialRestaurant="restaurant"
      />
    </div>

    <RestaurantPagination
      v-if="totalPage.length > 1"
      :current-page="currentPage"
      :total-page="totalPage"
      :category-id="categoryId"
      :previous-page="previousPage"
      :next-page="nextPage"
    />
  </div>
</template>

<script>
import NavTabs from "../components/NavTabs.vue";
import RestaurantCard from "../components/RestaurantCard.vue";
import RestaurantsNavPills from "../components/RestaurantsNavPills.vue";
import RestaurantPagination from "../components/RestaurantsPagination.vue";

const dummyData = {
  restaurants: [
    {
      id: 1,
      name: "Royal Kirlin",
      tel: "1-279-871-4558",
      address: "779 Larry Grove",
      opening_hours: "08:00",
      description: "quasi",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=93.40570532027948",
      viewCounts: 0,
      createdAt: "2022-01-29T09:01:55.000Z",
      updatedAt: "2022-01-29T09:01:55.000Z",
      CategoryId: 1,
      Category: {
        id: 1,
        name: "中式料理",
        createdAt: "2022-01-29T09:01:55.000Z",
        updatedAt: "2022-01-29T09:01:55.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 2,
      name: "Junior Heidenreich",
      tel: "229-039-4723",
      address: "085 Patience Fork",
      opening_hours: "08:00",
      description: "dolorem qui ipsa",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=49.75130047525029",
      viewCounts: 0,
      createdAt: "2022-01-29T09:01:55.000Z",
      updatedAt: "2022-01-29T09:01:55.000Z",
      CategoryId: 1,
      Category: {
        id: 1,
        name: "中式料理",
        createdAt: "2022-01-29T09:01:55.000Z",
        updatedAt: "2022-01-29T09:01:55.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 3,
      name: "Layla Bernhard",
      tel: "065-852-2479 x0430",
      address: "6406 Pfannerstill Track",
      opening_hours: "08:00",
      description: "Ut facilis ipsum sed unde.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=73.50377976778604",
      viewCounts: 0,
      createdAt: "2022-01-29T09:01:55.000Z",
      updatedAt: "2022-01-29T09:01:55.000Z",
      CategoryId: 4,
      Category: {
        id: 4,
        name: "墨西哥料理",
        createdAt: "2022-01-29T09:01:55.000Z",
        updatedAt: "2022-01-29T09:01:55.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 4,
      name: "Creola Doyle",
      tel: "(087) 086-8473 x19366",
      address: "021 Myron Course",
      opening_hours: "08:00",
      description: "Quae vero et similique debitis voluptatibus non et",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=93.83690272750209",
      viewCounts: 0,
      createdAt: "2022-01-29T09:01:55.000Z",
      updatedAt: "2022-01-29T09:01:55.000Z",
      CategoryId: 5,
      Category: {
        id: 5,
        name: "素食料理",
        createdAt: "2022-01-29T09:01:55.000Z",
        updatedAt: "2022-01-29T09:01:55.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 5,
      name: "Rocky Abshire DVM",
      tel: "(422) 049-8370",
      address: "2347 Theodora Forge",
      opening_hours: "08:00",
      description: "Voluptatem expedita facilis.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=73.57501562389443",
      viewCounts: 0,
      createdAt: "2022-01-29T09:01:55.000Z",
      updatedAt: "2022-01-29T09:01:55.000Z",
      CategoryId: 5,
      Category: {
        id: 5,
        name: "素食料理",
        createdAt: "2022-01-29T09:01:55.000Z",
        updatedAt: "2022-01-29T09:01:55.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 6,
      name: "Rocio Mueller",
      tel: "689.186.3228 x15409",
      address: "20569 Schmeler Bridge",
      opening_hours: "08:00",
      description: "Quia molestiae omnis deleniti ex. Non tenetur nequ",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=88.42484374799282",
      viewCounts: 0,
      createdAt: "2022-01-29T09:01:55.000Z",
      updatedAt: "2022-01-29T09:01:55.000Z",
      CategoryId: 1,
      Category: {
        id: 1,
        name: "中式料理",
        createdAt: "2022-01-29T09:01:55.000Z",
        updatedAt: "2022-01-29T09:01:55.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 7,
      name: "Kyleigh Grant Sr.",
      tel: "534-133-8644",
      address: "461 Karl Shoal",
      opening_hours: "08:00",
      description: "Aut ipsum accusantium. Consequatur ipsum aut ut qu",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=55.99127321300321",
      viewCounts: 0,
      createdAt: "2022-01-29T09:01:55.000Z",
      updatedAt: "2022-01-29T09:01:55.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2022-01-29T09:01:55.000Z",
        updatedAt: "2022-01-29T09:01:55.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 8,
      name: "Lauren Kutch",
      tel: "066.217.3183",
      address: "750 Patrick Trafficway",
      opening_hours: "08:00",
      description: "vel",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=79.5656920534097",
      viewCounts: 0,
      createdAt: "2022-01-29T09:01:55.000Z",
      updatedAt: "2022-01-29T09:01:55.000Z",
      CategoryId: 4,
      Category: {
        id: 4,
        name: "墨西哥料理",
        createdAt: "2022-01-29T09:01:55.000Z",
        updatedAt: "2022-01-29T09:01:55.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 9,
      name: "Lawson Williamson",
      tel: "1-398-591-6283 x978",
      address: "478 McLaughlin Ramp",
      opening_hours: "08:00",
      description: "Esse veritatis amet amet.\nUt at velit atque ration",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=68.50882609985314",
      viewCounts: 0,
      createdAt: "2022-01-29T09:01:55.000Z",
      updatedAt: "2022-01-29T09:01:55.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-01-29T09:01:55.000Z",
        updatedAt: "2022-01-29T09:01:55.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 10,
      name: "Alek McCullough",
      tel: "636.182.6010",
      address: "923 Charles Radial",
      opening_hours: "08:00",
      description: "Laboriosam itaque et non. Eum sint delectus occaec",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=17.08669597239494",
      viewCounts: 0,
      createdAt: "2022-01-29T09:01:55.000Z",
      updatedAt: "2022-01-29T09:01:55.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-01-29T09:01:55.000Z",
        updatedAt: "2022-01-29T09:01:55.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
  ],
  categories: [
    {
      id: 1,
      name: "中式料理",
      createdAt: "2022-01-29T09:01:55.000Z",
      updatedAt: "2022-01-29T09:01:55.000Z",
    },
    {
      id: 2,
      name: "日本料理",
      createdAt: "2022-01-29T09:01:55.000Z",
      updatedAt: "2022-01-29T09:01:55.000Z",
    },
    {
      id: 3,
      name: "義大利料理",
      createdAt: "2022-01-29T09:01:55.000Z",
      updatedAt: "2022-01-29T09:01:55.000Z",
    },
    {
      id: 4,
      name: "墨西哥料理",
      createdAt: "2022-01-29T09:01:55.000Z",
      updatedAt: "2022-01-29T09:01:55.000Z",
    },
    {
      id: 5,
      name: "素食料理",
      createdAt: "2022-01-29T09:01:55.000Z",
      updatedAt: "2022-01-29T09:01:55.000Z",
    },
    {
      id: 6,
      name: "美式料理",
      createdAt: "2022-01-29T09:01:55.000Z",
      updatedAt: "2022-01-29T09:01:55.000Z",
    },
    {
      id: 7,
      name: "複合式料理",
      createdAt: "2022-01-29T09:01:55.000Z",
      updatedAt: "2022-01-29T09:01:55.000Z",
    },
  ],
  categoryId: "",
  page: 1,
  totalPage: [1, 2, 3, 4, 5],
  prev: 1,
  next: 2,
};

export default {
  components: {
    NavTabs,
    RestaurantCard,
    RestaurantsNavPills,
    RestaurantPagination,
  },
  data() {
    return {
      restaurants: [],
      categories: [],
      categoryId: -1,
      currentPage: 1,
      totalPage: [],
      previousPage: -1,
      nextPage: -1,
    };
  },
  created() {
    this.fetchRestaurants();
  },
  methods: {
    fetchRestaurants() {
      const {
        restaurants,
        categories,
        categoryId,
        page,
        totalPage,
        prev,
        next,
      } = dummyData;
      this.restaurants = restaurants;
      this.categories = categories;
      this.categoryId = categoryId;
      this.currentPage = page;
      this.totalPage = totalPage;
      this.previousPage = prev;
      this.nextPage = next;
    },
  },
};
</script>