<template>
  <div class="like" @click="clickLike">
    <div class="like-item" v-for="item in imgList" :key="item">
      <img :src="item">
    </div>
  </div>
</template>
<script>
import {mTween, css} from './../../static/mTween'
export default {
  name: 'likeAni',
  data() {
    return {
      imgList: []
    }
  },
  created () {
    // 生成图片
    let imgArr = []
    for(let i = 1;i <= 16; i++ ) {
      imgArr.push(require('./../../static/images/' + i + '.png'))
    }
    this.imgList = imgArr.sort(() => {
      return 0.5 - Math.random()
    })
    
    
    // dom.style.transform = 'rotate(-180deg) translate(180px, 180px)'
    // console.log(this.imgList)
  },
  mounted () {
    
  },
  methods: {
    clickLike () {
      let dom = document.querySelectorAll('.like-item')
      console.log(dom)
      dom.forEach(item => {
        let random = Math.floor(Math.random()*(40 - 150) + 150)
        let length = Math.floor(Math.random()*(4 - 10) + 10)
        
        item.style.transform = `rotate(${random}deg) translate(-.98rem, 0)`
        item.style.opacity = 1
        setTimeout(() => {
          item.style.transition = '.8s';
          item.style.transform = `rotate(${random}deg) translate(-${length}rem, 0)`
          item.style.opacity = 0
          setTimeout(() => {
            item.style.transition = '0s';
            item.style.transform = `rotate(${random}deg) translate(-.98rem, 0)`
            item.style.opacity = 0
          }, 800)
        })
        // item.style.opacity = 0
        // setTimeout(() => {
        //   item.style.transform = `rotate(-.98deg) translate(-${length}rem, 0)`
        //   item.style.opacity = 0
        // }, 500)
        // css(item, 'rotate', random)
        // mTween({
        //   el: item,
        //   attr: {
        //     'rotate': random
        //   }
        // })
        console.log(mTween)
      })
    } 
  }
}
</script>
<style lang="less" scoped>
.like {
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  // position: absolute;
  display: flex;
  justify-content: center;
  align-items: center;
  // transform-origin: 20% 50%;
  .like-item {
    width: .48rem;
    height: .48rem;
    position: absolute;
    // opacity: 0;
    transform: rotate(50deg) translate(-.98rem, 0);
    img {
      width: 100%;
      height: 100%;
      transform: rotate(-50deg)
    }
    
  }
}
</style>
