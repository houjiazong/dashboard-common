<template>
  <div class="exception">
    <div class="img-block">
      <div class="img-ele" :style="{backgroundImage: `url(${config[type].img})`}" />
    </div>
    <div class="content">
      <h1>{{ config[type].title }}</h1>
      <div class="desc">{{ config[type].desc }}</div>
      <div class="actions">
        <a-button type="primary" @click="handleToHome">返回首页</a-button>
      </div>
    </div>
  </div>
</template>

<script>
import types from './type'

export default {
  name: 'Exception',
  props: {
    type: {
      type: String,
      default: '404',
    },
  },
  data () {
    return {
      config: types,
    }
  },
  methods: {
    handleToHome () {
      this.$router.push('/')
    },
  },
}
</script>
<style lang="scss" scoped>
.exception {
  display: flex;
  align-items: center;
  height: 80%;
  min-height: 500px;
  .img-block {
    flex: 0 0 62.5%;
    width: 62.5%;
    padding-right: 152px;
    zoom: 1;
    &::before,
    &::after {
      content: ' ';
      display: table;
    }
    &::after {
      clear: both;
      height: 0;
      font-size: 0;
      visibility: hidden;
    }
  }
  .img-ele {
    float: right;
    width: 100%;
    max-width: 430px;
    height: 360px;
    background-repeat: no-repeat;
    background-position: 50% 50%;
    background-size: contain;
  }
  .content {
    flex: auto;
    h1 {
      margin-bottom: 24px;
      color: #434e59;
      font-weight: 600;
      font-size: 72px;
      line-height: 72px;
    }
    .desc {
      margin-bottom: 16px;
      color: rgba(0, 0, 0, .45);
      font-size: 20px;
      line-height: 28px;
    }
    .actions {
      button:not(:last-child) {
        margin-right: 8px;
      }
    }
  }
}
@media screen and (max-width: 1200px) {
  .exception {
    .img-block {
      padding-right: 88px;
    }
  }
}
@media screen and (max-width: 768px) {
  .exception {
    display: block;
    text-align: center;
    .img-block {
      margin: 0 auto 24px;
      padding-right: 0;
    }
  }
}
@media screen and (max-width: 480px) {
  .exception {
    .img-block {
      margin-bottom: -24px;
      overflow: hidden;
    }
  }
}
</style>
