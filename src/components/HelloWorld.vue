<template>
  <div class="hello">
    <div class="zan">
      点赞
      <like-animation></like-animation>
    </div>
    
  </div>
</template>

<script>
import LikeAnimation from './LikeAnimation'
export default {
  name: 'HelloWorld',
  data () {
    return {
      
    }
  },
  components: {
    LikeAnimation
  }
}
</script>
<style lang="less" scoped>
.zan {
  width: 1rem;
  height: 1rem;
  background-color: red;
  color: #fff;
  border-radius: 50%;
  // overflow: hidden;
  text-align: center;
  line-height: 1rem;
  position: fixed;
  bottom: 0;
  left: 50%;
  margin-left: -.5rem;
  // position: relative;
}
</style>
