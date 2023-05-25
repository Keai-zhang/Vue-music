<template>
    <div>
        <div id="swipercom">
            <div class="swiper-container" id="swiperIndex">
                <div class="swiper-wrapper">
                    <div class="swiper-slide" v-for="(item, index) in imgs" :key="index"><img :src="item.pic" alt=""></div>
                </div>
                <!-- 分页器 -->
                <div class="swiper-pagination"></div>
            </div>
        </div>
    </div>
</template>

<script>
import "swiper/css/swiper.css"
import Swiper from 'swiper'
import {getBanner} from "@/api/index.js"

export default {
    name: "swipercom",
    data() {
        return {
            imgs: [//轮播图数据
                { pic: require("../assets/logo.png") },
                { pic: require("../assets/logo.png") },
                { pic: require("../assets/logo.png") },
                { pic: require("../assets/logo.png") },
                { pic: require("../assets/logo.png") },
                { pic: require("../assets/logo.png") },
                { pic: require("../assets/logo.png") }
            ]
        }
    },
    async mounted() {
        var res = await getBanner(1);
        this.imgs = res.data.banners;
        var myswiper = new Swiper("#swiperIndex", {
            // loop:true, //循环模式
            // autoplay:true, //自动轮播
            //分页器
            pagination: {
                el: ".swiper-pagination",
                clickable: true //分页小圆点可以点击
            }
        })
    }
}
</script>
<style lang="less">
#swipercom {
    width: 7.5rem;

    #swiperIndex.swiper-container {
        width: 7.1rem;
        height: 2.6rem;
        border-radius: 0.1rem;

        .swiper-slide img {
            width: 100%;
        }

        .swiper-pagination-bullet-active {
            background-color: orangered;
        }

    }
}
</style>
