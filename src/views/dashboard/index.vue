<template>
  <div class="dashboard-container">
    <component v-bind:is="currentRole">
    </component>
  </div>
</template>

<script>
    import { mapGetters } from 'vuex';
    import AdminDashboard from './admin/index'
    import StudentDashboard from './student/index'
    import DefaultDashboard from './default/index'

    export default {
      name: 'dashboard',
      components: {AdminDashboard, StudentDashboard, DefaultDashboard},
      data() {
        return {
          currentRole: 'StudentDashboard'
        };
      },
      computed: {
        ...mapGetters([
          'name',
          'roles'
        ])
      },
      created() {
        if (this.roles.indexOf('student') >= 0) {
          return;
        }
        this.currentRole = 'AdminDashboard';
      }
    };
</script>

<style rel="stylesheet/scss" lang="scss">
.dashboard {
  &-container {
    margin: 30px;
  }
  &-text {
    font-size: 30px;
    line-height: 46px;
  }
}
</style>
