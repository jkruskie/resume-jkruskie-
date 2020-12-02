<template>
  <v-card
    color="grey lighten-4"
    light
  >
    <v-card-text>
      <content-section
        title="Who am I?"
      >
        I am a hard-working web developer who strives to create elegant solutions across the web. I've developed a wide variety of software,
        all the way from an automotive dealership CRM, state organization websites, and Augmentative and Alternative Communication (AAC)
        applications for nonverbal individuals.
      </content-section>
      <content-section
        v-if="prouds"
        title="What am I proud of?"
      >
        <v-layout
          v-for="(proud, i) in prouds"
          :key="i"
        >
          <v-flex
            md1
            xs3
          >
            <v-icon right>
              {{ proud.icon }}
            </v-icon>
          </v-flex>
          <v-flex
            md11
            xs9
          >
            <p>
              <strong>{{ proud.text }}</strong><br>
              <small>{{ proud.source }}</small>
            </p>
          </v-flex>
        </v-layout>
      </content-section>
      <content-section
        v-if="experiences"
        title="Experiences"
      >
        <v-layout
          v-for="(experience, i) in experiences"
          :key="i"
        >
          <v-flex md4>
            {{ experience.from }} - {{ experience.to }}
          </v-flex>
          <v-flex md8>
            <strong v-if="experience.employer">{{ experience.employer }}</strong>
            <div v-if="experience.title">
              <i>{{ experience.title }}</i>
            </div>
            <div v-if="experience.description">
              {{ experience.description }}
            </div>
          </v-flex>
        </v-layout>
      </content-section>
      <content-section
        v-if="educations"
        title="Education"
      >
        <v-layout
          v-for="(education, i) in educations"
          :key="i"
        >
          <v-flex md4>
            {{ education.from }} - {{ education.to }}
          </v-flex>
          <v-flex md8>
            <strong v-if="education.title">{{ education.title }}</strong>
            <div v-if="education.location">
              <i>{{ education.location }}</i>
            </div>
            <div v-if="education.description">
              {{ education.description }}
            </div>
          </v-flex>
        </v-layout>
      </content-section>
      <content-section
        v-if="skills"
        id="to-timeline"
        title="Skills"
      >
        <template slot="actions">
          (% are relative not absolute)
        </template>
        <v-layout wrap>
          <template
            v-for="(skill, i) in skills"
          >
            <v-flex
              v-if="skill.divider"
              :key="i"
              md12
              xs12
              mb-4
            />
            <v-flex
              v-else
              :key="i"
              md6
              xs12
            >
              <div
                class="mr-2 ml-2"
              >
                <div class="align-center">
                  <v-icon
                    small
                  >
                    {{ skill.icon }}
                  </v-icon>
                  {{ skill.title }}
                </div>
                <v-progress-linear
                  class="progress"
                  color="secondary"
                  height="3"
                  :value="skill.value"
                />
              </div>
            </v-flex>
          </template>
        </v-layout>
      </content-section>
    </v-card-text>
  </v-card>
</template>

<script>
import ContentSection from '@/views/dark-template/content/Section'
export default {
  name      : 'MainContent',
  components: { ContentSection },
  data      : () => ({
    prouds: [
      {
        icon  : 'mdi-trophy',
        text  : '2nd, 6th, & 8th in Nation for Business Professionals of America in 2018-19',
        source: '(Web Application Team, Software Engineering Team, & Mobile Application Development)',
      },
      {
        icon  : 'mdi-medal',
        text  : 'Top 10 for A.H. Nickless Innovation Award Nicholas in 2019',
        source: '(https://ahninnovationaward.com)',
      },
    ],
    experiences: [
      {
        from       : 'August, 2020',
        to         : 'Current',
        employer   : 'McNally-Nimergood Crane Rentals',
        title      : 'Yard Worker',
        description: 'Primary responsibilities include loading and offloading construction equipment, light maintenance work on machines, and building maintenance.  ',
      },
      {
        from       : 'September, 2019',
        to         : 'August, 2020',
        employer   : 'NetSource One, Inc.',
        title      : 'Programmer I',
        description: 'Primary responsibilities include the creation of monitoring and scripts to create automation within a wide variety of systems. Regular use of Powershell, Python, ConnectWise Automate.',
      },
      {
        from       : 'July, 2016',
        to         : 'August, 2019',
        employer   : 'Essexville-Hampton Public Schools',
        title      : 'Network Technician',
        description: 'Primary responsibilities include maintaining, troubleshooting, and repairing computer systems, classroom technologies, and VMs.',
      },
      {
        from       : 'April, 2018',
        to         : 'April, 2019',
        employer   : 'Newtech Automotive Services',
        title      : 'Junior Developer',
        description: 'Primary responsibilities include creation of web applications using Laravel and database management. Regular use of HTML, CSS, JS, PHP, SQL, and jQuery.',
      },
    ],
    educations: [
      {
        from       : '2019',
        to         : '2023 (not finished yet)',
        title      : 'Bachelor\'s degree, Computer Science',
        location   : 'Saginaw Valley State University',
        description: 'Study Computer Science and Software Development',
      },
      {
        from       : '2017',
        to         : '2019',
        title      : 'Graduated',
        location   : 'Bay-Arenac ISD Career Center',
        description: 'Computer Programming',
      },
      {
        from       : '2015',
        to         : '2019',
        title      : 'Diploma',
        location   : 'Garber High School',
        description: '',
      },
    ],
    skills: [
      {
        title: 'PHP',
        icon : 'mdi-language-php',
        value: 95,
      },
      {
        title: 'JavaScript',
        icon : 'mdi-language-javascript',
        value: 80,
      },
      {
        title: 'Laravel Framework',
        icon : 'mdi-laravel',
        value: 90,
      },
      {
        title: 'Wordpress',
        icon : 'mdi-wordpress',
        value: 90,
      },
      {
        title: 'Vue.js Framework',
        icon : 'mdi-vuejs',
        value: 50,
      },
      {
        title: 'Python',
        icon : 'mdi-language-python',
        value: 60,
      },
      {
        title: 'Powershell',
        icon : 'mdi-powershell',
        value: 60,
      },
      { divider: true },
      {
        title: 'Ubuntu Server',
        icon : 'mdi-ubuntu',
        value: 70,
      },
      {
        title: 'Windows Server',
        icon : 'mdi-ubuntu',
        value: 65,
      },
      {
        title: 'Web Application Security',
        icon : 'mdi-shield-lock',
        value: 80,
      },
      {
        title: 'Git',
        icon : 'mdi-git',
        value: 67,
      },
      {
        title: 'Web Applications',
        icon : 'mdi-application',
        value: 67,
      },
    ],
  }),
}
</script>

<style scoped>
.title {
  border-bottom: 2px #bfbfbf solid;
  line-height: 1.5 !important;
}
.progress {
  margin-top: 0.1rem;
}
</style>
