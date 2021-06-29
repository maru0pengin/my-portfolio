<template>
  <div v-if="!loading"  class="mx-auto">    

    <v-card elevation="2" outlined shaped max-width="800" class="mx-auto">
      <v-container>
        <v-row class="home-about__contents px-2">
          <v-col  class="my-auto" md="5">
            <img :src="profile.icon.url" alt="icon" class="img-fluid" style="border-radius: 35px">
          </v-col>
          <v-col  class="mx-auto" style="color:#333c5e" md="7">
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
                  <v-col >
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

    <div class="font-weight-bold text-h4 pt-8 pb-2" style="color:#333c5e">
      Products
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
                <v-row class="pt-3">
                  <div v-for="tag in article.tags" :key="tag.id" >
                    <div class="text-body-2 grey lighten-2 px-2 py-1 mr-3 my-2 rounded-pill">
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
    <div class="font-weight-bold text-h4 pt-8 pb-2" style="color:#333c5e">
      Skill
    </div>
    <v-card outlined max-width="600" class="mx-auto">
      <v-container>
        <v-row>
          <v-col v-for="article in articles" :key="article.id" style="font-size: 20px;text-align:left;color:#333c5e" >
            <v-card-text >
              <div class="text-h5"><b>プログラミング言語・フレームワーク</b></div>
              <hr>
                <v-row>
                  <v-col cols="5" class="subtitle-1 my-2">
                    AtCoder
                  </v-col> 
                  <v-col>
                    <v-container>
                      <v-row >
                          <div class="text-body-2 grey lighten-2 px-2 py-1 mr-3 my-2 font-weight-bold rounded-pill">
                            Python
                          </div>

                      </v-row>
                    </v-container>
                  </v-col> 
                </v-row>
              <hr>
                <v-row>
                  <v-col cols="5" class="subtitle-1 my-2">
                    個人開発
                  </v-col> 
                  <v-col>
                    <v-container>
                      <v-row >
                          <div class="text-body-2 grey lighten-2 px-2 py-1 mr-3 my-2 font-weight-bold rounded-pill">
                            JavaScript
                          </div>
                          <div class="text-body-2 grey lighten-2 px-2 py-1 mr-3 my-2 font-weight-bold rounded-pill">
                            Vue.js
                          </div>
                          <div class="text-body-2 grey lighten-2 px-2 py-1 mr-3 my-2 font-weight-bold rounded-pill">
                            Ruby on Rails
                          </div>
                      </v-row>
                    </v-container>
                  </v-col> 
                </v-row>
              <hr>
                <v-row>
                  <v-col cols="5" class="subtitle-1 my-2">
                    長期インターンシップ
                  </v-col> 
                  <v-col>
                    <v-container>
                      <v-row >
                          <div class="text-body-2 grey lighten-2 px-2 py-1 mr-3 my-2 font-weight-bold rounded-pill">
                            TypeScript
                          </div>
                          <div class="text-body-2 grey lighten-2 px-2 py-1 mr-3 my-2 font-weight-bold rounded-pill">
                            Svelte
                          </div>
                          <div class="text-body-2 grey lighten-2 px-2 py-1 mr-3 my-2 font-weight-bold rounded-pill">
                            tailwind
                          </div>
                      </v-row>
                    </v-container>
                  </v-col> 
                </v-row>
              <hr>
                <v-row>
                  <v-col cols="5" class="subtitle-1 my-2">
                    講義・研究
                  </v-col> 
                  <v-col>
                    <v-container>
                      <v-row >
                          <div class="text-body-2 grey lighten-2 px-2 py-1 mr-3 my-2 font-weight-bold rounded-pill">
                            C
                          </div>
                          <div class="text-body-2 grey lighten-2 px-2 py-1 mr-3 my-2 font-weight-bold rounded-pill">
                            C++
                          </div>
                          <div class="text-body-2 grey lighten-2 px-2 py-1 mr-3 my-2 font-weight-bold rounded-pill">
                            R
                          </div>
                          <div class="text-body-2 grey lighten-2 px-2 py-1 mr-3 my-2 font-weight-bold rounded-pill">
                            Java
                          </div>
                          <div class="text-body-2 grey lighten-2 px-2 py-1 mr-3 my-2 font-weight-bold rounded-pill">
                            Verilog
                          </div>
                      </v-row>
                    </v-container>
                  </v-col> 
                </v-row>
              <hr>
              <div class="text-h5 pt-7 "><b>ソフトウェア・インフラ</b></div>
              <hr>
                <v-row>
                  <v-col cols="5" class="subtitle-1 my-2">
                    個人開発<br/>
                    長期インターンシップ
                  </v-col> 
                  <v-col>
                    <v-container>
                      <v-row >
                        <div class="text-body-2 grey lighten-2 px-2 py-1 mr-3 my-2 font-weight-bold rounded-pill">
                          Firebase
                        </div>
                        <div class="text-body-2 grey lighten-2 px-2 py-1 mr-3 my-2 font-weight-bold rounded-pill">
                          AWS Cognito
                        </div>
                      </v-row>
                    </v-container>
                  </v-col> 
                </v-row>
                <hr>
                <v-row>
                  <v-col cols="5" class="subtitle-1 my-2">
                    趣味
                  </v-col> 
                  <v-col>
                    <v-container>
                      <v-row >
                        <div class="text-body-2 grey lighten-2 px-2 py-1 mr-3 my-2 font-weight-bold rounded-pill">
                          CLIP STUDIO PAINT
                        </div>
                      </v-row>
                    </v-container>
                  </v-col> 
                </v-row>
              <hr>
              <div class="text-h5 pt-7"><b>資格</b></div>
              <hr>
                <v-row>
                  <v-col cols="5" class="subtitle-1 my-2">
                    情報処理技術者試験
                  </v-col> 
                  <v-col>
                    <v-container>
                      <v-row >
                        <div class="text-body-2 grey lighten-2 px-2 py-1 mr-3 my-2 font-weight-bold rounded-pill">
                          応用情報技術者試験
                        </div>
                      </v-row>
                    </v-container>
                  </v-col> 
                </v-row>

              <hr>
            </v-card-text >
          </v-col> 
        </v-row>
      </v-container>
    </v-card>

    <div class="font-weight-bold text-h4 pt-8 pb-2" style="color:#333c5e">
      創作活動
    </div>
    <v-card outlined max-width="600" class="mx-auto">
      <v-container>
        <v-row>
          <v-col v-for="article in articles" :key="article.id" style="font-size: 20px;text-align:left;color:#333c5e" >
            <v-card-text >
              <div class="text-h5"><b>イラスト提供</b></div>
              <hr>
                <v-row>
                  <v-col cols="5" class="subtitle-1 my-2">
                    歌ってみた動画
                  </v-col> 
                  <v-col>
                    <v-container>
                      <v-row >
                        <div class="px-2 py-1 mr-3 my-2 font-weight-bold rounded-pill">
                          <a
                            class="blue--text text-lighten-1"
                            target="_blank"
                            href="https://www.youtube.com/watch?v=pAZuhdTqObI"
                          >
                            残酷な天使のテーゼ Covered by 塩天使リエル
                          </a>
                        </div>
                      </v-row>
                    </v-container>
                  </v-col> 
                </v-row>
              <hr>
  
              <div class="text-h5 pt-7"><b>ノベルゲーム制作</b></div>
                <hr>
                  <v-row>
                    <v-col cols="5" class="subtitle-1 my-2">
                      こと国シスターズ<br/>(キャラクターデザイン)
                    </v-col> 
                    <v-col>
                      <v-container>
                        <v-row >
                          <div class="px-2 py-1 mr-3 my-2 font-weight-bold rounded-pill">
                            <a
                              class="blue--text text-lighten-1"
                              target="_blank"
                              href="https://nutrients20190227.wixsite.com/kotsis2020"
                            >
                              こと国シスターズ！！
                            </a>
                          </div>
                        </v-row>
                      </v-container>
                    </v-col> 
                  </v-row>
                <hr>
                  <v-row>
                    <v-col cols="5" class="subtitle-1 my-2">
                      凪の恋<br/>(キャラクターデザイン)
                    </v-col> 
                    <v-col>
                      <v-container>
                        <v-row >
                          <div class="px-2 py-1 mr-3 my-2 font-weight-bold rounded-pill">
                            <a
                              class="blue--text text-lighten-1"
                              target="_blank"
                              href="https://nutrients20190227.wixsite.com/naginokoi/%E4%BA%BA%E7%89%A9%E7%B4%B9%E4%BB%8B"
                            >
                              凪の恋
                            </a>
                          </div>
                        </v-row>
                      </v-container>
                    </v-col> 
                  </v-row>
                <hr>
            </v-card-text >
          </v-col> 
        </v-row>
      </v-container>
    </v-card>
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
      
    this.articles = response.data.contents

    response = await axios
      .get('https://maru0pengin.microcms.io/api/v1/profile', {
        headers: { 'X-API-KEY': process.env.VUE_APP_X_API_KEY },
      })
    this.profile = response.data
    
    this.loading = false
  },
}
</script>
<style scoped>


.home-about__contents {
  margin-top: 3px;
  margin-bottom: 3px;
}

</style>
