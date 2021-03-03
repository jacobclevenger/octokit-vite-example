<script setup lang="ts">
import { ref } from 'vue'
import { Octokit } from '@octokit/rest'

const repos = ref({})
const octokit = new Octokit()

octokit.repos
  .listForOrg({
    org: 'vitejs'
  })
  .then(({ data }) => {
    repos.value = data
  })

</script>

<template>
  <div>
    <div v-for="repo in repos">
      {{repo.name}}
    </div>
  </div>
</template>
