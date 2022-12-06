<template>
  <div>
    <div>
      <button @click="authorizeVk">Авторизироваться вк</button>
    </div>
    <div>
      <button @click="makeRepost">Сделать репост поста</button>
    </div>
    <!-- <div id="vk_like">LikeWidget</div> -->
    <div id="vk_post_-33118207_31542974" />
  </div>
</template>

<script>
export default {
  name: "HomeView",
  data() {
    return {
      user_data: null,
      postId: "https://vk.com/warface?w=wall-33118207_31542974",
    };
  },
  mounted() {
    // window.VK.Widgets.Like("vk_like");

    window.VK.Widgets.Post(
      "vk_post_-33118207_31542974",
      -33118207,
      31542974,
      "abDsTwDfTr9Ep_uoNWXMziQgQpwA"
    );
    // It is not working
    window.VK.Observer.subscribe("widgets.post.shared", () => {
      console.log("widgets.post.shared");
      alert("Thank you for your shared.");
    });
  },
  methods: {
    authorizeVk() {
      console.log("authorizeVk");
      this.user_data = window.VK.Auth.login();
    },
    makeRepost() {
      // TODO I can't find desired method
      window.VK.Api.call(
        "stories.save",
        {
          // eslint-disable-next-line
          v: "5.73",
          upload_results:
            "https://sun3-12.userapi.com/impg/WhGj_BnshuacWE8dAZvPtoRKQcpzHHtFg5vq8g/veSUdVx3_Ng.jpg?size=1080x1080&quality=95&sign=43524f9d9201c7e961a23fd09eb2a06d&type=album",
        },
        function (res) {
          if (res.response) {
            alert(res.response);
          }
        }
      );
    },
  },
};
</script>

<style scoped lang="scss">
.title {
  font-size: 32px;
}
</style>
