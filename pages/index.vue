<template>
  <IndexTemplate :items="items" />
</template>

<script>
import Vue from 'vue'
import axios from 'axios'
import IndexTemplate from '~/components/templates/IndexTemplate/IndexTemplate.vue'

export default Vue.extend({
  name: 'IndexLandingPage',
  components: {
    IndexTemplate,
  },
  async asyncData() {
    const { data } = await axios.get(
      'https://intkaaa.microcms.io/api/v1/entry',
      {
        headers: { 'X-API-KEY': process.env.API_KEY },
      }
    )
    return {
      items: data.contents,
    }
  },
  data() {
    return {
      items: [],
    }
  },
})
</script>
