<template>
    <div class="sidebarExtend">
        <div class="block">
            <div class="home" v-bind:class="[{active : selected === 0}]" @click="change(0)">
                <i class="ti-home"></i>
                <span>Home</span>
            </div>
            <div class="short" v-bind:class="[{active : selected === 1}]" @click="change(1)">
                <i class="ti-video-clapper"></i>
                <span>Shorts</span>
            </div>
            <div class="sub" v-bind:class="[{active : selected === 2}]" @click="change(2)">
                <i class="ti-user"></i>
                <span>Subscriptions</span>
            </div>
            </div>
        <hr>
        <div class="block">
            <div class="library" v-bind:class="[{active : selected === 3}]" @click="change(3)">
                <i class="ti-gallery"></i>
                <span>Library</span>
            </div>
            <div class="history" v-bind:class="[{active : selected === 4}]" @click="change(4)">
                <i class="ti-pie-chart"></i>
                <span>History</span>
            </div>
            <div class="your-video" v-bind:class="[{active : selected === 5}]" @click="change(5)">
                <i class="ti-control-play"></i>
                <span>Your videos</span>
            </div>
            <div class="watch-later" v-bind:class="[{active : selected === 6}]" @click="change(6)">
                <i class="ti-time"></i>
                <span>Watch later</span>
            </div>
            <div class="liked-videos" v-bind:class="[{active : selected === 7}]" @click="change(7)">
                <i class="ti-thumb-up"></i>
                <span>Liked videos</span>
            </div>
        </div>
        <hr>
        <div class="block">
            <p class="title">Subscriptions</p>
            <div v-bind:class="[{active : selected === 8}]" @click="change(8)">
                <img src="/assets/img/avatar/binhgold.jfif" alt="">
                <span>Bình Gold</span>
            </div>
            <div v-bind:class="[{active : selected === 9}]" @click="change(9)">
                <img src="/assets/img/avatar/ansez.png" alt="">
                <span>Ansez</span>
            </div>
            <div v-bind:class="[{active : selected === 10}]" @click="change(10)">
                <img src="/assets/img/avatar/andree.jpg" alt="">
                <span>Andree Right Hand</span>
            </div>
        </div>
        <hr>
        <div class="block">
            <p class="title">Explore</p>
            <div class="trending" v-bind:class="[{active : selected === 11}]" @click="change(11)">
                <i class="ti-bar-chart"></i>
                <span>Trending</span>
            </div>
            <div class="music" v-bind:class="[{active : selected === 12}]" @click="change(12)">
                <i class="ti-music"></i>
                <span>Music</span>
            </div>
            <div class="gaming" v-bind:class="[{active : selected === 13}]" @click="change(13)">
                <i class="ti-game"></i>
                <span>Gaming</span>
            </div>
            <div class="news" v-bind:class="[{active : selected === 14}]" @click="change(14)">
                <i class="ti-star"></i>
                <span>News</span>
            </div>
            <div class="sports" v-bind:class="[{active : selected === 15}]" @click="change(15)">
                <i class="ti-cup"></i>
                <span>Sports</span>
            </div>
        </div>
        <hr>
        <div class="block">
            <div class="settings" v-bind:class="[{active : selected === 16}]" @click="change(16)">
                <i class="ti-settings"></i>
                <span>Settings</span>
            </div>
            <div class="report" v-bind:class="[{active : selected === 17}]" @click="change(17)">
                <i class="ti-flag"></i>
                <span>Report history</span>
            </div>
            <div class="help" v-bind:class="[{active : selected === 18}]" @click="change(18)">
                <i class="ti-help-alt"></i>
                <span>Help</span>
            </div>
            <div class="feedback" v-bind:class="[{active : selected === 19}]" @click="change(19)">
                <i class="ti-comment-alt"></i>
                <span>Send feedback</span>
            </div>
        </div>
        <div class="lastBlock"></div>
    </div>
</template>
    
<script>
    export default{
        name : 'Sidebar_Left',
        data() {
            return {
                selected : -1
            }
        },
        methods : {
            change : function(number){
                this.selected = number
            }
        }
            
    }
</script>
    
<style scoped>

div{
    color : white;
}

.lastBlock{
    height: 200px;
}

.block{
    margin : 16px 0 ;
    text-align: left;
}

.block div{
    position: relative;
    padding : 8px 0; 
    width: 100%;
    margin-top : 10px;
}

.block div:hover{
    background-color: rgba(255, 255, 255, 0.1);
    border-radius: 10px;
    cursor: pointer;
}

.block span{
    margin-top : 8px;
    font-size: 16px;
    margin-left : 35%;
}

.block p.title{
    margin-left : 10%;
    font-size: 18px;
}

.block div i{
    position: absolute;
    left : 10%;
    font-size: 20px;
}
.block div img{
    --size : 28px;
    position: absolute;
    border-radius: 50%;
    top : 50%;
    transform: translateY(-50%);
    left : 10%;
    width: var(--size);
    height: var(--size);
}

i, p{
    color : inherit;
}

.sidebarExtend{
    padding : 0 5px;
}

hr{
    height: 1px;
    margin : 8px 0;
    background-color: #ccc;
    opacity: 0.3;
    border: none;
}

.sidebarExtend::after{
    content: '';
    display: block;
    clear: both;
}

.active{
    color : red !important;
    background-color: rgba(255, 255, 255, 0.1);
    border-radius: 10px;
}




</style>