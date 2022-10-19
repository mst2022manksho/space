
<template>
  <div class="container">
    <div class="notification p-3 m-3">
      <h3 class="is-size-4 has-text-centered">Nasa APOD</h3>
      <span>title: {{ title }}</span>
      <br />
      <span>copyright: {{ copyright }}</span>

      <h3
        v-if="images.length === 0 && !loading"
        class="is-size-5 my-2 has-text-danger has-text-centered"
      >
        No Images Found on Pixabay
      </h3>
      <b-loading
        :is-full-page="isFullPage"
        v-model="loading"
        :can-cancel="true"
      ></b-loading>
      <b-field class="my-2"> </b-field>
      <div class="card my-3">
        <div class="card-image">
          <figure class="image is-16by9">
            <img
              :src="images"
              alt="Placeholder image"
              height="400"
              width="700"
            />
          </figure>
        </div>
        <div class="card-content">
          <span>explanation: {{ des }}</span>
        </div>
      </div>
          <div class="adsbygoogle">
      <Adsense
        data-ad-client="ca-pub-6305863275081549"
        data-ad-slot="4202572180"
        data-ad-format="fluid"
        style="display: block"
        data-ad-layout-key="-fb+5w+4e-db+86"
        :data-full-width-responsive="true"
      >
      </Adsense>
    </div>

      <b-carousel>
        <!--         <b-carousel-item v-for="(carousel, i) in images" :key="i">
          <div class="card my-3">
            <div class="card-image">
              <figure class="image is-16by9">
                <img
                  :src="carousel.webformatURL"
                  alt="Placeholder image"
                  height="400"
                  width="700"
                />
              </figure>
            </div>
            <div class="card-content">
              <div class="media">
                <div class="media-content">
                  <p class="title is-4">
                  </p>
                  <b-button
                    type="is-danger"
                    icon-left="eye"
                    class="mr-2"
                  >
                  </b-button>
                  <b-button
                    type="is-primary"
                    icon-left="thumbs-up"
                    class="mr-2"
                  >
                  </b-button>
                  <b-button
                    type="is-dark"
                    icon-left="comments"
                    class="mr-2"
                  >
                  </b-button>
                  <b-button type="is-success" class="mr-2" icon-left="tags">
                  </b-button>
                </div>
              </div>
            </div>
          </div>
        </b-carousel-item>
 -->
      </b-carousel>
    </div>
  </div>
  
</template>
<script>
export default {
  name: "ImagesPage",
  data() {
    return {
      images: "",
      des: "",
      copyright: "",
      term: "nature",
      date: "",
      title: "",
      isFullPage: true,
      loading: true,
    };
  },
  mounted() {
    this.getPixabayImages();
  },
  methods: {
    getPixabayImages() {
      this.loading = false;
      // Flickr requests
      fetch(
        `https://api.nasa.gov/planetary/apod?api_key=iT7UUWa3UpkZUDO23Fn444YKYcNMGAR6OTj2rwf5`
        //`https://api.nasa.gov/insight_weather/?api_key=${process.env.VUE_APP_PIXABAY_API_KEY}&feedtype=json&ver=1.0`
      )
        .then((res) => res.json())
        .then((data) => {
          this.images = data.hdurl;
          this.des = data.explanation;
          this.copyright = data.copyright;
          this.date = data.date;
          this.title = data.title;
          console.log(this.images);
        })
        .catch((err) => console.log(err));
    },
  },
};
</script>

