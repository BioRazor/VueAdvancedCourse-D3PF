<template lang="pug">
  .skills-wrapper.mt-5
    h2.font-diablo Skills
    hr.bg-white
    b-nav(pills small)
      b-nav-item(
        :active="!isPassiveSkillsActive"
        @click="changeComponent('ActiveSkills')"
      ) Active
      b-nav-item(
        :active="isPassiveSkillsActive"
        @click="changeComponent('PassiveSkills')"
      ) Passive
    keep-alive
      component(:is="activeComponent" :skills="componentProps")
</template>
<script>
export default {
  name: 'HeroSkills',
  components: {
    ActiveSkills: () =>
      import(/* webpackChunkName: "ActiveSkills" */ './ActiveSkills'),
    PassiveSkills: () =>
      import(/* webpackChunkName: "PassiveSkills" */ './PassiveSkills')
  },
  data () {
    return {
      activeComponent: 'ActiveSkills'
    }
  },
  props: {
    skills: {
      required: true,
      type: Object
    }
  },
  computed: {
    /**
     * Dinamyc props for async dynamic components
     * @returns {String}
     */
    // Con esto estamos generando "props" dinámicas
    // Si el componente es ActiveSkills pasa como props las activas, si no, las pasivas
    componentProps () {
      return this.activeComponent === 'ActiveSkills'
        ? this.skills.active
        : this.skills.passive
    },
    // Nos dice si el componente "HabilidadesPasivas" está activo o no
    isPassiveSkillsActive () {
      return this.activeComponent === 'PassiveSkills'
    }
  },
  methods: {
    changeComponent (component) {
      this.activeComponent = component
    }
  }
}
</script>
