<template>
    <!-- Slider -->
    <div id="menu-slider">
        <div id="menu-slider-container">
            <div class="slider-bg bg-black"></div> <!-- Slider Background -->
            <div id="menu-slider-bar" class="slider-bar color-bar animate-bar" :style="barStyle"></div> <!-- Slider Bar -->
                <div id="menu-slider-pointer" class="slider-pointer color-pointer" :style="pointStyle"></div> <!-- Slider Pointer -->
        </div>
    </div>
    <!-- End Slider -->
</template>

<script>
export default {
    name:'barType',
    data() {
        return {
            barLength:0,
        }
    },
    methods:{
      //左右、长度
      pipeMover(LorR,site){
        if(LorR){
          this.barLength = this.barLength + site
        }else{
          this.barLength = this.barLength - site
        }
      },
    },
    computed:{
        barStyle(){
            return{
                width:this.barLength+'%'
            }
        },
        pointStyle(){
          return{
                left:this.barLength+'%'
            }
        },
    },
    mounted(){
      this.$bus.$on('pipeMover',this.pipeMover)
    }
}

</script>

<style lang='css' scoped> 
/* Bar */
.slider-bg {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 8px;
    z-index: 10;
    -webkit-border-radius: 4px;
        -box-border-radius: 4px;
            border-radius: 4px;
}
.bg-black {
    background: #272829;
    -webkit-box-shadow: inset 0px 1px 0px 0px rgba(0, 0, 0, 0.5), 0px 1px 0px 0px rgba(255, 255, 255, 0.1);
        -box-box-shadow: inset 0px 1px 0px 0px rgba(0, 0, 0, 0.5), 0px 1px 0px 0px rgba(255, 255, 255, 0.1);
            box-shadow: inset 0px 1px 0px 0px rgba(0, 0, 0, 0.5), 0px 1px 0px 0px rgba(255, 255, 255, 0.1);
}
.bg-grey {
    background: #cecece;
    -webkit-box-shadow: inset 0px 1px 0px 0px rgba(0, 0, 0, 0.1), 0px 1px 0px 0px rgba(255, 255, 255, 0.9);
        -box-box-shadow: inset 0px 1px 0px 0px rgba(0, 0, 0, 0.1), 0px 1px 0px 0px rgba(255, 255, 255, 0.9);
            box-shadow: inset 0px 1px 0px 0px rgba(0, 0, 0, 0.1), 0px 1px 0px 0px rgba(255, 255, 255, 0.9);
}
.slider-bar {
    position: absolute;
    top: 0;
    left: 0;
    background-repeat: repeat-x;
    background-position: left top;
    width: 0%;
    height: 8px;
    z-index: 11;
    transition-property: width;
    transition-duration: 0.5s;
    -webkit-border-radius: 4px;
        -box-border-radius: 4px;
            border-radius: 4px;
    -webkit-box-shadow: inset 0px 1px 0px 0px rgba(255, 255, 255, 0.75), 0px 1px 0px 0px rgba(0, 0, 0, 0.1);
        -box-box-shadow: inset 0px 1px 0px 0px rgba(255, 255, 255, 0.75), 0px 1px 0px 0px rgba(0, 0, 0, 0.1);
            box-shadow: inset 0px 1px 0px 0px rgba(255, 255, 255, 0.75), 0px 1px 0px 0px rgba(0, 0, 0, 0.1);
}
.slider-pointer {
    position: absolute;
    top: -6px;
    left: 0%;
    margin-left: -10px;
    width: 20px;
    height: 21px;
    z-index: 12;
    transition-property: left;
    transition-duration: 0.5s;
}

#menu-slider-container {
    height: 8px;
    margin: 0 auto;
    position: relative;
}

.color-bar{
    background-image: url('~@/assets/images/bar-blue.png');
}
.color-pointer{
    background-image: url('~@/assets/images/pointer-blue.png');
}

/* Bar animation */
.animate-bar {
	animation: progress 0.5s linear infinite;
	-moz-animation: progress 0.5s linear infinite;
	-webkit-animation: progress 0.5s linear infinite;
	-ms-animation: progress 0.5s linear infinite;
	-o-animation: progress 0.5s linear infinite;
}

@-webkit-keyframes progress {
  from {
    background-position: 0 0;
  }
  to {
    background-position: -20px 0;
  }
}
@-moz-keyframes progress {
  from {
    background-position: 0 0;
  }
  to {
    background-position: -20px 0;
  }
}
@-ms-keyframes progress {
  from {
    background-position: 0 0;
  }
  to {
    background-position: -20px 0;
  }
}
@-o-keyframes progress {
  from {
    background-position: 0 0;
  }
  to {
    background-position: -20px 0;
  }
}
@keyframes progress {
  from {
    background-position: 0 0;
  }
  to {
    background-position: -20px 0;
  }
}

</style>
