<template>
  <div>
    <b-container>
      <b-row>
        <b-col cols=3>
          <b-list-group>
            <b-list-group-item href="#" v-for="(url, index) in videoids" :key="index" @click="currentVideoNumber=index" :class="index===currentVideoNumber?'active':'notactive'">{{index}}</b-list-group-item>
          </b-list-group>
        </b-col>
        <b-col cols=9><video preload="false" allow="autoplay" controls="true" :src="'https://drive.google.com/uc?id='+videoids[currentVideoNumber]" @canplaythrough="arguments[0].target.play()" @ended="videoNext" @error="videoNext" @click="onClick"></video></b-col>
      </b-row>
    </b-container>
  </div>
</template>
<script>
import axios from 'axios'

export default {
  data() {
    return {
      videoids: [],
      currentVideoNumber: 0,
    }
  },
  async asyncData() {
    let data = [];
    try {
      data = (await axios({
        url: "http://o99920au.beget.tech/api/video",
        method: "get",
        headers:{'user-agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/71.0.3578.98 Safari/537.36'}
      })).data;
    } catch (er) {
      console.dir(er);
    }
    return { videoids: (data) };
  },
  methods: {
    videoNext: function() {
      this.videoids.length === this.currentVideoNumber + 1 ? this.currentVideoNumber = 0 : ++this.currentVideoNumber
    },
    onClick: function(e) {
      if (e.target.paused) {
        e.target.play();
      } else {
        e.target.pause();
      }
    },
  },
  created: function() {}
}

</script>
<style lang="less" scoped>
video {
  display: block;
  margin: 10px 0;
  width: 100%;
}

.container {
  padding-top: 50px;
  padding-bottom: 50px;
}

</style>
