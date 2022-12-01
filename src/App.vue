<template>
  <div id="app">
  <Header id="header" 
  :search.sync="filter" 
  :is-extend.sync = "isExtend"
  :notification="notification"
  :idSelect.sync="idSelect">
  </Header>

  <SideBar id="sidebar" :idSelect.sync = "idSelect" v-if="isExtend == false" :key="keySidebar"></SideBar>
  <SideBarExtend id="sidebarextend" :idSelect.sync = "idSelect" v-if="isExtend == true" :key="keySidebar"></SideBarExtend>

  <ContentVideo id="content" :class="[{contentZoomOut : isExtend == true}]" 
    :data="data" 
    :filterTag.sync="filterTag" 
    :key="keyChild"
    :index.sync="indexTag"
    :tag="tag"
    :idSelect="idSelect"
    :shorts="short"
    :author="channel">
  </ContentVideo>
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
      if(search == ''){
          this.indexTag = 0
          this.idSelect = 0
          self.keyChild = Math.ceil(Math.random() * 1000)%123 + ''
      }
      for(var item of self.dataVideo)
      {
        if(item !== undefined && (item.name.toLowerCase().startsWith(search.toLowerCase(),0)==true || item.tag.includes(search) == true))
          self.data.push(item)
      }
      this.keyChild = Math.ceil(Math.random() * 1000)%123 + ''
      this.indexTag = 0
      this.idSelect = 0
      this.keySidebar = Math.ceil(Math.random() * 1000)%123 + ''
    },
    filterTag : function(){
      var self = this
      this.filter = ''
      self.data = []
      for(var item of self.dataVideo)
      {
        if(item !== undefined && item.tag.includes(self.filterTag))
          self.data.push(item)
      }
      self.keyChild = Math.ceil(Math.random() * 1000)%123 + ''
    },
    isExtend : function(){

    },
    idSelect : function(){
      var self = this
      if(this.idSelect >= 8 && this.idSelect <= 10){
        var name = ''
        switch(this.idSelect){
          case 8 : {
            name = 'Bình Gold'
            break
          }
          case 9 : {
            name = 'Ansez'
            break
          }
          case 10 : {
            name = 'Andree Right Hand'
            break
          }
        }
        this.authors.forEach(function(channel){
          if(name == channel.author){
            self.channel = channel
            return
          }
        })
      }
      self.keyChild = Math.ceil(Math.random() * 1000)%123 + ''
    }
  },
  methods:{
    convertToUser : function(str){
        str = str.toLowerCase();
        str = str.replace(/à|á|ạ|ả|ã|â|ầ|ấ|ậ|ẩ|ẫ|ă|ằ|ắ|ặ|ẳ|ẵ/g, "a");
        str = str.replace(/è|é|ẹ|ẻ|ẽ|ê|ề|ế|ệ|ể|ễ/g, "e");
        str = str.replace(/ì|í|ị|ỉ|ĩ/g, "i");
        str = str.replace(/ò|ó|ọ|ỏ|õ|ô|ồ|ố|ộ|ổ|ỗ|ơ|ờ|ớ|ợ|ở|ỡ/g, "o");
        str = str.replace(/ù|ú|ụ|ủ|ũ|ư|ừ|ứ|ự|ử|ữ/g, "u");
        str = str.replace(/ỳ|ý|ỵ|ỷ|ỹ/g, "y");
        str = str.replace(/đ/g, "d");
        str = str.replace(/\u0300|\u0301|\u0303|\u0309|\u0323/g, ""); // Huyền sắc hỏi ngã nặng 
        str = str.replace(/\u02C6|\u0306|\u031B/g, ""); // Â, Ê, Ă, Ơ, Ư
        return str.replaceAll(' ','');
    }
  },
  created: function() {
    var self = this
    this.filter = ''
    this.dataVideo.forEach(function(item){
        item.tag.push(item.author)
        if(self.tag.includes(item.author) == false) self.tag.push(item.author)

        //Push all authors author : function(avatar,author,verified,username,sub,videos)
        var isExist = false 
        self.authors.forEach(function(author){
            if(author.author == item.author) isExist = true
        })
        if(isExist==false){
          var videos = []
          var channel = new self.author(
                item.avatar,
                item.author,
                item.check,
                self.convertToUser(item.author) + Math.floor(Math.random()*1000),
                Math.ceil(Math.random()*998) + 'K',
                videos,
                item.banner
          )
          for(var video of self.dataVideo){
            if(video.author == channel.author){
              channel.videos.push(video)
            }
          }
          self.authors.push(channel)
        }
    })
  }
  ,
  data(){
    return {
      indexTag : 0,
      tag : ['All','Music'],
      idSelect : 0,
      isExtend : false,
      keyChild : '',
      keySidebar : 'key',
      data : [],
      filter : 'start',
      filterTag : 'all',
      author : function(avatar,author,verified,username,sub,videos,banner){
                this.avatar = avatar
                this.author = author
                this.check = verified
                this.username = username
                this.subscribers = sub
                this.videos = videos
                this.banner = banner
            },
      authors : [

      ],
      channel : '',
      notification : [
        {
          avatar : 'avatar.jpg',
          content : 'Technology used : Html - CSS - VueJS - icons global',
          time : '0 giây trước',
          img : ''
        },
        {
          avatar : 'hungquan.jpg',
          content : 'Hùng Quân đã tải lên: Tiếng pháo tiễn người',
          time : '13 ngày trước',
          img : 'tptn.jpg'
        },
        {
          avatar : 'binhgold.jfif',
          content : 'Bình Gold đã tải lên: Bật chế độ bay lên - Bình Gold',
          time : '2 tháng trước',
          img : 'bcdbl.jpg'
        },
        {
          avatar : 'binhgold.jfif',
          content : 'Bình Gold đã tải lên: Ông bà già tao lo hết - Bình Gold',
          time : '8 tháng trước',
          img : 'obgtlh.jpg'
        },
        {
          avatar : 'andree.jpg',
          content : 'Andree Right Hand đã tải lên: Em iu - Andree Right Hand ft. Wxrdie x Bình Gold x 2pillz',
          time : '11 tháng trước',
          img : 'ei.jpg'
        }
      ],
      dataVideo : [
                    {
                        name :"Bật chế độ bay lên - Bình Gold",
                        image  : "bcdbl.jpg",
                        avatar  : "binhgold.jfif",
                        view :"985K" ,
                        time :"2 months",
                        author : "Bình Gold",
                        banner : 'binhgold.png',
                        check : true,
                        link : "https://youtu.be/r842vn9Os0Y",
                        gif : 'bcdbl.gif',
                        tag : ['All','Music','Đan Trường','Bình Gold'],
                        description : 'BCDBL - Bình Gold | Bật Chế Độ Bay Lên | Nhạc Cực Căng'
                        
                    },
                    {
                        name :"Ông bà già tao lo hết - Bình Gold",
                        image  : "obgtlh.jpg",
                        avatar  : "binhgold.jfif",
                        view :"1.4M" ,
                        time :"8 months",
                        author : "Bình Gold",
                        banner : 'binhgold.png',
                        check : true,
                        link : "https://youtu.be/siEhdhxiqHg",
                        gif  : "obgtlh.gif",
                        tag : ['All','Music','Đan Trường','Bình Gold'],
                        description : 'Costume:  Venesto, SexyM, Bigent, Shadowiii3, Apex Solitaire Jewerly, the Suits house, Aobvns, DANG and madebyLYSKELI'
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
                        gif : "tptn.gif",
                        tag : ['All','Music','Đan Trường']
                    },
                    {
                        name :"ANH CHỈ CÓ 102 (02) | VINARAP - JP LONG x KUZZ",
                        image  : "acc102.jpg",
                        avatar  : "ansez.png",
                        view :"400K" ,
                        time :"5 months",
                        author : "Ansez",
                        banner : 'ansez.png',
                        check : false,
                        link : "https://youtu.be/L5nVIDA5zFY",
                        gif : "acc102.gif",
                        tag : ['All','Music','Đan Trường'],
                        description : 'ANH CHỈ CÓ 102 (02) | VINARAP (PINO REMIX) - JP LONG x KUZZ | ANSEZ RELEASE #ansez #vinarap #vinrapansez'
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
                        gif : "lpn9.gif",
                        tag : ['All','Music','Đan Trường']
                    },
                    {
                        name :"Bốc bát họ | Bình Gold",
                        image  : "bbh.jpg",
                        avatar  : "binhgold.jfif",
                        view :"874K" ,
                        time :"3 months",
                        author : "Bình Gold",
                        banner : 'binhgold.png',
                        check : true,
                        link : "https://youtu.be/gQ9U94eH7xQ",
                        gif : 'bbh.gif',
                        tag : ['All','Music','Đan Trường','Bình Gold'],
                        description : '✈ BỐC BÁT HỌ I BÌNH GOLD I NAM DUCK REMIX I PMT .'
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
                        gif : "hncv.gif",
                        tag : ['All','Music','Đan Trường']
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
                        gif : "cltc.gif",
                        tag : ['All','Music','Đan Trường']
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
                        gif : "sxm.gif",
                        tag : ['All','Music','Đan Trường']
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
                        gif : "goodies.gif",
                        tag : ['All','Music','Đan Trường']
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
                        gif : "lt.gif",
                        tag : ['All','Music','Đan Trường']
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
                        gif : "lcht.gif",
                        tag : ['All','Music','Đan Trường']
                    },
                    {
                        name :"Em iu - Andree Right Hand ft. Wxrdie x Bình Gold x 2pillz",
                        image  : "ei.jpg",
                        avatar  : "andree.jpg",
                        view :"998K" ,
                        time :"11 months",
                        author : "Andree Right Hand",
                        banner : 'andree.png',
                        check : true,
                        link : "https://youtu.be/p7YGAKeDPkM",
                        gif : "ei.gif",
                        tag : ['All','Music','Đan Trường'],
                        description : 'Sponsored by $maker & Jagermeister Producer: 2pillz Director: Tungage & Minh Bi'
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
                        gif : "odda.gif",
                        tag : ['All','Music','Đan Trường']
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
                        gif : "nchd.gif",
                        tag : ['All','Music','Đan Trường']
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
                        gif : "dtnd.gif",
                        tag : ['All','Music','Đan Trường']
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
                        gif : "ocovdcc.gif",
                        tag : ['All','Music','Đan Trường']
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
                        gif : "pdh.gif",
                        tag : ['All','Music','Đan Trường']
                    }
                ],
      short:[
        {
          avatar : 'dinz.jpg',
          author : 'Dinz',
          source : 'spiderman.mp4',
          like : '421K',
          comment : '25.9K'
        },
        {
          avatar : 'avatar.jpg',
          author : 'Đan Trường',
          source : 'cake.mp4',
          like : '89.3K',
          comment : '6.1K'
        },
        {
          avatar : 'mylove.jpg',
          author : 'Thu Trang',
          source : 'anvat.mp4',
          like : '189.7K',
          comment : '13.4K'
        }
      ]
    }
  }
}
</script>

<style>
*{
   margin : 0;
   padding : 0;
}

html {
    scrollbar-width: none; 
    -ms-overflow-style: none; 
}

html::-webkit-scrollbar {
    width: 0px; 
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
  position: fixed;
  z-index: 0;
  margin-left : 5%;
  margin-top : 0px;
  /* margin-top : 60px; */
  width: 93%;
  height: 100%;
  background-color: #0f0f0f;
  padding : 32px 48px;
  min-height: 100vh;
  overflow-y: auto;
}

#content::after{
  content: '';
  display : block;
  margin-bottom: 200px;
}

</style>
