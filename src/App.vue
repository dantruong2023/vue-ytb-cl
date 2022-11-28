<template>
  <div id="app">
    <Header id="header" msg="Welcome to Your Vue.js App"></Header>
    <SideBar id="sidebar"></SideBar>
    <ContentVideo id="content" msg="Hello" :data="dataVideo"></ContentVideo>
    
  </div>
</template>

<script>
import Header from './components/Header.vue'
import SideBar from './components/Sidebar-Left.vue'
import ContentVideo from './components/Content-Main.vue'


export default {
  name: 'App',
  components: {
    Header,
    SideBar,
    ContentVideo,
  },
  data(){
    return {
      dataVideo : [
                    {
                        name :"Bật chế độ bay lên - Bình Gold",
                        image  : "bcdbl.jpg",
                        avatar  : "avatar.jpg",
                        view :"985K" ,
                        time :"2 months",
                        author : "Đan Trường",
                        check : true,
                        link : "https://youtu.be/r842vn9Os0Y"
                    },
                    {
                        name :"Ông bà già tao lo hết",
                        image  : "obgtlh.jpg",
                        avatar  : "mylove.jpg",
                        view :"1.4M" ,
                        time :"8 months",
                        author : "Thu Trang",
                        check : true,
                        link : "https://youtu.be/siEhdhxiqHg"
                    },
                    {
                        name :"Tiếng pháo tiễn người",
                        image  : "tptn.jpg",
                        avatar  : "hungquan.jpg",
                        view :"186K" ,
                        time :"13 days",
                        author : "Hùng Quân",
                        check : true,
                        link : "https://youtu.be/KI6TFG0-mTY"
                    },
                    {
                        name :"Love potion number 9",
                        image  : "lpn9.jpg",
                        avatar  : "dolce.jpg",
                        view :"1.1M" ,
                        time :"11 months",
                        author : "Dolce Music",
                        check : false,
                        link : "https://youtu.be/-RqwGKFJbsE"
                    },
                    {
                        name :"Bốc bát họ | Bình Gold",
                        image  : "bbh.jpg",
                        avatar  : "binhgold.jfif",
                        view :"874K" ,
                        time :"3 months",
                        author : "Bình Gold",
                        check : true,
                        link : "https://youtu.be/gQ9U94eH7xQ"
                    },
                    {
                        name :"Hết nhạc con về",
                        image  : "hncv.jpg",
                        avatar  : "1967.jpg",
                        view :"200K" ,
                        time :"2 months",
                        author : "1967 Music",
                        check : false,
                        link : "https://youtu.be/CKgEdz3paa0"
                    },
                    {
                        name :"Chạnh lòng thương cô",
                        image  : "cltc.jpg",
                        avatar  : "hhd.jpg",
                        view :"357K" ,
                        time :"10 months",
                        author : "HOA HỒNG DẠI MUSIC",
                        check : false,
                        link : "https://youtu.be/xIyIP-fR7Xg"
                    },
                    {
                        name :"Sang Xịn Mịn REMIX - Gill ft. Kewtiie x CUKAK",
                        image  : "sxm.jpg",
                        avatar  : "djay.jpg",
                        view :"198K" ,
                        time :"6 months",
                        author : "Djay Boy",
                        check : false,
                        link : "https://youtu.be/g4HygG78cT0"
                    },
                    {
                        name :"Goodie - Tbynz",
                        image  : "goodies.jpg",
                        avatar  : "dinz.jpg",
                        view :"786K" ,
                        time :"1 year",
                        author : "Dinz Music",
                        check : false,
                        link : "https://youtu.be/o-e68Xjs2As"
                    },
                    {
                        name :"Lạc Trôi Remix - Sơn Tùng M-TP",
                        image  : "lt.jpg",
                        avatar  : "sontung.jpg",
                        view :"1.3M" ,
                        time :"3 years",
                        author : "Sơn Tùng MTP",
                        check : true,
                        link : "https://youtu.be/Llw9Q6akRo4"
                    },
                    {
                        name :"Lạc Chốn Hồng Trần Remix Lã Phong Lâm x Đại Mèo",
                        image  : "lcht.jfif",
                        avatar  : "bili.jpg",
                        view :"553K" ,
                        time :"9 months",
                        author : "BiliBili",
                        check : false,
                        link : "https://youtu.be/LJo0d9sASFI"
                    },
                    {
                        name :"ANH CHỈ CÓ 102 (02) | VINARAP - JP LONG x KUZZ",
                        image  : "acc102.jpg",
                        avatar  : "ansez.png",
                        view :"400K" ,
                        time :"5 months",
                        author : "Ansez",
                        check : false,
                        link : "https://youtu.be/L5nVIDA5zFY"
                    },
                    {
                        name :"Em iu - Andree Right Hand ft. Wxrdie x Bình Gold x 2pillz",
                        image  : "ei.jpg",
                        avatar  : "andree.jpg",
                        view :"998K" ,
                        time :"11 months",
                        author : "Andree Right Hand",
                        check : true,
                        link : "https://youtu.be/p7YGAKeDPkM"
                    },
                    {
                        name :"Ơ Động Đất À? Không Phải Đấy Là Bọn Anh Đang Đi Lên - VÂN RUNG",
                        image  : "odda.jpg",
                        avatar  : "orinn.jpg",
                        view :"400K" ,
                        time :"3 months",
                        author : "Orinn Music",
                        check : false,
                        link : "https://youtu.be/5kT9DlHYiOE"
                    },
                    {
                        name :"16 Typh - Người Chơi Hệ Đẹp「Cukak Remix」",
                        image  : "nchd.jpg",
                        avatar  : "1967.jpg",
                        view :"603K" ,
                        time :"5 months",
                        author : "1967 Music",
                        check : false,
                        link : "https://youtu.be/1VnsC7SgkBI"
                    },
                    {
                        name :"Đoạn Tuyệt Nàng Đi Ver2 Remix",
                        image  : "dtnd.jpg",
                        avatar  : "frexs.jpg",
                        view :"800K" ,
                        time :"1 year",
                        author : "Frexs Record",
                        check : false,
                        link : "https://youtu.be/1Y5AxyERJsA"
                    },
                    {
                        name :"Ông Cháu Ơi Về Đội Của Chú | WanGanh Remix",
                        image  : "ocovdcc.jpg",
                        avatar  : "nhacsan.jpg",
                        view :"712K" ,
                        time :"8 months",
                        author : "Nhạc sàn remix",
                        check : false,
                        link : "https://youtu.be/erRTlNs8OkM"
                    },
                    {
                        name :"Phong dạ hành Remix",
                        image  : "pdh.jpg",
                        avatar  : "djam.jpg",
                        view :"103K" ,
                        time :"3 months",
                        author : "DJ AM Official",
                        check : false,
                        link : "https://youtu.be/bXZgaAc2BB8"
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

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
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

#content{
  margin-left : 5%;
  margin-top : 60px;
  width: 93%;
  height: 100%;
  background-color: #0f0f0f;
  padding : 32px 48px;
  min-height: 100vh;
}

</style>
