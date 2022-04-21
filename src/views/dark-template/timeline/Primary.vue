<template>
  <v-card
    color="grey lighten-4"
    light
  >
    <v-card-text>
      <content-section
        id="timeline"
        :title="detailed ? 'My Life in a Nutshell' : 'My Experiences'"
      >
        <template slot="actions">
          <div>
            <v-switch
              v-model="detailed"
              :label="detailed ? 'Detailed' : 'Summary'"
            />
          </div>
        </template>

        <v-timeline
          dense
        >
          <v-timeline-item
            v-for="(item, i) in orderedItems"
            :key="i"
            :icon="item.icon || ''"
            :class="{transparent: item.transparent}"
            large
          >
            <template
              v-if="item.iconImage"
              v-slot:icon
            >
              <v-avatar>
                <img
                  :src="publicPath(item.iconImage)"
                >
              </v-avatar>
            </template>
            <template v-slot:opposite />
            <v-layout>
              <v-flex
                v-if="$vuetify.breakpoint.smAndUp"
                md1
                sm2
                align-self-center
              >
                <span>{{ item.year }}</span>
              </v-flex>
              <v-flex
                md11
                sm10
                xs12
              >
                <v-card class="elevation-1">
                  <v-card-title class="pb-0">
                    <div>
                      <p v-if="$vuetify.breakpoint.xsOnly">
                        {{ item.year }}
                      </p>
                      <h3>{{ item.title }}</h3>
                    </div>
                  </v-card-title>
                  <v-card-text>
                    <v-layout wrap>
                      <v-flex
                        :md7="!!item.image"
                        :md12="!item.image"
                        xs12
                      >
                        <div class="mr-1">
                          <span
                            v-if="item.text"
                            class="pre"
                          >{{ item.text }}</span>
                          <!-- eslint-disable vue/no-v-html -->
                          <div
                            v-else-if="item.html"
                            v-html="item.html"
                          />
                          <!-- eslint-enable vue/no-v-html -->
                        </div>
                      </v-flex>
                      <v-flex
                        v-if="item.image"
                        md5
                        xs12
                      >
                        <div
                          class="mt-2"
                        >
                          <v-carousel
                            v-if="Array.isArray(item.image)"
                            :show-arrows="false"
                            :height="325"
                          >
                            <v-carousel-item
                              v-for="(citem,ci) in item.image"
                              :key="ci"
                              :src="publicPath(citem)"
                            />
                          </v-carousel>
                          <v-img
                            v-else
                            :max-height="item.imageHeight ? item.imageHeight : ''"
                            :src="publicPath(item.image)"
                          />
                        </div>
                      </v-flex>
                    </v-layout>
                  </v-card-text>
                </v-card>
              </v-flex>
            </v-layout>
          </v-timeline-item>
        </v-timeline>
      </content-section>
    </v-card-text>
  </v-card>
</template>

<script>
import ContentSection from '@/views/dark-template/content/Section'
export default {
  name      : 'Timeline',
  components: { ContentSection },
  data      : () => ({
    detailed: true,
    items   : [
      {
        detailed   : false,
        transparent: false,
        year       : '2000',
        title      : 'Born',
        html       : 'With a chance of %0.00000000000512.<br>I\'m completely aware of the value of life!',
        icon       : 'mdi-cake-variant',
      },
      {
        detailed   : false,
        transparent: false,
        year       : '2005',
        title      : 'Broke my first cmputer',
        html       : 'ME: "Oof"<br><i>... Of course got slapped later!</i>',
        icon       : 'mdi-desktop-classic',
      },
      {
        detailed   : false,
        year       : '2018',
        transparent: false,
        title      : 'Started VoicedAAC.com',
        html       : `
                <p>
                    I started at the Bay-Arenac ISD Career Center not knowing anything about programming. Near the end of the year I was one of the top students in my class. My teacher offered me the opportunity to develop an
                    application for nonverbal students... I told him yes.
                </p>
                <p>
                  Back then, I was scared to say yes to things that challenged me; however, now I embrace them. I took this idea and am still slowing trying to develop this.
                </p>
                <p>
                    During 2018 - 2019, this project has had a few interactions with the community:
                    <ul>
                        <li>
                            <a href="https://www.secondwavemedia.com/baycity/features/students-develop-app-help-nonverbal-students.aspx"</a> First public article about this project
                        </li>
                        <li>
                            <a href="https://www.facebook.com/macul.org/photos/a.1974200719284286/1983942458310112/?type=3&theater"</a> MACUL Student Technology Showcase
                        </li>
                    </ul>
                </p>
        `,
        image      : 'img/timeline/voiced-ipad.png',
        imageHeight: 300,
        icon       : 'mdi-web',
      },
      {
        detailed   : false,
        transparent: false,
        year       : '2019',
        title      : 'First "professional" camera',
        html       : 'Purchased a used Sony A6000, the beginning of a photography obsession.',
        icon       : 'mdi-camera',
      },
      {
        detailed   : false,
        transparent: false,
        year       : '2020',
        title      : 'Sports photography hobby',
        html       : 'Discovered I have a passion for sports photography. Started shooting high school sports in my free time.',
        icon       : 'mdi-film',
      },
      {
        detailed   : false,
        transparent: false,
        year       : '2022',
        title      : 'First picture published',
        html       : 'Mlive.com published my very first sports picture from a local high school basketball game. <br><a>https://www.mlive.com/highschoolsports/2022/02/bay-city-boys-roundup-with-gritty-play-glenn-finally-gets-close-one-to-go-its-way.html</a>',
        icon       : 'mdi-film',
      },
      {
        detailed   : false,
        transparent: false,
        year       : '2022',
        title      : 'First photography job',
        html       : 'Joined the student ran news paper at Saginaw Valley State University as a photographer, specializing in sports. This allowed me to shoot my first district 3 basketball game!',
        icon       : 'mdi-film',
      },
    ],
  }),
  computed: {
    orderedItems () {
      const items = [...this.items].reverse()
      if (this.detailed)
        return items
      return items.filter((item) => {
        return !item.detailed
      })
    },
  },
}
</script>

<style scoped>
.title {
  border-bottom: 2px #bfbfbf solid;
  line-height: 1.5 !important;
}
.pre {
  white-space: pre;
}
.transparent{
  opacity: 0.6;
}
</style>
