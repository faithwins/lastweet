<template>
  <div class="tweep" @click="clicked">
    <img
      class="Avatar"
      data-src-2x="https://pbs.twimg.com/profile_images/432081479/DOI_LOGO_bigger.jpg"
      alt
      data-src-1x="https://pbs.twimg.com/profile_images/432081479/DOI_LOGO_normal.jpg"
      :src="tweep.profile_image_url"
    />
    <div class="TweetAuthor js-inViewportScribingTarget">
      <div class="TweetAuthor-nameScreenNameContainer">
        <span class="TweetAuthor-decoratedName">
          <span class="TweetAuthor-name Identity-name customisable-highlight">{{tweep.name}}</span>
          <span v-show="tweep.verified" class="TweetAuthor-verifiedBadge">
            <div class="Icon Icon--verified" aria-label="Verified Account" role="img"></div>
            <b class="u-hiddenVisually">✔</b>
          </span>
        </span>
        <span class="TweetAuthor-screenName Identity-screenName" dir="ltr">@{{tweep.screen_name}}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    tweep: {
      type: Object,
      required: true,
      default: {
        id: "",
        name: "",
        screen_name: "",
        location: "",
        description: "",
        profile_image_url: "",
        verified: false,
        status: ""
      }
    }
  },
  methods: {
    clicked() {
      this.$emit("click", this.tweep);
    }
  }
};
</script>

<style scoped>
.tweep {
  display: -webkit-box;
  display: -webkit-flex;
  display: -moz-box;
  display: -ms-flexbox;
  display: flex;
  padding: 10px;
  margin: 2px;
  border-radius: 0.5em;
  border-color: #1da1f2;
  cursor: pointer;
}
.tweep:hover {
  border: thin solid #1da1f2;
  border-radius: 0.5em;
  cursor: pointer;
}
.Avatar {
  max-width: 100%;
  max-height: 100%;
  border-radius: 50%;
}

.Avatar--fill {
  width: 100%;
  height: 100%;
}
img {
  border: 0;
}
.TweetAuthor {
  display: -webkit-box;
  display: -webkit-flex;
  display: -moz-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
  -webkit-flex-direction: column;
  -moz-box-orient: vertical;
  -moz-box-direction: normal;
  -ms-flex-direction: column;
  flex-direction: column;
  overflow: hidden;
  width: -webkit-min-content;
  width: -moz-min-content;
  width: min-content;
}
.TweetAuthor-nameScreenNameContainer {
  display: -webkit-box;
  display: -webkit-flex;
  display: -moz-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
  -webkit-flex-direction: column;
  -moz-box-orient: vertical;
  -moz-box-direction: normal;
  -ms-flex-direction: column;
  flex-direction: column;
  line-height: 1.2;
  -webkit-box-align: start;
  -webkit-align-items: flex-start;
  -moz-box-align: start;
  -ms-flex-align: start;
  align-items: flex-start;
  min-width: 0;
}
.TweetAuthor-decoratedName {
  display: -webkit-box;
  display: -webkit-flex;
  display: -moz-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-align: center;
  -webkit-align-items: center;
  -moz-box-align: center;
  -ms-flex-align: center;
  align-items: center;
  min-width: 0;
}
.TweetAuthor-name {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  padding-right: 4px;
}

.Identity-name {
  font-weight: 700;
}

.Identity-screenName {
  color: #697882;
}

.TweetAuthor-nameScreenNameContainer {
  display: -webkit-box;
  display: -webkit-flex;
  display: -moz-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
  -webkit-flex-direction: column;
  -moz-box-orient: vertical;
  -moz-box-direction: normal;
  -ms-flex-direction: column;
  flex-direction: column;
  line-height: 1.2;
  -webkit-box-align: start;
  -webkit-align-items: flex-start;
  -moz-box-align: start;
  -ms-flex-align: start;
  align-items: flex-start;
  min-width: 0;
}

.TweetAuthor-screenName {
  font-size: 14px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  -webkit-flex-shrink: 1;
  -ms-flex-negative: 1;
  flex-shrink: 1;
}
.TweetAuthor-verifiedBadge {
  position: static;
  -webkit-box-flex: 0;
  -webkit-flex: none;
  -moz-box-flex: 0;
  -ms-flex: none;
  flex: none;
  padding-right: 4px;
}

.Icon {
  display: inline-block;
  height: 1.25em;
  background-repeat: no-repeat;
  background-size: contain;
  vertical-align: text-bottom;
}
.Icon--verified {
  width: 1.11111em;
  background-image: url(data:image/svg+xml;charset=utf-8,%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20viewBox%3D%220%200%2064%2072%22%3E%3Cpath%20fill%3D%22none%22%20d%3D%22M0%200h64v72H0z%22%2F%3E%3Cpath%20fill%3D%22%231da1f2%22%20d%3D%22M3%2037.315c0%204.125%202.162%207.726%205.363%209.624-.056.467-.09.937-.09%201.42%200%206.103%204.72%2011.045%2010.546%2011.045%201.295%200%202.542-.234%203.687-.686C24.22%2062.4%2027.827%2064.93%2032%2064.93c4.174%200%207.782-2.53%209.49-6.213%201.148.45%202.39.685%203.69.685%205.826%200%2010.546-4.94%2010.546-11.045%200-.483-.037-.953-.093-1.42C58.83%2045.04%2061%2041.44%2061%2037.314c0-4.37-2.42-8.15-5.933-9.946.427-1.203.658-2.5.658-3.865%200-6.104-4.72-11.045-10.545-11.045-1.302%200-2.543.232-3.69.688-1.707-3.685-5.315-6.216-9.49-6.216-4.173%200-7.778%202.53-9.492%206.216-1.146-.455-2.393-.688-3.688-.688-5.827%200-10.545%204.94-10.545%2011.045%200%201.364.23%202.662.656%203.864C5.42%2029.163%203%2032.944%203%2037.314z%22%2F%3E%3Cpath%20fill%3D%22%23FFF%22%20d%3D%22M17.87%2039.08l7.015%206.978c.585.582%201.35.873%202.116.873.77%200%201.542-.294%202.127-.883.344-.346%2015.98-15.974%2015.98-15.974%201.172-1.172%201.172-3.07%200-4.243-1.17-1.17-3.07-1.172-4.242%200l-13.87%2013.863-4.892-4.868c-1.174-1.168-3.074-1.164-4.242.01-1.168%201.176-1.163%203.075.01%204.244z%22%2F%3E%3C%2Fsvg%3E);
}
.u-hiddenVisually {
  position: absolute !important;
  overflow: hidden !important;
  width: 1px !important;
  height: 1px !important;
  padding: 0 !important;
  border: 0 !important;
  clip: rect(1px, 1px, 1px, 1px) !important;
}
</style>