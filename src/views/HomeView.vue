<template>
    <v-container fluid>
      <!-- Карусель -->
      <v-carousel>
        <v-carousel-item
          v-for="ad in ads"
          :key="ad.id"
          :src="ad.src"
          class="position-relative"
        >
          <v-btn
            class="position-absolute bottom-3 left-1/2 transform -translate-x-1/2"
            :to="'/ad/' + ad.id"
            color="error"
          >
            {{ ad.title }}
          </v-btn>
        </v-carousel-item>
      </v-carousel>
  
      <!-- Сетка карточек -->
      <v-row>
        <v-col
          v-for="ad in ads"
          :key="ad.id"
          :cols="12"
          :sm="6"
          :md="4"
          class="d-flex justify-center"
        >
          <v-card>
            <v-img :src="ad.src" height="200px" />
            <v-card-title>
              <div>
                <h3 class="headline mb-0">{{ ad.title }}</h3>
                <div>{{ ad.desc }}</div>
              </div>
            </v-card-title>
            <v-card-actions>
              <v-spacer />
              <v-btn text :to="'/ad/' + ad.id">Open</v-btn>
              <v-btn raised color="primary">Buy</v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </template>
  
  <script>
  export default {
    data() {
      return {
        ads: [
          {
            title: "First",
            desc: "First Desc",
            promo: true,
            src: "https://cdn.vuetifyjs.com/images/carousel/squirrel.jpg",
            id: "1"
          },
          {
            title: "Second",
            desc: "Second Desc",
            promo: true,
            src: "https://cdn.vuetifyjs.com/images/carousel/sky.jpg",
            id: "2"
          },
          {
            title: "Third",
            desc: "Third Desc",
            promo: true,
            src: "https://cdn.vuetifyjs.com/images/carousel/bird.jpg",
            id: "3"
          },
          {
            title: "Fourth",
            desc: "Fourth Desc",
            promo: true,
            src: "https://cdn.vuetifyjs.com/images/carousel/planet.jpg",
            id: "4"
          }
        ]
      };
    }
  };
  </script>
  
  <style scoped>
  /* Стили для кнопки в карусели */
  .v-carousel-item .v-btn {
    position: absolute;
    bottom: 50px;
    left: 50%;
    transform: translateX(-50%);
    background: rgba(0, 0, 0, 0.5);
    padding: 5px 15px;
    border-radius: 5px;
  }
  </style>
  