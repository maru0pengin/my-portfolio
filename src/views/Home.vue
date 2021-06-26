<template>
  <div class="main_contents mx-auto">    
    <div v-if="!loading" >
      <v-card  class="mx-auto">
        <v-container>
          <v-row class="home-about__contents">
            <v-col md="5" class="home-about__contents-img">
              <img :src="profile.icon.url" alt="icon" class="img-fluid" style="border-radius: 30px">
            </v-col>
            <v-col md="5" class="mx-auto" style="font-weight: bold; color:#333c5e">
              <div style="font-size: 20px">
                {{profile.name}}
              </div>
              <div>
                生年月日：{{profile.birthday}}
              </div>
              <div style="font-size: 13px;text-align:left;padding:12px 0px;">
                {{profile.summary}}
              </div>
              <v-container>
                <v-row>
                  <div v-for="link in profile.links" :key="link.id">
                    <v-col>
                      <v-btn
                        :href=link.link
                        elevation="2"
                        style="text-transform: none;font-weight: bold"
                      >
                        {{link.name}}
                      </v-btn>
                    </v-col>
                  </div>
                </v-row>
              </v-container>
            </v-col>
          </v-row>
        </v-container>
      </v-card>

      <div  style="font-size: 25px; padding-top:20px">
        <b>Products</b>
      </div>

      <v-card >
        <v-container>
          <v-row>
            <v-col v-for="article in articles" :key="article.id">
              <v-img
                class="white--text align-end"
                height="200px"
                :src="article.image.url"
              />
              <div style="font-size: 20px">
                {{ article.title }}
              </div>
              <v-card-text class="text--primary">
                <div class="summary">{{ article.summary }}</div>
              </v-card-text>

              <v-card-actions>
                <v-btn color="orange" text>More</v-btn>
              </v-card-actions>

            </v-col>
          </v-row>
        </v-container>
      </v-card>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Home',

  data: () => ({
    articles: [],
    profile: {},
    loading: true,
  }),

  async mounted() {
    // 記事を取得する
    let response = await axios
      .get('https://maru0pengin.microcms.io/api/v1/products', {
        headers: { 'X-API-KEY': process.env.VUE_APP_X_API_KEY },
      })
      .catch((e) => console.log(e))
      
    this.articles = response.data.contents

    response = await axios
      .get('https://maru0pengin.microcms.io/api/v1/profile', {
        headers: { 'X-API-KEY': process.env.VUE_APP_X_API_KEY },
      })
      .catch((e) => console.log(e))
    console.log(response)
    this.profile = response.data
    console.log(this.profile)
    this.loading = false
  },
}
</script>
<style scoped>

.main_contents{
  width:700px
}

.home-about__contents {
  margin-top: 3px;
  margin-bottom: 3px;
}
</style>
