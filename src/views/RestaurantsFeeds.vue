<template>
  <div class="container py-5">
    <NavTabs />

    <h1 class="mt-5">
      最新動態
    </h1>
    <hr>
    <div class="row">
      <div class="col-md-6">
        <h3>最新餐廳</h3>
        <NewestRestaurants :restaurants="restaurants" />
      </div>
      <div class="col-md-6">
        <NewestComments :comments="comments"/>
       <h3>最新評論</h3>
      </div>
    </div>
  </div>
</template>

<script>
import NavTabs from '../components/NavTabs.vue'
import NewestRestaurants from '../components/NewestRestaurants.vue'
import NewestComments from '../components/NewestComments.vue'

const dummyData = {
  "restaurants": [
        {
            "id": 30,
            "name": "Sheldon Sipes",
            "tel": "151-027-7832",
            "address": "4778 Stokes Mountains",
            "opening_hours": "08:00",
            "description": "Et delectus deserunt. Qui eaque voluptatem labore. Quasi aut et. Optio sed voluptatem iusto sed expedita. Reiciendis occaecati quas velit.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=54.39894349199459",
            "viewCounts": 0,
            "createdAt": "2022-01-29T09:01:55.000Z",
            "updatedAt": "2022-01-29T09:01:55.000Z",
            "CategoryId": 1,
            "Category": {
                "id": 1,
                "name": "中式料理",
                "createdAt": "2022-01-29T09:01:55.000Z",
                "updatedAt": "2022-01-29T09:01:55.000Z"
            }
        },
        {
            "id": 13,
            "name": "Adalberto Krajcik",
            "tel": "1-038-482-3536 x693",
            "address": "764 Kylee Springs",
            "opening_hours": "08:00",
            "description": "Et temporibus perspiciatis adipisci beatae id debitis excepturi. Voluptate ut quia est consequatur. Qui unde dolorem. Eos et beatae sed eum dolores voluptatem quia reprehenderit nobis.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=77.59307837064256",
            "viewCounts": 0,
            "createdAt": "2022-01-29T09:01:55.000Z",
            "updatedAt": "2022-01-29T09:01:55.000Z",
            "CategoryId": 2,
            "Category": {
                "id": 2,
                "name": "日本料理",
                "createdAt": "2022-01-29T09:01:55.000Z",
                "updatedAt": "2022-01-29T09:01:55.000Z"
            }
        },
        {
            "id": 14,
            "name": "Kaci Thiel",
            "tel": "1-759-478-2708 x864",
            "address": "76498 Trantow Locks",
            "opening_hours": "08:00",
            "description": "Aut nam velit aliquam.\nAutem quo quae non sed.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=82.95078709951372",
            "viewCounts": 0,
            "createdAt": "2022-01-29T09:01:55.000Z",
            "updatedAt": "2022-01-29T09:01:55.000Z",
            "CategoryId": 3,
            "Category": {
                "id": 3,
                "name": "義大利料理",
                "createdAt": "2022-01-29T09:01:55.000Z",
                "updatedAt": "2022-01-29T09:01:55.000Z"
            }
        },
        {
            "id": 8,
            "name": "Lauren Kutch",
            "tel": "066.217.3183",
            "address": "750 Patrick Trafficway",
            "opening_hours": "08:00",
            "description": "vel",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=79.5656920534097",
            "viewCounts": 0,
            "createdAt": "2022-01-29T09:01:55.000Z",
            "updatedAt": "2022-01-29T09:01:55.000Z",
            "CategoryId": 4,
            "Category": {
                "id": 4,
                "name": "墨西哥料理",
                "createdAt": "2022-01-29T09:01:55.000Z",
                "updatedAt": "2022-01-29T09:01:55.000Z"
            }
        },
        {
            "id": 4,
            "name": "Creola Doyle",
            "tel": "(087) 086-8473 x19366",
            "address": "021 Myron Course",
            "opening_hours": "08:00",
            "description": "Quae vero et similique debitis voluptatibus non et.\nEt fuga voluptate aut voluptas repellendus quasi.\nIllo eum et architecto molestiae quos.\nMolestiae quia odio rerum et ut laboriosam praesentium.\nVelit optio est exercitationem labore voluptatem amet qui.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=93.83690272750209",
            "viewCounts": 0,
            "createdAt": "2022-01-29T09:01:55.000Z",
            "updatedAt": "2022-01-29T09:01:55.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2022-01-29T09:01:55.000Z",
                "updatedAt": "2022-01-29T09:01:55.000Z"
            }
        },
        {
            "id": 38,
            "name": "Junior Eichmann",
            "tel": "209-678-3568",
            "address": "3558 Marilyne Estates",
            "opening_hours": "08:00",
            "description": "Aut quae corporis ut minus perferendis. Iure laudantium aut possimus perferendis. Porro libero tenetur asperiores aut sint hic quis ipsam expedita. Est praesentium eos animi recusandae deleniti nemo accusantium.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=72.90670490036773",
            "viewCounts": 0,
            "createdAt": "2022-01-29T09:01:55.000Z",
            "updatedAt": "2022-01-29T09:01:55.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2022-01-29T09:01:55.000Z",
                "updatedAt": "2022-01-29T09:01:55.000Z"
            }
        },
        {
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
            }
        },
        {
            "id": 32,
            "name": "Marcos Jerde",
            "tel": "(831) 605-2560",
            "address": "91024 Olson Track",
            "opening_hours": "08:00",
            "description": "qui expedita aut",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=43.09903938301169",
            "viewCounts": 0,
            "createdAt": "2022-01-29T09:01:55.000Z",
            "updatedAt": "2022-01-29T09:01:55.000Z",
            "CategoryId": 1,
            "Category": {
                "id": 1,
                "name": "中式料理",
                "createdAt": "2022-01-29T09:01:55.000Z",
                "updatedAt": "2022-01-29T09:01:55.000Z"
            }
        },
        {
            "id": 19,
            "name": "Cassandre Doyle",
            "tel": "285-782-1502 x91783",
            "address": "0901 Purdy Greens",
            "opening_hours": "08:00",
            "description": "Beatae culpa quidem quo et et eveniet nostrum aperiam.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=69.80835073515046",
            "viewCounts": 0,
            "createdAt": "2022-01-29T09:01:55.000Z",
            "updatedAt": "2022-01-29T09:01:55.000Z",
            "CategoryId": 2,
            "Category": {
                "id": 2,
                "name": "日本料理",
                "createdAt": "2022-01-29T09:01:55.000Z",
                "updatedAt": "2022-01-29T09:01:55.000Z"
            }
        },
        {
            "id": 18,
            "name": "Kennedy Smith",
            "tel": "597-436-3836",
            "address": "29431 Ozella Run",
            "opening_hours": "08:00",
            "description": "voluptatem consectetur autem",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=75.5313667222155",
            "viewCounts": 0,
            "createdAt": "2022-01-29T09:01:55.000Z",
            "updatedAt": "2022-01-29T09:01:55.000Z",
            "CategoryId": 3,
            "Category": {
                "id": 3,
                "name": "義大利料理",
                "createdAt": "2022-01-29T09:01:55.000Z",
                "updatedAt": "2022-01-29T09:01:55.000Z"
            }
        }
    ],
    "comments": [
        {
            "id": 15,
            "text": "Nostrum consequuntur ut vel eos ut omnis tempora et.",
            "UserId": 1,
            "RestaurantId": 15,
            "createdAt": "2022-01-29T09:01:55.000Z",
            "updatedAt": "2022-01-29T09:01:55.000Z",
            "User": {
                "id": 1,
                "name": "root",
                "email": "root@example.com",
                "password": "$2a$10$f9iezqnQrz8Yhgp7i28IY.Y/x9Wzz0bEllpvt2VQPfv8Xh.iPgIe6",
                "isAdmin": true,
                "image": null,
                "createdAt": "2022-01-29T09:01:55.000Z",
                "updatedAt": "2022-01-29T09:01:55.000Z"
            },
            "Restaurant": {
                "id": 15,
                "name": "Mitchell Littel",
                "tel": "636.728.9297 x26068",
                "address": "771 Louvenia Fall",
                "opening_hours": "08:00",
                "description": "Laboriosam sit omnis ea sit sunt aut et. Fugiat aperiam voluptatem iste reiciendis aut omnis. Aspernatur placeat est a nobis voluptatibus maiores voluptas.\n \rQui corrupti eius eum ullam dolores repudiandae. Natus vel doloremque tenetur cum incidunt quia. Vero sapiente hic voluptas dolor. Incidunt sit similique minus. Nobis quis velit et esse.\n \rIpsa est voluptatem est officiis porro sed. Et natus consequatur tenetur sit rerum eum tempora ut. Dolores amet temporibus et corrupti repudiandae vel et quia voluptas. Omnis sequi praesentium repellendus neque deserunt. Tempore voluptatem magnam.",
                "image": "https://loremflickr.com/320/240/restaurant,food/?random=51.1925675040676",
                "viewCounts": 0,
                "createdAt": "2022-01-29T09:01:55.000Z",
                "updatedAt": "2022-01-29T09:01:55.000Z",
                "CategoryId": 5
            }
        },
        {
            "id": 31,
            "text": "Et deleniti autem aperiam laborum aut quia.",
            "UserId": 1,
            "RestaurantId": 31,
            "createdAt": "2022-01-29T09:01:55.000Z",
            "updatedAt": "2022-01-29T09:01:55.000Z",
            "User": {
                "id": 1,
                "name": "root",
                "email": "root@example.com",
                "password": "$2a$10$f9iezqnQrz8Yhgp7i28IY.Y/x9Wzz0bEllpvt2VQPfv8Xh.iPgIe6",
                "isAdmin": true,
                "image": null,
                "createdAt": "2022-01-29T09:01:55.000Z",
                "updatedAt": "2022-01-29T09:01:55.000Z"
            },
            "Restaurant": {
                "id": 31,
                "name": "Jabari Wintheiser",
                "tel": "(849) 824-5897 x16050",
                "address": "4694 Vincent Garden",
                "opening_hours": "08:00",
                "description": "Voluptatibus ea distinctio explicabo qui non. Consequatur cupiditate est reiciendis ipsam. Recusandae deserunt consequatur et qui ipsam fugit. Occaecati iure ut expedita dicta.",
                "image": "https://loremflickr.com/320/240/restaurant,food/?random=52.00575873076308",
                "viewCounts": 0,
                "createdAt": "2022-01-29T09:01:55.000Z",
                "updatedAt": "2022-01-29T09:01:55.000Z",
                "CategoryId": 4
            }
        },
        {
            "id": 63,
            "text": "Id voluptatibus adipisci aut maxime quae eos voluptatem libero est.",
            "UserId": 1,
            "RestaurantId": 13,
            "createdAt": "2022-01-29T09:01:55.000Z",
            "updatedAt": "2022-01-29T09:01:55.000Z",
            "User": {
                "id": 1,
                "name": "root",
                "email": "root@example.com",
                "password": "$2a$10$f9iezqnQrz8Yhgp7i28IY.Y/x9Wzz0bEllpvt2VQPfv8Xh.iPgIe6",
                "isAdmin": true,
                "image": null,
                "createdAt": "2022-01-29T09:01:55.000Z",
                "updatedAt": "2022-01-29T09:01:55.000Z"
            },
            "Restaurant": {
                "id": 13,
                "name": "Adalberto Krajcik",
                "tel": "1-038-482-3536 x693",
                "address": "764 Kylee Springs",
                "opening_hours": "08:00",
                "description": "Et temporibus perspiciatis adipisci beatae id debitis excepturi. Voluptate ut quia est consequatur. Qui unde dolorem. Eos et beatae sed eum dolores voluptatem quia reprehenderit nobis.",
                "image": "https://loremflickr.com/320/240/restaurant,food/?random=77.59307837064256",
                "viewCounts": 0,
                "createdAt": "2022-01-29T09:01:55.000Z",
                "updatedAt": "2022-01-29T09:01:55.000Z",
                "CategoryId": 2
            }
        },
        {
            "id": 85,
            "text": "Sed a pariatur.",
            "UserId": 1,
            "RestaurantId": 35,
            "createdAt": "2022-01-29T09:01:55.000Z",
            "updatedAt": "2022-01-29T09:01:55.000Z",
            "User": {
                "id": 1,
                "name": "root",
                "email": "root@example.com",
                "password": "$2a$10$f9iezqnQrz8Yhgp7i28IY.Y/x9Wzz0bEllpvt2VQPfv8Xh.iPgIe6",
                "isAdmin": true,
                "image": null,
                "createdAt": "2022-01-29T09:01:55.000Z",
                "updatedAt": "2022-01-29T09:01:55.000Z"
            },
            "Restaurant": {
                "id": 35,
                "name": "Sonny Hoeger",
                "tel": "(937) 153-9944",
                "address": "123 Durgan Route",
                "opening_hours": "08:00",
                "description": "et",
                "image": "https://loremflickr.com/320/240/restaurant,food/?random=37.89203621468202",
                "viewCounts": 0,
                "createdAt": "2022-01-29T09:01:55.000Z",
                "updatedAt": "2022-01-29T09:01:55.000Z",
                "CategoryId": 5
            }
        },
        {
            "id": 100,
            "text": "Dolor fuga minima neque ullam et qui.",
            "UserId": 1,
            "RestaurantId": 50,
            "createdAt": "2022-01-29T09:01:55.000Z",
            "updatedAt": "2022-01-29T09:01:55.000Z",
            "User": {
                "id": 1,
                "name": "root",
                "email": "root@example.com",
                "password": "$2a$10$f9iezqnQrz8Yhgp7i28IY.Y/x9Wzz0bEllpvt2VQPfv8Xh.iPgIe6",
                "isAdmin": true,
                "image": null,
                "createdAt": "2022-01-29T09:01:55.000Z",
                "updatedAt": "2022-01-29T09:01:55.000Z"
            },
            "Restaurant": {
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
                "CategoryId": 5
            }
        },
        {
            "id": 130,
            "text": "Quia nam saepe quis earum praesentium.",
            "UserId": 1,
            "RestaurantId": 30,
            "createdAt": "2022-01-29T09:01:55.000Z",
            "updatedAt": "2022-01-29T09:01:55.000Z",
            "User": {
                "id": 1,
                "name": "root",
                "email": "root@example.com",
                "password": "$2a$10$f9iezqnQrz8Yhgp7i28IY.Y/x9Wzz0bEllpvt2VQPfv8Xh.iPgIe6",
                "isAdmin": true,
                "image": null,
                "createdAt": "2022-01-29T09:01:55.000Z",
                "updatedAt": "2022-01-29T09:01:55.000Z"
            },
            "Restaurant": {
                "id": 30,
                "name": "Sheldon Sipes",
                "tel": "151-027-7832",
                "address": "4778 Stokes Mountains",
                "opening_hours": "08:00",
                "description": "Et delectus deserunt. Qui eaque voluptatem labore. Quasi aut et. Optio sed voluptatem iusto sed expedita. Reiciendis occaecati quas velit.",
                "image": "https://loremflickr.com/320/240/restaurant,food/?random=54.39894349199459",
                "viewCounts": 0,
                "createdAt": "2022-01-29T09:01:55.000Z",
                "updatedAt": "2022-01-29T09:01:55.000Z",
                "CategoryId": 1
            }
        },
        {
            "id": 5,
            "text": "Ab in fugiat consequatur.",
            "UserId": 2,
            "RestaurantId": 5,
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
            },
            "Restaurant": {
                "id": 5,
                "name": "Rocky Abshire DVM",
                "tel": "(422) 049-8370",
                "address": "2347 Theodora Forge",
                "opening_hours": "08:00",
                "description": "Voluptatem expedita facilis.",
                "image": "https://loremflickr.com/320/240/restaurant,food/?random=73.57501562389443",
                "viewCounts": 0,
                "createdAt": "2022-01-29T09:01:55.000Z",
                "updatedAt": "2022-01-29T09:01:55.000Z",
                "CategoryId": 5
            }
        },
        {
            "id": 32,
            "text": "Architecto veniam quia sed asperiores amet.",
            "UserId": 2,
            "RestaurantId": 32,
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
            },
            "Restaurant": {
                "id": 32,
                "name": "Marcos Jerde",
                "tel": "(831) 605-2560",
                "address": "91024 Olson Track",
                "opening_hours": "08:00",
                "description": "qui expedita aut",
                "image": "https://loremflickr.com/320/240/restaurant,food/?random=43.09903938301169",
                "viewCounts": 0,
                "createdAt": "2022-01-29T09:01:55.000Z",
                "updatedAt": "2022-01-29T09:01:55.000Z",
                "CategoryId": 1
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
            },
            "Restaurant": {
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
                "CategoryId": 1
            }
        },
        {
            "id": 68,
            "text": "Dolor asperiores vel qui qui omnis.",
            "UserId": 2,
            "RestaurantId": 18,
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
            },
            "Restaurant": {
                "id": 18,
                "name": "Kennedy Smith",
                "tel": "597-436-3836",
                "address": "29431 Ozella Run",
                "opening_hours": "08:00",
                "description": "voluptatem consectetur autem",
                "image": "https://loremflickr.com/320/240/restaurant,food/?random=75.5313667222155",
                "viewCounts": 0,
                "createdAt": "2022-01-29T09:01:55.000Z",
                "updatedAt": "2022-01-29T09:01:55.000Z",
                "CategoryId": 3
            }
        }
    ]
}

export default {
  components: {
    NavTabs,
    NewestRestaurants,
    NewestComments
  },
  data() {
    return {
      restaurants: [],
      comments: [],
    }
  },
  methods: {
    fetchFeeds() {
      this.restaurants = dummyData.restaurants
      this.comments = dummyData.comments
    }
  },
  created() {
    this.fetchFeeds()
  }
}
</script>