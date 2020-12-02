<template>
<v-container>
    <v-row class="text-center">
      <v-col class="mb-4">
        <h1 class="display-2 font-weight-bold mb-3">
          検索結果
        </h1>
        <p>
          検索キーワード: {{ $route.params.keyword }}
        </p>
      </v-col>

      <v-col 
      mb-5
      xs12
      
      >

      <!-- <v-card
    max-width="1000"
    class="mx-auto"
  >
    <v-system-bar
      color="pink darken-2"
      dark
    >
      <v-spacer></v-spacer>

      <v-icon>mdi-window-minimize</v-icon>

      <v-icon>mdi-window-maximize</v-icon>

      <v-icon>mdi-close</v-icon>
    </v-system-bar>

    <v-app-bar
      dark
      color="pink"
    >
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>My Music</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>
    </v-app-bar>

    <v-container>
      <v-row dense> -->

        <!-- <v-col
          v-for="(item, i) in items"
          :key="i"
          cols="12"
        > -->
        <div style="margin-bottom:10px" v-for="(album, i) in albums" :key="i">
          <v-card
            color="black"
            dark
            :href="album.collectionViewUrl"
          >
            <div class="d-flex flex-no-wrap justify-space-between">
              <div>
                <v-card-title
                  class="headline"
                  v-text="album.collectionName"
                ></v-card-title>

                <v-card-subtitle v-text="album.artistName"></v-card-subtitle>
              </div>

              <v-avatar
                class="ma-3"
                size="250"
                tile
              >
                <v-img :src="album.artworkUrl100"></v-img>
              </v-avatar>
            </div>
          </v-card>
          </div>
        <!-- </v-col> -->
      <!-- </v-row>
    </v-container>
  </v-card>-->
      </v-col>
    </v-row>
  </v-container> 
</template>

<script>
import axios from 'axios'

export default {
  data(){
    return {
      albums: [],
    }
  },
  created(){
     const vm = this
    axios.get(`https://itunes.apple.com/search?term=${this.$route.params.keyword}&entity=album`)
    .then(response => {
      console.log(response);
      vm.albums = response.data.results
    })
  }
}
</script>