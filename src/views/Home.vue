<template>
  <div class="main_contents mx-auto">    
    <div v-if="!loading" >
      <v-card elevation="2" outlined shaped max-width="700" class="mx-auto">
        <v-container>
          <v-row class="home-about__contents">
            <v-col  class="home-about__contents-img">
              <img :src="profile.icon.url" alt="icon" class="img-fluid" style="border-radius: 30px">
            </v-col>
            <v-col class="mx-auto" style="color:#333c5e">
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

      <div  style="font-size: 25px; padding-top:30px; padding-bottom:10px; color:#333c5e">
        <b>Products</b>
      </div>

      <v-card outlined max-width="600" class="mx-auto">
        <v-container>
          <v-row>
            <v-col v-for="article in articles" :key="article.id" style="font-size: 20px;text-align:left;color:#333c5e" >
              <a :href=article.product_link.link target="_blank">
                <v-img
                  class="white--text align-end indigo lighten-5"
                  :src="article.image.url"
                  style="border: solid "
                /> 
              </a>
              <v-card-text >
                <div style="font-size:20px;padding-bottom:10px"><b>{{ article.title }}</b></div>
                <div >{{ article.summary }}</div>
                <div class="pt-5" style="font-size:18px"><b>Link</b></div>
                <div v-for="link in article.links" :key="link.id">
                  <a
                    class="blue--text text-lighten-1"
                    target="_blank"
                    :href=link.link
                  >
                    {{link.name}}
                  </a>
                </div>
                <v-container>
                  <v-row>
                    <div v-for="tag in article.tags" :key="tag.id" class="pt-3">
                      <div class="text-body-2 grey lighten-2 px-2 py-1 mr-3 my-2" style="border-radius: 40px">
                        <b>{{tag.name}}</b>
                      </div>
                    </div>
                  </v-row>
                </v-container>

              </v-card-text>
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
    console.log(this.articles)
    this.loading = false
  },
}
</script>
<style scoped>

.main_contents{

}

.home-about__contents {
  margin-top: 3px;
  margin-bottom: 3px;
}
</style>
