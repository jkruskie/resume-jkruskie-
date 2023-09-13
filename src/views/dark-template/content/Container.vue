<template>
  <v-card
    color="grey lighten-4"
    light
  >
    <v-card-text>
      <content-section title="Who am I?">
        I'm a dedicated technology enthusiast with a strong background in web application development, automation, and
        system administration. My portfolio includes crafting automotive dealership CRM systems, delivering fullstack web
        solutions for the petroleum industry, and creating Augmentative and Alternative Communication (AAC) applications
        for nonverbal individuals.
        My expertise lies in fullstack web development, with a focus on ASP.NET Core/.NET. I'm driven by the constant
        pursuit of knowledge and enjoy embracing new challenges. Beyond my technical pursuits, I have a creative outlet in
        sports photography, capturing special moments in time.
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
          <template v-for="(skill, i) in skills">
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
              <div class="mr-2 ml-2">
                <div class="align-center">
                  <v-icon small>
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
        icon  : 'mdi-application',
        text  : 'WeServe Mobile App Developer',
        source: "Developer for Saginaw Valley State University's WeServe volunteer application",
      },
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
        from       : 'Jun 2023',
        to         : 'Present',
        employer   : 'J & J Diversified LLC',
        title      : 'Co-Founder',
        description: 'Co-founded J & J Diversified LLC, specializing in advanced software solutions for tank monitoring, site commissions, and commander backups & monitoring. Streamlined operations, enhanced safety, and ensured reliable backup and monitoring for petroleum storage and distribution processes.',
      },
      {
        from       : 'Jan 2022',
        to         : 'Present',
        employer   : 'J. Kruskie, LLC',
        title      : 'Owner',
        description: 'As a self-employed professional, I offer comprehensive expertise in photography, IT services, and programming. Services include capturing memorable moments through photography, providing IT consulting, troubleshooting, cybersecurity, and developing high-quality web solutions for diverse needs.',
      },
      {
        from       : 'May 2022',
        to         : 'Present',
        employer   : 'Saginaw Valley State University',
        title      : 'Intern Photographer for University Communications',
        description: 'Intern Photographer at SVSU University Communications. Responsibilities include capturing campus events, sports, and student candids, engaging the university community through vibrant visuals, collaborating with the team for desired visual narrative, editing images for brand standards and impact, and providing high-quality photos for publications and digital platforms.',
      },
      {
        from       : 'Feb 2022',
        to         : 'Present',
        employer   : 'The Valley Vanguard',
        title      : 'Photo & Design Editor',
        description: 'Photo & Design Editor at The Valley Vanguard, SVSU Student Newspaper. Led photo and design efforts for the student newspaper, created captivating visuals to enhance storytelling, collaborated with writers and editors for visual cohesion, implemented creative design concepts for print and digital platforms, captured compelling images to accompany news articles, and oversaw photo editing and retouching processes.',
      },
      {
        from       : 'May 2020',
        to         : 'May 2022',
        employer   : 'McNally-Nimergood Co.',
        title      : 'Yard Worker',
        description: 'Yard Worker at McNally-Nimergood Co., responsible for equipment loading, maintenance, and rigging. Proficient in loading and offloading equipment using cranes and telehandlers, cleaning and servicing equipment, gathering rigging and equipment for upcoming jobs, ensuring efficient organization and inventory management in the yard, collaborating with team members to optimize workflow and safety protocols, and assisting with general maintenance tasks.',
      },
      {
        from       : 'Sep 2019',
        to         : 'Jul 2020',
        employer   : 'NetSource One',
        title      : 'Programmer I',
        description: 'Programmer I at NetSource One. Collaborated with clients and team members to develop scripts and automation for system and software uptime, self-managed work activities to meet plans, monitored progress, and reported status. Utilized Microsoft 365 applications, including Automate and SharePoint, for streamlined processes, regularly employed ConnectWise Manage, CW Automate, Python, Visual Basic, C#, and PowerShell, and contributed to the enhancement of system efficiency and automation.',
      },
      {
        from       : 'Jul 2016',
        to         : 'Aug 2019',
        employer   : 'Essexville-Hampton Public Schools',
        title      : 'Network Technician',
        description: 'Network Technician at Essexville-Hampton Public Schools. Responsible for troubleshooting and repairing hardware and software for classroom devices, maintaining and managing servers and virtual machines, deploying new classroom technologies to enhance learning experiences, assisting with network infrastructure maintenance and optimization, providing technical support to educators and staff members, and ensuring reliable connectivity and efficient operation of school systems.',
      },
      {
        from       : 'Apr 2018',
        to         : 'Apr 2019',
        employer   : 'Newtech Dealer Services',
        title      : 'Junior Developer',
        description: 'Junior Developer at Newtech Dealer Services. Planned and developed web applications using Laravel framework, customized themes, and developed plugins to enhance website functionality, managed databases for efficient data storage and retrieval, contributed to mobile app development using Ionic framework, and regularly utilized HTML, CSS, JavaScript, PHP, SQL, and jQuery. Collaborated with team members to deliver high-quality solutions.',
      },
    ],

    educations: [
      {
        from       : '2019',
        to         : '(Expected Graduation: 2023)',
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
        title: '.NET Development',
        icon : 'mdi-language-csharp',
        value: 95,
      },
      {
        title: 'Azure Cloud Services',
        icon : 'mdi-cloud',
        value: 90,
      },
      {
        title: 'Web Application Security',
        icon : 'mdi-shield-lock',
        value: 85,
      },
      {
        title: 'Laravel Framework',
        icon : 'mdi-laravel',
        value: 90,
      },
      {
        title: 'WordPress Development',
        icon : 'mdi-wordpress',
        value: 90,
      },
      {
        title: 'JavaScript',
        icon : 'mdi-language-javascript',
        value: 80,
      },
      {
        title: 'React Framework',
        icon : 'mdi-react',
        value: 70,
      },
      {
        title: 'Python Programming',
        icon : 'mdi-language-python',
        value: 50,
      },
      {
        title: 'PowerShell Scripting',
        icon : 'mdi-powershell',
        value: 60,
      },
      {
        title: 'React Native App Development',
        icon : 'mdi-react',
        value: 50,
      },
      { divider: true },
      {
        title: 'Ubuntu Server Administration',
        icon : 'mdi-ubuntu',
        value: 70,
      },
      {
        title: 'Windows Server Administration',
        icon : 'mdi-windows',
        value: 70,
      },
      {
        title: 'Git Version Control',
        icon : 'mdi-git',
        value: 65,
      },
      {
        title: 'Sports Photography',
        icon : 'mdi-camera',
        value: 75,
      },
      {
        title: 'Music Enthusiast',
        icon : 'mdi-music',
        value: 70,
      },
      {
        title: 'Emphasis on Quality Rest',
        icon : 'mdi-sleep',
        value: 75,
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
