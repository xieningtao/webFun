<template>
  <div class="article-container">
    <ul class="storyItemContainer">
      <li v-for="(story,index) in stories" class="markdown-body article-item">
        <!-- <div class="bg"></div> -->
        <div class="article-item-subcontainer">
          <!-- <span class="article-title">
            <strong>{{story.title}}</strong>
          </span>-->
          <img class="imgFun" :src="story.funUrl">
          <div class="article-content-expand" ref="article-content">
            <div
              class="article-content_inner"
              v-html="story.render"
              @select="select"
              @click="toPage($event,story,index)"
            ></div>
          </div>
          <div class="funStoryAction">
            <div class="actionItem funStoryPraise">
              <div class="actionContiner">
                <img class="actionImg" src="/src/assets/fun/praise.svg">
                <p>
                  <strong>222</strong>
                </p>
              </div>
            </div>
            <div class="actionItem funStoryView">
              <div class="actionContiner">
                <img class="actionImg" src="/src/assets/fun/views.svg">
                <p>
                  <strong>111</strong>
                </p>
              </div>
            </div>
            <div class="actionItemEnd funStoryComment">
              <div class="actionContiner">
                <img class="actionImg" src="/src/assets/fun/comment.svg">
                <p>
                  <strong>123</strong>
                </p>
              </div>
            </div>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
import "mavon-editor/dist/css/index.css";
export default {
  data() {
    return {
      pageSize: 10,
      pageNum: 0,
      stories: []
    };
  },
  mounted() {
    debugger;
    this.getStories();
  },
  methods: {
    select() {},
    getStories() {
      const query = Bmob.Query("FunnyStory");
      query.order("-updatedAt");
      query.limit(this.pageSize);
      query.skip(this.pageNum * this.pageSize);
      query
        .find()
        .then(res => {
          console.log(JSON.stringify(res));
          this.stories = res;
        })
        .catch(err => {
          console.log(err);
        });
    },
    toPage(event, story, index) {
      debugger;
      let routeData = this.$router.resolve({
        name: "funnyStoryDetail",
        params: { id: story.objectId }
      });
      window.open(routeData.href, "_blank");
    }
  }
};
</script>

<style>
.article-container {
  width: 80%;
  height: 80%;
  margin: 0px auto;
}

.storyItemContainer {
  list-style: none;
  padding-bottom: 20px;
  margin-top: 20px;
  padding-left: 0px;
}
.article-item {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  transition: 0.3s;
  width: 100%;
  margin-top: 20px;
  background-color: white;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  position: relative;
}

.bg {
  position: absolute;
  top: 0px;
  bottom: 0px;
  left: 0px;
  right: 0px;
  /* background: url("https://wx1.sinaimg.cn/mw690/006MWlXYly1g08faf50gmj30u0190kjo.jpg");  */
}
/* 高斯模糊 */
.bg-blur {
  width: 100%;
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  -webkit-filter: blur(15px);
  -moz-filter: blur(15px);
  -o-filter: blur(15px);
  -ms-filter: blur(15px);
  filter: blur(15px);
}

.article-title {
  font-size: 16px;
  color: #010101;
  margin-top: 10px;
  margin-bottom: 10px;
}
.article-content-collapse {
  font-size: 16px;
  color: gray;
  position: relative;
  height: 100px;
}

.article-content-expand {
  font-size: 16px;
  color: gray;
  position: relative;
  height: auto;
}
.article-item-subcontainer {
  background: white;
  padding: 10px;
}

/* .article-item-subcontainer:hover {
  background: lightsalmon;
} */

.article-content_inner {
  margin-right: 20px;
  margin-bottom: 20px;
  height: 100%;
  margin-right: 100px;
}

.article-content {
  font-size: 16px;
  color: gray;
}

.toggle {
  position: absolute;
  right: 10px;
  bottom: 10px;
}
.imgFun {
  position: absolute;
  right: 10px;
  top: 10px;
  width: 80px;
  height: auto;
}
.funStoryAction {
  width: 100%;
  height: 50px;
  border: solid 1px lightgray;
  border-top-width: 1px;
  border-left-width: 0px;
  border-right-width: 0px;
  border-bottom-width: 0px;
  padding-top: 10px;
  position: relative;
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: center;
}
.actionItem {
  height: 100%;
  line-height: 50px;
  flex-grow: 1;
  text-align: center;
  border: solid 1px lightgray;
  border-top-width: 0px;
  border-left-width: 0px;
  border-right-width: 1px;
  border-bottom-width: 0px;
  position: relative;
}
.actionItemEnd {
  height: 100%;
  line-height: 50px;
  flex-grow: 1;
  text-align: center;
  position: relative;
}
.actionContiner {
  width: 30%;
  margin: auto;
  display: flex;
  flex-direction: row;
  justify-content: center;
}
.funStoryAction p {
  left: 10px;
  position: relative;
  margin: 0px;
  align-self: center;
}
.actionImg {
  width: 40px;
  height: 40px;
  align-self: center;
}
</style>