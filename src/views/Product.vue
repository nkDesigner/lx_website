<template>
  <div class="product">
    <banner img="../assets/img/bgtop.jpg" />
    <div class="product-content" v-loading="loading">
      <!-- <div class="p-video">
        <video-player
          class="video-player vjs-custom-skin"
          ref="videoPlayer"
          :playsinline="true"
          :options="playerOptions"
        ></video-player>
      </div> -->
      <div class="lacking">
        <h3 class="title">APS</h3>
        <div class="lacking-bottom">
          <div class="lacking-bottom-item">
            <div class="lacking-bottom-item-img">
              <img src="../assets/img/product-group-icon_3.png" alt />
            </div>
            <p>智能聊天对话</p>
          </div>

          <div class="lacking-bottom-item">
            <div class="lacking-bottom-item-img">
              <img src="../assets/img/product-group-icon_2.png" alt />
            </div>
            <p>备忘录</p>
          </div>

          <div class="lacking-bottom-item">
            <div class="lacking-bottom-item-img">
              <img src="../assets/img/product-group-icon_1.png" alt />
            </div>
            <p>账号密码</p>
          </div>
        </div>
      </div>
      <!-- 平台目标 -->
      <div class="target">
        <h3 class="title">后台管理</h3>
        <div class="target-img">
          <img src="../assets/img/product_group_3_img.png" alt />
        </div>
      </div>
      <!--功能模块  -->
      <div class="modular">
        <h3 class="title">AAV</h3>
        <div class="modular-content">
          <div class="modular-content-same">
            <div class="same-item">
              <div class="same-item-img">
                <img src="../assets/img/product-group_4-icon_1.png" alt />
              </div>
              <p>商品管理模块</p>
            </div>
            <div class="same-item">
              <div class="same-item-img">
                <img src="../assets/img/product-group_4-icon_2.png" alt />
              </div>
              <p>订单模块模块</p>
            </div>
            <div class="same-item">
              <div class="same-item-img">
                <img src="../assets/img/product-group_4-icon_3.png" alt />
              </div>
              <p>订单支付模块</p>
            </div>
            <div class="same-item">
              <div class="same-item-img">
                <img src="../assets/img/product-group_4-icon_1.png" alt />
              </div>
              <p>VIP专区模块</p>
            </div>
          </div>
          <div class="modular-content-center">
            <img src="../assets/img/product_group_4_img.png" alt />
          </div>
          <div class="modular-content-same">
            <div class="same-item">
              <p>账号权限模块</p>
              <div class="same-item-img">
                <img src="../assets/img/product-group_4-icon_5.png" alt />
              </div>
            </div>
            <div class="same-item">
              <p>统一认证模块</p>
              <div class="same-item-img">
                <img src="../assets/img/product-group_4-icon_6.png" alt />
              </div>
            </div>
            <div class="same-item">
              <p>日志监控模块</p>
              <div class="same-item-img">
                <img src="../assets/img/product-group_4-icon_7.png" alt />
              </div>
            </div>
            <div class="same-item">
              <p>任务调度模块</p>
              <div class="same-item-img">
                <img src="../assets/img/product-group_4-icon_8.png" alt />
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Banner from "../components/Banner";
export default {
  data() {
    return {
      loading: true,
      videoSrc: "http://www.shkjem.com/video/kj.mp4",
      playerOptions: {
        playbackRates: [0.5, 1.0, 1.5, 2.0, 4.0, 8.0], //可选择的播放速度
        autoplay: false, //如果true,浏览器准备好时开始回放。
        muted: false, // 默认情况下将会消除任何音频。
        loop: false, // 视频一结束就重新开始。
        preload: "auto", // 建议浏览器在<video>加载元素后是否应该开始下载视频数据。auto浏览器选择最佳行为,立即开始加载视频（如果浏览器支持）
        language: "zh-CN",
        aspectRatio: "16:9", // 将播放器置于流畅模式，并在计算播放器的动态大小时使用该值。值应该代表一个比例 - 用冒号分隔的两个数字（例如"16:9"或"4:3"）
        fluid: true, // 当true时，Video.js player将拥有流体大小。换句话说，它将按比例缩放以适应其容器。
        sources: [
          {
            type: "",
            src: "http://www.shkjem.com/video/kj.mp4" //url地址
          }
        ],
        //poster: "../assets/img/home_top.jpg", //你的封面地址
        // width: document.documentElement.clientWidth,
        notSupportedMessage: "此视频暂无法播放，请稍后再试", //允许覆盖Video.js无法播放媒体源时显示的默认信息。
        controlBar: {
          timeDivider: true, //当前时间和持续时间的分隔符
          durationDisplay: true, //显示持续时间
          remainingTimeDisplay: false, //是否显示剩余时间功能
          fullscreenToggle: true //全屏按钮
        }
      }
    };
  },
  components: {
    Banner
  },
  created() {
    this.$http
      .get(
        "DataDictionary/GetDataDictionaryAll?key=%E4%BA%A7%E5%93%81%E8%A7%86%E9%A2%91%E9%93%BE%E6%8E%A5"
      )
      .then(response => {
        this.videoSrc = response.data[0].Content;
        window.console.log(this.videoSrc);
        this.loading = false;
      })
      .catch(function(error) {
        window.console.log(error);
      });
  }
};
</script>

<style lang="scss" scoped>
.product {
  width: 100%;
  height: 100%;
  background-color: #14679f;
}

.product-content {
  width: 1240px;
  margin: 0 auto;
  background-color: #fff;
}

.p-video {
  width: 1000px;
  margin: 0 auto;
  padding: 60px 0;
}

//传统管理模式不足
.lacking {
  height: 420px;
  padding: 20px 0;
  //margin: 20px 0;

  .lacking-bottom {
    display: flex;
    justify-content: space-around;
    padding: 100px 100px;

    .lacking-bottom-item {
      width: 200px;
      display: flex;
      flex-direction: column;
      align-items: center;
      text-align: center;
      //justify-content: center;

      .lacking-bottom-item-img {
        width: 120px;
        height: 120px;
        background: #1667a0;
        border-radius: 50%;
        overflow: hidden;
        line-height: 160px;
      }
    }
    p {
      font-size: 16px;
      text-align: start;
      margin: 10px 0;
    }
  }
}

//平台目标
.target {
  margin-top: 50px;
  &-img {
    margin-top: 50px;
    text-align: center;
  }
}

//
.modular {
  margin-top: 50px;
  .modular-content {
    padding: 50px 50px;
    display: flex;
    justify-content: space-around;
  }
}
.modular-content-same {
  width: 182px;
  height: 405px;

  .same-item {
    height: 70px;
    padding: 10px 0;
    display: flex;
    justify-content: space-between;

    .same-item-img {
      width: 70px;
      height: 70px;
      line-height: 100px;
      background: #1667a0;
      border-radius: 50%;
      text-align: center;
    }
    p {
      color: #1667a0;
      font-weight: 700;
      line-height: 70px;
    }
  }
}

.modular-content-center {
  width: 355px;
  height: 355px;
  img {
    width: 100%;
  }
}
//公共样式
.title,
.eTitle {
  font-size: 34px;
  font-weight: 400;
  color: #333;
  text-align: center;
}
.eTitle {
  font-size: 30px;
  padding: 10px 0;
}
</style>