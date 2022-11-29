<template>
  <div id="app">
    <Header id="header" :search.sync="filter" :is-extend.sync = "isExtend"></Header>
    <SideBar id="sidebar" v-if="isExtend == false"></SideBar>
    <SideBarExtend id="sidebarextend" v-if="isExtend == true"></SideBarExtend>
    <ContentVideo id="content" :class="[{contentZoomOut : isExtend == true}]" :data="data" :key="keyChild"></ContentVideo>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import SideBar from './components/Sidebar-Left.vue'
import SideBarExtend from './components/Sidebar-LeftExtend.vue'
import ContentVideo from './components/Content-Main.vue'


export default {
  name: 'App',
  components: {
    Header,
    SideBar,
    ContentVideo,
    SideBarExtend
  },
  watch:{
    filter : function(){
      var self = this
      var search = this.filter
      self.data = []
      for(var item of self.dataVideo)
      {
        if(item !== undefined && item.name.toLowerCase().startsWith(search.toLowerCase(),0)==true)
          self.data.push(item)
      }
      self.keyChild = Math.ceil(Math.random() * 1000)%123 + ''
    }
  },
  created: function() {
    this.filter = ''
  }
  ,
  data(){
    return {
      isExtend : false,
      keyChild : '',
      data : [],
      filter : 'vipvay',
      dataVideo : [
                    {
                        name :"Bật chế độ bay lên - Bình Gold",
                        image  : "bcdbl.jpg",
                        avatar  : "avatar.jpg",
                        view :"985K" ,
                        time :"2 months",
                        author : "Đan Trường",
                        check : true,
                        link : "https://youtu.be/r842vn9Os0Y",
                        gif : 'bcdbl.gif'
                    },
                    {
                        name :"Ông bà già tao lo hết",
                        image  : "obgtlh.jpg",
                        avatar  : "mylove.jpg",
                        view :"1.4M" ,
                        time :"8 months",
                        author : "Thu Trang",
                        check : true,
                        link : "https://youtu.be/siEhdhxiqHg",
                        gif  : "obgtlh.gif"
                    },
                    {
                        name :"Tiếng pháo tiễn người",
                        image  : "tptn.jpg",
                        avatar  : "hungquan.jpg",
                        view :"186K" ,
                        time :"13 days",
                        author : "Hùng Quân",
                        check : true,
                        link : "https://youtu.be/KI6TFG0-mTY",
                        gif : "tptn.gif"
                    },
                    {
                        name :"Love potion number 9",
                        image  : "lpn9.jpg",
                        avatar  : "dolce.jpg",
                        view :"1.1M" ,
                        time :"11 months",
                        author : "Dolce Music",
                        check : false,
                        link : "https://youtu.be/-RqwGKFJbsE",
                        gif : "lpn9.gif"
                    },
                    {
                        name :"Bốc bát họ | Bình Gold",
                        image  : "bbh.jpg",
                        avatar  : "binhgold.jfif",
                        view :"874K" ,
                        time :"3 months",
                        author : "Bình Gold",
                        check : true,
                        link : "https://youtu.be/gQ9U94eH7xQ",
                        gif : 'bbh.gif'
                    },
                    {
                        name :"Hết nhạc con về",
                        image  : "hncv.jpg",
                        avatar  : "1967.jpg",
                        view :"200K" ,
                        time :"2 months",
                        author : "1967 Music",
                        check : false,
                        link : "https://youtu.be/CKgEdz3paa0",
                        gif : "hncv.gif"
                    },
                    {
                        name :"Chạnh lòng thương cô",
                        image  : "cltc.jpg",
                        avatar  : "hhd.jpg",
                        view :"357K" ,
                        time :"10 months",
                        author : "HOA HỒNG DẠI MUSIC",
                        check : false,
                        link : "https://youtu.be/xIyIP-fR7Xg",
                        gif : "cltc.gif"
                    },
                    {
                        name :"Sang Xịn Mịn REMIX - Gill ft. Kewtiie x CUKAK",
                        image  : "sxm.jpg",
                        avatar  : "djay.jpg",
                        view :"198K" ,
                        time :"6 months",
                        author : "Djay Boy",
                        check : false,
                        link : "https://youtu.be/g4HygG78cT0",
                        gif : "sxm.gif"
                    },
                    {
                        name :"Goodie - Tbynz",
                        image  : "goodies.jpg",
                        avatar  : "dinz.jpg",
                        view :"786K" ,
                        time :"1 year",
                        author : "Dinz Music",
                        check : false,
                        link : "https://youtu.be/o-e68Xjs2As",
                        gif : "goodies.gif"
                    },
                    {
                        name :"Lạc Trôi Remix - Sơn Tùng M-TP",
                        image  : "lt.jpg",
                        avatar  : "sontung.jpg",
                        view :"1.3M" ,
                        time :"3 years",
                        author : "Sơn Tùng MTP",
                        check : true,
                        link : "https://youtu.be/Llw9Q6akRo4",
                        gif : "lt.gif"
                    },
                    {
                        name :"Lạc Chốn Hồng Trần Remix Lã Phong Lâm x Đại Mèo",
                        image  : "lcht.jfif",
                        avatar  : "bili.jpg",
                        view :"553K" ,
                        time :"9 months",
                        author : "BiliBili",
                        check : false,
                        link : "https://youtu.be/LJo0d9sASFI",
                        gif : "lcht.gif"
                    },
                    {
                        name :"ANH CHỈ CÓ 102 (02) | VINARAP - JP LONG x KUZZ",
                        image  : "acc102.jpg",
                        avatar  : "ansez.png",
                        view :"400K" ,
                        time :"5 months",
                        author : "Ansez",
                        check : false,
                        link : "https://youtu.be/L5nVIDA5zFY",
                        gif : "acc102.gif"
                    },
                    {
                        name :"Em iu - Andree Right Hand ft. Wxrdie x Bình Gold x 2pillz",
                        image  : "ei.jpg",
                        avatar  : "andree.jpg",
                        view :"998K" ,
                        time :"11 months",
                        author : "Andree Right Hand",
                        check : true,
                        link : "https://youtu.be/p7YGAKeDPkM",
                        gif : "ei.gif"
                    },
                    {
                        name :"Ơ Động Đất À? Không Phải Đấy Là Bọn Anh Đang Đi Lên - VÂN RUNG",
                        image  : "odda.jpg",
                        avatar  : "orinn.jpg",
                        view :"400K" ,
                        time :"3 months",
                        author : "Orinn Music",
                        check : false,
                        link : "https://youtu.be/5kT9DlHYiOE",
                        gif : "odda.gif"
                    },
                    {
                        name :"16 Typh - Người Chơi Hệ Đẹp「Cukak Remix」",
                        image  : "nchd.jpg",
                        avatar  : "1967.jpg",
                        view :"603K" ,
                        time :"5 months",
                        author : "1967 Music",
                        check : false,
                        link : "https://youtu.be/1VnsC7SgkBI",
                        gif : "nchd.gif"
                    },
                    {
                        name :"Đoạn Tuyệt Nàng Đi Ver2 Remix",
                        image  : "dtnd.jpg",
                        avatar  : "frexs.jpg",
                        view :"800K" ,
                        time :"1 year",
                        author : "Frexs Record",
                        check : false,
                        link : "https://youtu.be/1Y5AxyERJsA",
                        gif : "dtnd.gif"
                    },
                    {
                        name :"Ông Cháu Ơi Về Đội Của Chú | WanGanh Remix",
                        image  : "ocovdcc.jpg",
                        avatar  : "nhacsan.jpg",
                        view :"712K" ,
                        time :"8 months",
                        author : "Nhạc sàn remix",
                        check : false,
                        link : "https://youtu.be/erRTlNs8OkM",
                        gif : "ocovdcc.gif"
                    },
                    {
                        name :"Phong dạ hành Remix",
                        image  : "pdh.jpg",
                        avatar  : "djam.jpg",
                        view :"103K" ,
                        time :"3 months",
                        author : "DJ AM Official",
                        check : false,
                        link : "https://youtu.be/bXZgaAc2BB8",
                        gif : "pdh.gif"
                    }
                ],
    }
  }
}
</script>

<style>
*{
   margin : 0;
   padding : 0;
   /* box-sizing: border-box; */
}

html {
    scrollbar-width: none; /* For Firefox */
    -ms-overflow-style: none; /* For Internet Explorer and Edge */
}

html::-webkit-scrollbar {
    width: 0px; /* For Chrome, Safari, and Opera */
}

#app {
  overflow: scroll;
  -ms-overflow-style: none;
  scrollbar-width: none;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#app::-webkit-scrollbar{
  display : none;
}

#header{
  width: 100vw;
  height : 60px;
  background-color : #0f0f0f;
  /* border : 1px solid #000; */
  z-index: 1;
  position : fixed;
  top : 0;
}

#sidebar{
  position: fixed;
  top : 55px;
  width: 5%;
  height: 100vh;
  background-color: #0f0f0f;
}

@keyframes extendSidebar{
  from{
    width: 5%;
  }
  to{
    width: 15%;
  }
}

#sidebarextend{
  position: fixed;
  overflow-y: hidden;
  overflow-y: scroll;
  top : 55px;
  width: 15%;
  height: 100%;
  background-color: #0f0f0f;
  overflow: auto;
  -ms-overflow-style: none;
  animation: extendSidebar ease 0.0s;
}

#sidebarextend::-webkit-scrollbar{
  display: none;
}

.contentZoomOut{
  margin-left : 15% !important;
  width: 83% !important;
}

#content{
  margin-left : 5%;
  margin-top : 0px;
  /* margin-top : 60px; */
  width: 93%;
  height: 100%;
  background-color: #0f0f0f;
  padding : 32px 48px;
  min-height: 100vh;
}

</style>
