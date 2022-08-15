<template>
  <div>{{ title}}
  </div>
</template>

<script>

export default {
  name: 'IndexPage',
  data() {
    return {
      title: ''
    }
  },
  created() {
    this.getTitle()
  },
  methods: {
    async getTitle() {
      let strapiTitle = await fetch('http://localhost:1337/api/hellos')
        .then(response => response.json())
        .then(result => result.data[0].attributes.title)
      console.log(strapiTitle)
      this.title = strapiTitle;
    }
  }

}
</script>
