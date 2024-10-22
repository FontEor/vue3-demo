<template>
  <div>
    <canvas id="QRCode_header" style="width: 280px; height: 280px"></canvas>
  </div>
</template>

<script>
import QRCode from "qrcode"; //引入生成二维码插件
export default {
  props: [""],
  data() {
    return {
      qrUrl: location.href,
    };
  },
  watch: {},
  mounted() {
    this.getQRCode();
  },
  created() {},
  methods: {
    getQRCode() {
      //生成的二维码为URL地址js
      //http://e.hiphotos.baidu.com/image/pic/item/a1ec08fa513d2697e542494057fbb2fb4316d81e.jpg
      this.qrUrl =
        "http://qp119.bmwae.cn/sqrcode/image?short=GUsQrq&domain=f.afbkw.cn&sign=&vhcode=gvbem1729591493uci769f827d2bb8ef130819e293c81148f134"; //"https://www.baidu.com/";
      let opts = {
        errorCorrectionLevel: "H", //容错级别
        type: "image/png", //生成的二维码类型
        quality: 0.3, //二维码质量
        margin: 0, //二维码留白边距
        width: 280, //宽
        height: 280, //高
        text: "http://qp119.bmwae.cn/sqrcode/image?short=GUsQrq&domain=f.afbkw.cn&sign=&vhcode=gvbem1729591493uci769f827d2bb8ef130819e293c81148f134", //二维码内容https://www.baidu.com/ 
        color: {
          dark: "#333333", //前景色
          light: "#fff", //背景色
        },
      };

      let msg = document.getElementById("QRCode_header");
      // 将获取到的数据（val）画到msg（canvas）上
      QRCode.toCanvas(msg, this.qrUrl, opts, function (error) {
        if (error) {
          console.log("二维码加载失败", error);
          this.$message.error("二维码加载失败");
        }
      });
    },
  },
};
</script>

<style></style>
