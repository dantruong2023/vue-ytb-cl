<template>
<div class="sidebar">
    <div class="home active">
        <i class="ti-home"></i>
        <p>Home</p>
    </div>
    <div class="short">
        <i class="ti-video-clapper"></i>
        <p>Shorts</p>
    </div>
    <div class="sub">
        <i class="ti-user"></i>
        <p>Subscriptions</p>
    </div>
    <div class="library">
        <i class="ti-gallery"></i>
        <p>Library</p>
    </div>
</div>
</template>

<script>
    export default{
        name : 'Sidebar_Left',
        data() {
            return {

            }
        }
            
    }
</script>

<style scoped>

div{
    color : white;
}

.home:hover, .short:hover, .sub:hover, .library:hover{
    background-color: rgba(255, 255, 255, 0.1);
    border-radius: 10px;
    cursor: pointer;
}

i, p{
    color : inherit;
}
.active{
    color : red !important;
}

.home,
.short,
.sub, .library{
    padding : 16px 0; 
    width: 100%;
}

.home i,.short i,.sub i, .library i{
    font-size: 20px;
}

.home p,.short p,.sub p, .library p{
    margin-top : 8px;
    font-size: 9px;
}


</style>