<template>
  <div>
    <div class="search-bar">
      <input type="text" placeholder="Search Here" />
      <i class="fas fa-search icon"></i>
    </div>
    <ul class="list-divided mt-4">
      <li class="courses flex items-center px-4 py-3" v-for="course in courses" :key="course.id">
        <div>{{ course.title }} </div>
        <div> 
          <nuxt-link class="button-solid button-orange mx-auto" :to="`/admin/courses/${course.id}`"> Edit</nuxt-link>
        </div>
      </li>
    </ul>
    <nuxt-link class="button-solid button-orange mx-auto mt-4" to="/admin/courses/add"> Create Course </nuxt-link>
  </div>
</template>


<script lang="ts">
import Vue from 'vue';
import { mapGetters, mapActions } from 'vuex';
import Button from '@/components/Base/Button.vue';

export default Vue.extend({
  components: {},
  mounted() {
    this.fetchCourses()
  },
  computed: {
    ...mapGetters({
      courses: 'courses/list'
    })
  },
  methods: {
    ...mapActions({
      fetchCourses: 'courses/fetchAll'
    })
  }
})
</script>
