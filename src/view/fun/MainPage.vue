<template>
  <div>
    <!--<img src="https://farm6.staticflickr.com/5591/15008867125_68a8ed88cc_m.jpg"-->
    <!--v-on:click="enargePic()" v-bind:class="{min:!clickPic,max:clickPic}"-->
    <!--/>-->
    <photo-bar :photos="photos"></photo-bar>
    <!-- <vue-preview :slides="slide1" @close="handleClose"></vue-preview> -->
    <photo-wall></photo-wall>
  </div>
</template>

<script>
import PhotoBar from "./PhotoBar.vue";
import PhotoWall from "./PhotoWall.vue";
export default {
  data() {
    return {
      msg: this.$route.params.tag,
      clickPic: false,
      show: false,
      photos: [
        {
          url:
            "https://wx1.sinaimg.cn/mw690/006MWlXYly1g0jnitgee4j31f724pb2b.jpg",
          content: "this is a test"
        },
        {
          url:
            "https://wx1.sinaimg.cn/mw690/006MWlXYly1g0eyy0ufmyj31741uo7wi.jpg",
          content: "this is a test A"
        },
        {
          url:
            "https://wx3.sinaimg.cn/mw690/006MWlXYly1g0amiowxwuj31jk2bchdu.jpg",
          content: "this is a test B"
        },
        {
          url:
            "https://wx3.sinaimg.cn/mw690/006MWlXYly1g0j027o2acj318g1oohdt.jpg",
          content: "this is a test C"
        },
        {
          url:
            "https://wx2.sinaimg.cn/mw690/006MWlXYly1g0j026tw8xj318g1ow7wh.jpg",
          content: "this is a test D"
        },
        {
          url:
            "https://wx1.sinaimg.cn/mw690/006MWlXYly1g08faf50gmj30u0190kjo.jpg",
          content: "this is a test F"
        },
        {
          url:
            "https://wx4.sinaimg.cn/mw690/006MWlXYly1g0is49k64bj31av2517wk.jpg",
          content: "this is a test E"
        },
        {
          url:
            "https://images.3ajiepai.com/data/attachment/forum/201903/11/144537jxu4u677s6t7e5k2.jpg",
          content: "this is a test G"
        }
      ],
      slide1: [
        {
          src:
            "https://farm6.staticflickr.com/5591/15008867125_68a8ed88cc_b.jpg",
          msrc:
            "https://farm6.staticflickr.com/5591/15008867125_68a8ed88cc_m.jpg",
          alt: "picture1",
          title: "Image Caption 1",
          w: 600,
          h: 400
        },
        {
          src:
            "https://farm4.staticflickr.com/3902/14985871946_86abb8c56f_b.jpg",
          msrc:
            "https://farm4.staticflickr.com/3902/14985871946_86abb8c56f_m.jpg",
          alt: "picture2",
          title: "Image Caption 2",
          w: 1200,
          h: 900
        }
      ]
    };
  },
  watch: {
    $route(to, from) {
      // 对路由变化作出响应...
      debugger;
      this.msg = this.$route.params.tag;
    }
  },
  methods: {
    enargePic() {
      this.clickPic = !this.clickPic;
      this.show = true;
    },
    handleClose() {
      this.show = false;
    }
  },
  components: {
    PhotoBar,
    PhotoWall
  }
};
</script>

<style>
img {
  transition: 2s;
}
.min {
  width: 200px;
  height: auto;
}

.max {
  width: 100%;
  height: auto;
}
</style>