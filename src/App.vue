<template>
  <div id="app">
    <h1>hello world</h1>
    <button @click="downloadCapture2Png()">保存为图片</button>
  </div>
</template>

<script>
import html2canvas from 'html2canvas';

export default {
  name: 'App',
  components: {
  },
  methods: {
    //下载截图
    downloadCapture2Png() {
      html2canvas(document.body).then(function(canvas) {
        let uri = canvas.toDataURL()
        let filename = 'canvas.png'
        var link = document.createElement('a');
        if (typeof link.download === 'string') {
          link.href = uri;
          link.download = filename;
          //Firefox requires the link to be in the body
          document.body.appendChild(link);
          //simulate click
          link.click();
          //remove the link when done
          document.body.removeChild(link);
        } else {
          window.open(uri);
        }
      });
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
