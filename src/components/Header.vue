<template>
  <div class="header">
    <i class="ti-menu"></i>
    <div class="logo">
      <svg class="yt-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 576 512"><path d="M549.655 124.083c-6.281-23.65-24.787-42.276-48.284-48.597C458.781 64 288 64 288 64S117.22 64 74.629 75.486c-23.497 6.322-42.003 24.947-48.284 48.597-11.412 42.867-11.412 132.305-11.412 132.305s0 89.438 11.412 132.305c6.281 23.65 24.787 41.5 48.284 47.821C117.22 448 288 448 288 448s170.78 0 213.371-11.486c23.497-6.321 42.003-24.171 48.284-47.821 11.412-42.867 11.412-132.305 11.412-132.305s0-89.438-11.412-132.305zm-317.51 213.508V175.185l142.739 81.205-142.739 81.201z"/></svg>
      <h2 class="yt-title">Youtube <span>VN</span></h2>
    </div>
    
    <div class="search-bar">
      <i class="ti-search search-icon"></i>
      <input type="text" class="input-bar" placeholder="Search">
      <button title="Search" class="btn-search-bar"><i class="ti-search"></i></button>
    </div>

    <div class="user">
      <div class="img">
        <img src="/assets/img/avatar/avatar.jpg" alt="" width="32px" height="32px">
      </div>
      <i title="Notifications" class="ti-bell"></i>
      <i title="Create" class="ti-video-camera"></i>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
*{
  color : white;
}
.active{
  color : red;
}

i:hover{
  cursor : pointer;
}

i.search-icon{
  cursor: auto;
}

.header{
  position : relative;
}

i.ti-menu{
  --size : 50px;
  position : absolute;
  font-size : 24px;
  line-height: var(--size);
  float : left;
  left : 1%;
  top : 50%;
  transform : translateY(-50%);
  min-width: 42px;
  width : var(--size);
  height : var(--size);
  border-radius: 50%;
}



.logo{
  position: absolute;
  left : 6%;
  height: 100%;
  width : 200px;
}

.logo::after{
  clear: both;
}

.logo svg:hover, .logo h2{
  cursor: pointer;
}

.yt-icon{
  position: absolute;
  height : 24px;
  top : 50%;
  transform : translateY(-50%);
  fill : red;
  left : 0;
}

.yt-title{
  position: absolute;
  font-size: 20px;
  font-weight: 600;
  top : 50%;
  transform : translateY(-50%);
  left : 15%;
}
.yt-title span{
  position: absolute;
  right : -15%;
  font-size: 8px;
  font-weight: 100;
}

.search-bar{
  --radius : 40px;
  position: absolute;
  top : 50%;
  left : 50%;
  width: 35%;
  height : 70%;
  transform: translateY(-50%) translateX(-50%);
  border : 1px solid white;;
  border-radius: var(--radius);
  padding : 0 30px;
}

.search-bar i {
  float : left;
  height: 100%;
  line-height: 40px;
  padding : 0 20px 0 0;
}

.input-bar{
  background-color: rgba(0,0,0,0);
  height: 100%;
  width : 80%;
  font-size: 16px;
  border : none;
  line-height: 100%;
  float : left;
}

.input-bar:focus{
  outline: none;
}

.btn-search-bar{
  position: absolute;
  height: 100%;
  width: 15%;
  line-height: 100%;
  background-color: hsla(0, 0%, 100%, 0.08);
  border : 1px solid hsl(0, 0%, 18.82%);
  border-radius : 0 40px 40px 0 ;
  padding : 0 32px;
  right : 0;
  cursor: pointer;
}

.user{
  position: absolute;
  width : 30%;
  height: 100%;
  right : 0;
}
.user div.img{
  position: relative;
  height: 100%;
  width: 10%;
  float : right;
  margin-right : 24px;
}
.user div.img img{
  position: absolute;
  top : 50%;
  left : 50%;
  transform: translateY(-50%) translateX(-50%);
  right : 0;
  border-radius: 50%;
  cursor: pointer;
  /* left : -50%; */
}
i.ti-bell, i.ti-video-camera{
  --size : 50px;
  font-size : 24px;
  line-height: var(--size);
  float : right;
  width: var(--size);
  height: var(--size);
  border-radius: 50%;
}

i.ti-menu:hover,
i.ti-bell:hover,
i.ti-video-camera:hover{
  background-color : rgba(255, 255, 255, 0.1)
}
</style>
