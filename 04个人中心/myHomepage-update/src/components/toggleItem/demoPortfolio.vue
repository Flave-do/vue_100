<template>
    <!-- Portfolio -->
    <div id="portfolio" class="content-list" ref="portfoliobox">
        <!-- Portfolio Filter -->
        <div id="portfolio-filter-container">
            <ul id="portfolio-filter">
                <li v-for="(datas,dataid) in dataFilterList" :key="dataid">
                    <a href="#" 
                        :data-filter="datas.datasFilter" 
                        @click.prevent="changeFilter(datas.dataFilter)"
                        :class="{current:datas.dataFilter == dataFilter}" 
                    >
                    {{datas.title}}</a>
                </li>
            </ul>
        </div>
        <!-- End Portfolio Filter -->

        <!-- Portfolio Lists -->
        <ul id="portfolio-list" class="isotope" :style="portfolioListStyle">
            <transition-group name="list" tag="p" appear>
                <li class="isotope-item " 
                    v-for="(imgs,imgId) in dataFilterRom(imgDemo)" 
                    :key="imgs.id"
                    :style="liItemStyle(imgId)"
                    :class="imgs.imgClass"
                >
                    <CoolLightBox
                        :items="imgs.items" 
                        :index="index[imgId].index"
                        :fullScreen="true"
                        @close="index[imgId].index = null">
                    </CoolLightBox>
                    <div class="img_wrapper" :style="imgWrapperStyle">
                        <div class="image"
                            v-for="(image,imageIndex) in imgs.items"
                            :key="image.id"
                            @click="index[imgId].index = imageIndex"
                            >
                            <img :src="require('../../assets/images/portfolio/'+imgs.imgSrc)" alt="" :style="imgSrcStyle"/>
                        </div>
                    </div>
                </li>
            </transition-group>
        </ul>
        <!-- End Portfolio Lists -->

    </div>
    <!-- End Portfolio -->

</template>

<script>
import CoolLightBox from 'vue-cool-lightbox'
import 'vue-cool-lightbox/dist/vue-cool-lightbox.min.css'
import 'animate.css'
export default {
    name:'demoPortfolio',
    components: {CoolLightBox,},
    data() {
        return {
            dataFilter:'*',
            index:[
                {index:'null',},
                {index:'null',},
                {index:'null',},
                {index:'null',},
                {index:'null',},
                {index:'null',},
                {index:'null',},
                {index:'null',},
                {index:'null',},
                {index:'null',},
            ],
            dataFilterList:[
                {id:'0','dataFilter':'*',title:'??????'},
                {id:'1','dataFilter':'VueHxWebdesign',title:'Vue'},
                {id:'2','dataFilter':'GitProgram',title:'MyGithub'},
                {id:'3','dataFilter':'SpiderVideo',title:'Spider'},
                {id:'4','dataFilter':'DjangoHxWebdesign',title:'Django'},
                // {id:'5','dataFilter':'knowledgeHierarchy',title:'????????????'},
            ],
            imgDemo:[
                {id:'0',imgClass:'VueHxWebdesign',title:'VueHxWebdesign',imgSrc:'Vue/HomePageHx.png',
                    items:[
                        {
                            src:require('../../assets/images/portfolio/Vue/HomePageHx.png'),
                            thumb:require('../../assets/images/portfolio/Vue/HomePageHx.png'),
                            title: '??????vue?????????????????????????????????',
                            description: "Photo by Yang",
                        },
                        {
                            src:require('../../assets/images/portfolio/Vue/HomePageHxCode.png'),
                            thumb:require('../../assets/images/portfolio/Vue/HomePageHxCode.png'),
                            title: '????????????????????????????????????',
                            description: "Photo by Yang",
                        },
                    ]
                },
                {id:'1',imgClass:'GitProgram',title:'GitProgram',imgSrc:'Github/MyGithub.png',
                    items:[
                        {
                            src:require('../../assets/images/portfolio/Github/MyGithub.png'),
                            thumb:require('../../assets/images/portfolio/Github/MyGithub.png'),
                            title: '??????git????????????',
                            description: "Photo by Yang",
                        },
                        {
                            src:require('../../assets/images/portfolio/Github/githubDjangoHx.png'),
                            thumb:require('../../assets/images/portfolio/Github/githubDjangoHx.png'),
                            title: 'Django-Hx????????????????????????',
                            description: "Photo by Yang",
                        },
                        {
                            src:require('../../assets/images/portfolio/Github/githubDjangoMeiduo.png'),
                            thumb:require('../../assets/images/portfolio/Github/githubDjangoMeiduo.png'),
                            title: 'Django-meiduo??????????????????',
                            description: "Photo by Yang",
                        },
                        {
                            src:require('../../assets/images/portfolio/Github/githubDjangoStart.png'),
                            thumb:require('../../assets/images/portfolio/Github/githubDjangoStart.png'),
                            title: 'Django-????????????',
                            description: "Photo by Yang",
                        },
                    ]
                },
                {id:'2',imgClass:'SpiderVideo',title:'SpiderVideo',imgSrc:'Spider/VideoCrawler8.png',
                    items:[
                        {
                            src:require('../../assets/images/portfolio/Spider/VideoCrawler1.png'),
                            thumb:require('../../assets/images/portfolio/Spider/VideoCrawler1.png'),
                            title: '?????????,???????????????????????????',
                            description: "Photo by Yang",
                        },
                        {
                            src:require('../../assets/images/portfolio/Spider/VideoCrawler2.png'),
                            thumb:require('../../assets/images/portfolio/Spider/VideoCrawler2.png'),
                            title: '?????????????????????',
                            description: "Photo by Yang",
                        },
                        {
                            src:require('../../assets/images/portfolio/Spider/VideoCrawler3.png'),
                            thumb:require('../../assets/images/portfolio/Spider/VideoCrawler3.png'),
                            title: '????????????????????????????????????',
                            description: "Photo by Yang",
                        },
                        {
                            src:require('../../assets/images/portfolio/Spider/VideoCrawler4.png'),
                            thumb:require('../../assets/images/portfolio/Spider/VideoCrawler4.png'),
                            title: '????????????????????????????????????????????????????????????????????????',
                            description: "Photo by Yang",
                        },
                        {
                            src:require('../../assets/images/portfolio/Spider/VideoCrawler5.png'),
                            thumb:require('../../assets/images/portfolio/Spider/VideoCrawler5.png'),
                            title: '?????????????????????,?????????',
                            description: "Photo by Yang",
                        },
                        {
                            src:require('../../assets/images/portfolio/Spider/VideoCrawler6.png'),
                            thumb:require('../../assets/images/portfolio/Spider/VideoCrawler6.png'),
                            title: '????????????????????????',
                            description: "Photo by Yang",
                        },
                        {
                            src:require('../../assets/images/portfolio/Spider/VideoCrawler7.png'),
                            thumb:require('../../assets/images/portfolio/Spider/VideoCrawler7.png'),
                            title: '????????????????????????,?????????',
                            description: "Photo by Yang",
                        },
                        {
                            src:require('../../assets/images/portfolio/Spider/VideoCrawler8.png'),
                            thumb:require('../../assets/images/portfolio/Spider/VideoCrawler8.png'),
                            title: '??????????????????,???????????????~',
                            description: "Photo by Yang",
                        },
                        {
                            src:require('../../assets/images/portfolio/Spider/VideoCrawlerCode.png'),
                            thumb:require('../../assets/images/portfolio/Spider/VideoCrawlerCode.png'),
                            title: '???????????????1',
                            description: "Photo by Yang",
                        },
                        {
                            src:require('../../assets/images/portfolio/Spider/VideoCrawlerCode2.png'),
                            thumb:require('../../assets/images/portfolio/Spider/VideoCrawlerCode2.png'),
                            title: '???????????????2',
                            description: "Photo by Yang",
                        },
                    ]
                },
                {id:'3',imgClass:'DjangoHxWebdesign',title:'DjangoHxWebdesign',imgSrc:'Django/ubtunHxPage.png',
                    items:[
                        {
                            src:require('../../assets/images/portfolio/Django/ubtunHxPage.png'),
                            thumb:require('../../assets/images/portfolio/Django/ubtunHxPage.png'),
                            title: '??????Django?????????????????????',
                            description: "Photo by Yang",
                        },
                        {
                            src:require('../../assets/images/portfolio/Django/ubtunHxMessage.png'),
                            thumb:require('../../assets/images/portfolio/Django/ubtunHxMessage.png'),
                            title: '????????????,????????????????????????????????????',
                            description: "Photo by Yang",
                        },
                        {
                            src:require('../../assets/images/portfolio/Django/ubtunHxInterflow.png'),
                            thumb:require('../../assets/images/portfolio/Django/ubtunHxInterflow.png'),
                            title: '?????????????????????,??????????????????????????????????????????',
                            description: "Photo by Yang",
                        },
                        {
                            src:require('../../assets/images/portfolio/Django/ubtunHxCode.png'),
                            thumb:require('../../assets/images/portfolio/Django/ubtunHxCode.png'),
                            title: '????????????',
                            description: "Photo by Yang",
                        },
                    ]
                },
                // {id:'4',imgClass:'knowledgeHierarchy',title:'knowledgeHierarchy',imgSrc:'knowledgeHierarchy/vue????????????.png',
                //     items:[
                //         {
                //             src:require('../../assets/images/portfolio/knowledgeHierarchy/vue????????????.png'),
                //             thumb:require('../../assets/images/portfolio/knowledgeHierarchy/vue????????????.png'),
                //             title: '????????????',
                //             description: "Photo by Yang",
                //         },
                        
                //     ]
                // },
            ],
            // portfolioListStyle:"position: relative; overflow: hidden; height: 480px;",
            imgWrapperStyle:'display: inline-block; width: 145px; height: 145px;',
            portfolioWidth:0,
            imgBoxWidth:155,
            // windowWidth: document.documentElement.clientWidth, // ??????????????????
            // windowHeight: document.documentElement.clientHeight // ??????????????????
        }
    },
    computed:{
        portfolioListStyle(){
            let heightY = Math.ceil(this.portfolioListNumber*this.imgBoxWidth/this.portfolioWidth)*240
            return "position: relative; overflow: hidden; height: "+heightY+"px;width:"+this.portfolioWidth+"px;"
        },
        portfolioListNumber(){
            let len = 0
            for(var i in this.imgDemo){
                if(this.dataFilter === '*'){
                    len ++
                }else if(this.imgDemo[i].imgClass === this.dataFilter){
                    len ++
                }
            }
            return len
        },
        liItemStyle(){
            return function(pic){
                let rowX = parseInt(this.portfolioWidth/this.imgBoxWidth)
                if(rowX>=this.portfolioListNumber){
                    rowX = this.portfolioListNumber
                }
                let marginX = (this.portfolioWidth-rowX*this.imgBoxWidth)/rowX/2
                let boxWidth = (this.imgBoxWidth + marginX*2)
                let lefX = 0
                let topY = 0
                topY = parseInt(pic/rowX)*230
                lefX = boxWidth*(pic%rowX)
                return 'position: absolute; left:'+lefX+'px; top: '+topY+'px;margin:0px '+marginX+'px;'
            } 
        },
        // imgWrapperStyle(){
        //    // ?????????????????????
        // }
        imgSrcStyle(){
            // img????????????
            //position: absolute;left: 5px;top: 5px;
           return ''
        },
        


    },
    methods:{
        changeFilter(filter){
            this.dataFilter = filter
        },
        GetPortfolioWidth(){
            const that = this
            this.$nextTick(() => {
                // var domWidth = this.$refs.container.clientWidth // ???
                // var domHeight = this.$refs.container.clientHeight // ???
                that.portfolioWidth = that.$refs.portfoliobox.offsetWidth
            })
        },
        dataFilterRom(data){
            let that = this
            return data.filter(obj => {
                if(that.dataFilter === '*'){
                    return obj
                }else{
                   return obj.imgClass === that.dataFilter 
                }
            })
        },

    },

    created(){
        window.addEventListener('resize', this.GetPortfolioWidth); //???????????????
        this.GetPortfolioWidth() //??????????????????????????????
    },
    destroyed(){
    window.removeEventListener('resize', this.GetPortfolioWidth)
    }

}

</script>

<style lang='css' scoped> 
.clearfix,
.content-list {
  zoom: 1;
}
h6{
    text-shadow: 0;
}
/* Portfolio */
#portfolio-filter-container {
    text-align: center;
    margin-bottom: 30px;
}
#portfolio-filter {
    text-align: center
}
#portfolio-filter li {
    display: inline-block;
    margin: 0 5px 10px 5px;
    line-height: 30px;
}
#portfolio-filter li a {
    display: block;
    padding: 0 10px;
    color: #FFFFFF;
    border-style: solid;
    border-width: 1px;
    cursor: pointer;
    display: inline-block;
    text-align: center;
    /* vertical-align: middle; */
    background-color: #414141;
    *background-color: #222222;
    background-image: -ms-linear-gradient(top, #555555, #222222);
    background-image: -webkit-gradient(linear, 0 0, 0 100%, from(#555555), to(#222222));
    background-image: -webkit-linear-gradient(top, #555555, #222222);
    background-image: -o-linear-gradient(top, #555555, #222222);
    background-image: -moz-linear-gradient(top, #555555, #222222);
    /* background-image: linear-gradient(top, #555555, #222222); */
    background-repeat: repeat-x;
    border-color: #222222 #222222 #000000;
    border-color: rgba(0, 0, 0, 0.1) rgba(0, 0, 0, 0.1) rgba(0, 0, 0, 0.25);
    filter: progid:dximagetransform.microsoft.gradient(startColorstr='#555555', endColorstr='#222222', GradientType=0);
    filter: progid:dximagetransform.microsoft.gradient(enabled=false);
    text-shadow: 0 -1px 0 rgba(0, 0, 0, 0.25);
    -webkit-border-radius: 4px;
       -box-border-radius: 4px;
            border-radius: 4px;
    -webkit-box-shadow: 0 1px 0 rgba(255, 255, 255, 0.2) inset, 0 1px 0px rgba(255, 255, 255, 0.9);
       -moz-box-shadow: 0 1px 0 rgba(255, 255, 255, 0.2) inset, 0 1px 0px rgba(255, 255, 255, 0.9);
            box-shadow: 0 1px 0 rgba(255, 255, 255, 0.2) inset, 0 1px 0px rgba(255, 255, 255, 0.9);
}
#portfolio-filter li a:hover {
    color: #ffffff;
    text-shadow: 0 -1px 0 rgba(0, 0, 0, 0.25);
    background-color: #222222;
    *background-color: #151515;

    background-position: 0 -15px;
    -webkit-transition: background-position 0.1s linear;
       -moz-transition: background-position 0.1s linear;
        -ms-transition: background-position 0.1s linear;
         -o-transition: background-position 0.1s linear;
            transition: background-position 0.1s linear;
}
#portfolio-filter li a.current {
    background-image: none;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.15) inset, 0 1px 2px rgba(0, 0, 0, 0.05);
    outline: 0 none;
    background-color: #111111;
    color: rgba(255, 255, 255, 0.75);
}
#portfolio-list {
    display: inline-block;
    text-align: center;
    /* ??????box?????? */
    width: 780px;
}
#portfolio-list li {
    width: 155px;
    height: 200px;
    /* margin: 0 20px 40px; */
    background: #fff;
    float: left;
    -webkit-box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.1);
       -box-box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.1);
            box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.1);
}
#portfolio-list li a {
    margin: 5px;
    display: block;
}

/* Isotope CSS3 transitions */

.isotope,
.isotope .isotope-item {
  -webkit-transition-duration: 0.8s;
     -moz-transition-duration: 0.8s;
      -ms-transition-duration: 0.8s;
       -o-transition-duration: 0.8s;
          transition-duration: 0.8s;
}

.isotope {
  -webkit-transition-property: height, width;
     -moz-transition-property: height, width;
      -ms-transition-property: height, width;
       -o-transition-property: height, width;
          transition-property: height, width;
}

.isotope .isotope-item {
  -webkit-transition-property: -webkit-transform, opacity;
     -moz-transition-property:    -moz-transform, opacity;
      -ms-transition-property:     -ms-transform, opacity;
       -o-transition-property:         top, left, opacity;
          transition-property:         transform, opacity;
}

/* disabling Isotope CSS3 transitions */
.isotope.no-transition,
.isotope.no-transition .isotope-item,
.isotope .isotope-item.no-transition {
  -webkit-transition-duration: 0s;
     -moz-transition-duration: 0s;
      -ms-transition-duration: 0s;
       -o-transition-duration: 0s;
          transition-duration: 0s;
}
.img_wrapper{
    overflow: hidden
}
.list-enter-active{
    animation: zoomIn; /* referring directly to the animation's @keyframe declaration */
    animation-duration: 2s; /* don't forget to set a duration! */
}
.list-leave-active{
    animation: zoomOut; /* referring directly to the animation's @keyframe declaration */
    animation-duration: 2s; /* don't forget to set a duration! */
}
#portfolio-list img{
    /* width: 145px; */
    height: 145px;
}
</style>
