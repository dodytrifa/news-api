<template>
  <div class="home">
    
    <h1 class="text-center mt-5">
      News API
    </h1>
    <div class="container mt-5">
      <div class="row">
        <div class="card m-5" style="width: 18rem;">
          <img src="https://static.foxnews.com/foxnews.com/content/uploads/2021/05/AP21131583136649.jpg" class="card-img-top" alt="newsimage">
          <div class="card-body">
            <h5 class="card-title mb-5">{{title}}</h5>
            <p class="card-text mb-5" >{{description}}</p>
            <p class="card-text">Author by: {{author}}</p>
            <p class="card-text">Published at: {{publish}}</p>
            <a href="https://www.foxnews.com/health/fauci-says-pandemic-exposed-undeniable-effects-of-racism-in-us" class="btn btn-primary">Link to news</a>
          </div>
        </div>
      
        
        <div class="card m-5" style="width: 18rem;">
          <img src="https://cdn.vox-cdn.com/thumbor/FUBnOQy1UelVvCn9seiRj6joA0E=/0x816:3600x2701/fit-in/1200x630/cdn.vox-cdn.com/uploads/chorus_asset/file/22519419/1232691427.jpg" class="card-img-top" alt="newsimage">
            <div class="card-body">
            <h5 class="card-title mb-5">{{title1}}</h5>
            <p class="card-text mb-5" >{{description1}}</p>
            <p class="card-text">Author by: {{author1}}</p>
            <p class="card-text">Published at: {{publish1}}</p>
          <a href="https://www.goldenstateofmind.com/2021/5/16/22439643/warriors-will-lakers-in-opening-round-of-nba-play-in-tournament" class="btn btn-primary">Link to news</a>
          </div>
        </div>

        <div class="card m-5" style="width: 18rem;">
          <img src="https://imagesvc.meredithcorp.io/v3/mm/image?q=85&c=sc&poi=%5B466%2C40%5D&w=1333&h=667&url=https%3A%2F%2Fstatic.onecms.io%2Fwp-content%2Fuploads%2Fsites%2F20%2F2021%2F05%2F17%2FMiss-Universe_7.jpg" class="card-img-top" alt="newsimage">
          <div class="card-body">
            <h5 class="card-title mb-5">{{title2}}</h5>
              <p class="card-text mb-5" >{{description2}}</p>
              <p class="card-text">Author by: {{author2}}</p>
              <p class="card-text">Published at: {{publish2}}</p>
              <a href="https://people.com/human-interest/miss-universe-winner-2020-miss-mexico/" class="btn btn-primary">Link to news</a>
          </div>
        </div>
        
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
  components: {
  },
  data() {

  },
  methods: {
    async fetchNews() {
      const res = await fetch('https://newsapi.org/v2/top-headlines?country=us&apiKey=8fc8c42fbe254d6da393a3b98c166efa')
      const data = await res.json()
      return data
    }
  },
  async created(){
    const data = await this.fetchNews()

    this.name = data.articles[0].source.name
    this.author = data.articles[0].author
    this.title = data.articles[0].title
    this.description = data.articles[0].description
    this.url = data.articles[0].url
    this.urlToImage = data.articles[0].urlToImage
    this.publish = data.articles[0].publishedAt 

    this.name1 = data.articles[1].source.name
    this.author1 = data.articles[1].author
    this.title1 = data.articles[1].title
    this.description1 = data.articles[1].description
    this.url1 = data.articles[1].url
    this.urlToImage1 = data.articles[1].urlToImage
    this.publish1 = data.articles[1].publishedAt

    this.name2 = data.articles[2].source.name
    this.author2 = data.articles[2].author
    this.title2 = data.articles[2].title
    this.description2 = data.articles[2].description
    this.url2 = data.articles[2].url
    this.urlToImage2 = data.articles[2].urlToImage
    this.publish2 = data.articles[2].publishedAt

  }
}
</script>

<style scoped>
body {
  background-color: aquamarine;
}
</style>