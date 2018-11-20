<template>
    <div class="home-container">
        <!-- 轮播图区域 -->
        <mt-swipe class="banner-container" :auto="4000">
            <mt-swipe-item v-for="(item, index) in lunbotuList" :key="index">
                <a :href="item.url">
                    <img :src="item.img" alt="">
                </a>
            </mt-swipe-item> 
        </mt-swipe>

        <!-- 九宫格到6宫格的改造 -->
        <ul class="mui-table-view mui-grid-view mui-grid-9">
            <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3"><a href="#">
                    <img src="../../images/menu1.png" alt="">
                    <div class="mui-media-body">新闻资讯</div></a></li>
            <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3"><a href="#">
                    <img src="../../images/menu2.png" alt="">
                    <div class="mui-media-body">图片分享</div></a></li>
            <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3"><a href="#">
                    <img src="../../images/menu3.png" alt="">
                    <div class="mui-media-body">商品购买</div></a></li>
            <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3"><a href="#">
                    <img src="../../images/menu4.png" alt="">
                    <div class="mui-media-body">留言反馈</div></a></li>
            <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3"><a href="#">
                    <img src="../../images/menu5.png" alt="">
                    <div class="mui-media-body">视频专区</div></a></li>
            <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3"><a href="#">
                    <img src="../../images/menu6.png" alt=""> 
                    <div class="mui-media-body">联系我们</div></a></li>
		</ul>

    </div>
</template>

<script>
    import { Toast } from 'mint-ui';

    export default {
        data() {
            return {
                lunbotuList: []     /* 保存轮播图的数组 */
            };
        },
        created() {
            this.getLunbotu();
        },
        methods: {
            getLunbotu() {
                this.$http.get("http://www.lovegf.cn:8899/api/getlunbo").then(result => {
                    // console.log(result.body);
                    if (result.body.status === 0) {
                        this.lunbotuList = result.body.message;
                        // Toast("加载轮播图成功!");
                    }else {
                        Toast("获取轮播图数据失败!请重试!");
                    }
                });
            }
        }
    };
</script>

<style lang="less">
   .home-container {
       .banner-container {
           height: 200px;
           .mint-swipe-item {
               &:nth-child(1) {
                   background-color: red;
               }
               &:nth-child(2) {
                   background-color: cyan;
               }
               &:nth-child(3) {
                   background-color: orange;
               }
               a {
                    display: block;
                    width: 100%;
                    height: 100%;
                }
               img {
                   width: 100%;
                   height: 100%;
               }
           }
       }
        .mui-grid-view {
            background-color: #fff;
            border: none;
            .mui-table-view-cell {
            border: none;
            img {
                width: 60px;
                height: 60px;
            }
            .mui-media-body {
                font-size: 13px;
            }
           }
        }
   }
</style>


