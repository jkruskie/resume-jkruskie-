<template>
  <v-card
    color="grey darken-3"
    dark
  >
    <v-card-text>
      <avatar />
      <div class="text-sm-center mb-4 mt-3">
        <h1>
          Justin <span class="light-blue--text text--lighten-3">Kruskie</span>
        </h1>
        <span>
          A challenge-loving web developer
        </span>
      </div>

      <sidebar-section :options="sections.info" />
      <sidebar-section :options="sections.socials" />
      <sidebar-section :options="sections.hobbies">
        <template v-slot:item="{ item }">
          <v-chip>
            <v-avatar>
              <v-icon>
                {{ item.icon }}
              </v-icon>
            </v-avatar>
            {{ item.text }}
          </v-chip>
        </template>
      </sidebar-section>
      <sidebar-section :options="sections.references">
        <template v-slot:items="{ items }">
          <v-container pa-0>
            <v-layout
              wrap
              class="text-xs-center"
            >
              <template v-for="(item, i) in items">
                <v-flex
                  :key="i"
                  md6
                  sm6
                  xs6
                >
                  <h3>{{ item.name }}</h3>
                  <p style="margin-bottom:.5rem;">
                    {{ item.position }}
                  </p>
                  <p style="margin-bottom:.5rem;">
                    {{ item.email }}
                  </p>
                  <p style="margin-bottom:.5rem;">
                    {{ item.phone }}
                  </p>
                </v-flex>
              </template>
            </v-layout>
          </v-container>
        </template>
      </sidebar-section>
    </v-card-text>
  </v-card>
</template>

<script>
import Avatar from '@/views/dark-template/sidebar/Avatar'
import SidebarSection from '@/views/dark-template/sidebar/Section'
export default {
  name      : 'Sidebar',
  components: { SidebarSection, Avatar },
  data () {
    return {
      sections: {
        info: {
          title: 'INFO',
          items: [
            {
              name: 'Email',
              icon: 'mdi-email',
              text: 'justin@kruskie.net',
            },
            {
              name: 'Website',
              icon: 'mdi-web',
              text: 'jkruskie.com',
            },
            {
              name: 'Location',
              icon: 'mdi-map-marker',
              text: 'Bay City, MI',
            },
          ],
        },
        socials: {
          title: 'SOCIALS',
          items: [
            {
              icon: 'mdi-github-circle',
              text: 'github.com/jkruskie',
              link: 'https://github.com/jkruskie',
            },
            {
              icon: 'mdi-linkedin-box',
              text: 'linkedin.com/in/justinkruskie',
              link: 'https://linkedin.com/in/justinkruskie',
            },
            {
              icon: 'mdi-facebook-box',
              text: 'facebook.com/jkruskie',
              link: 'https://www.facebook.com/jkruskie',
            },
            {
              icon: 'mdi-camera-iris',
              text: 'facebook.com/justinkruskiephotography',
              link: 'https://www.facebook.com/justinkruskiephoto',
            },
            {
              icon: 'mdi-camera',
              text: 'instagram.com/justinkruskiephoto',
              link: 'https://www.instagram.com/justinkruskiephoto',
            },
          ],
        },
        hobbies: {
          title: 'HOBBIES',
          items: [
            {
              icon: 'mdi-code-tags',
              text: 'Expertise in .NET Development',
            },
            {
              icon: 'mdi-cloud',
              text: 'Proficient in Azure Cloud Services',
            },
            {
              icon: 'mdi-bullseye',
              text: 'Problem-Solving Skills',
            },
            {
              icon: 'mdi-biohazard',
              text: 'Technical Challenges Enthusiast',
            },
            {
              icon: 'mdi-image-filter-hdr',
              text: 'Appreciation for Nature',
            },
            {
              icon: 'mdi-auto-fix',
              text: 'Tech Enthusiast and Hacker',
            },
            {
              icon: 'mdi-swim',
              text: 'Swimming as a Fitness Pursuit',
            },
            {
              icon: 'mdi-music',
              text: 'Passion for Music',
            },
            {
              icon: 'mdi-sleep',
              text: 'Emphasis on Quality Rest',
            },
            {
              icon: 'mdi-camera',
              text: 'Devoted Sports Photographer',
            },
          ],
        },
        references: {
          title: 'REFERENCES',
          items: [
            {
              name    : 'Jesse Dockett',
              position: 'Bay City Commissioner',
              email   : 'jdockett@gmail.com',
              phone   : '(989) 493-0656',
            },
            {
              name    : 'George Corser',
              position: 'CS Professor, SVSU',
              email   : 'gpcorser@svsu.edu',
              phone   : '(989) 964-2756',
            },
          ],
        },
      },
    }
  },
}
</script>

<style scoped>
.sidebar {
  background: #2e2e2e;
}
</style>
