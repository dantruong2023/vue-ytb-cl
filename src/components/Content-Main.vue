<template>
    <div>
        <template v-if="great4">
        <div class="rows" v-for="idx in Math.ceil(this.length/4)" v-bind:key="idx">
            <div v-for="i in 4" :key="i">
                <VideoPlayer           
                :name = "data[i-1+(idx-1)*4].name"
                :image = "data[i-1+(idx-1)*4].image"
                :avatar = "data[i-1+(idx-1)*4].avatar"
                :view="data[i-1+(idx-1)*4].view" 
                :time="data[i-1+(idx-1)*4].time"
                :author="data[i-1+(idx-1)*4].author"
                :check="data[i-1+(idx-1)*4].check"
                :link="data[i-1+(idx-1)*4].link"
                :gif="data[i-1+(idx-1)*4].gif"
                v-if="data[i-1+(idx-1)*4]"
                ></VideoPlayer>
            </div>
        </div>
        </template>
        <div class="rows" v-if="great4===false">
            <div v-for="i in 4" :key="i">
                <VideoPlayer           
                :name = "data[i-1].name"
                :image = "data[i-1].image"
                :avatar = "data[i-1].avatar"
                :view="data[i-1].view" 
                :time="data[i-1].time"
                :author="data[i-1].author"
                :check="data[i-1].check"
                :link="data[i-1].link"
                v-if="data[i-1]"
                ></VideoPlayer>
            </div>
        </div>
    </div> 
</template>
<script>
    import VideoPlayer from './VideoPlayer.vue'
    //Length title max = 58 + 3(...) . substring(0,58)
    export default{
        name : 'ContentMain',
        data(){
            return {
                length : 0,
                index : 0,
                great4 : false
            }
        },
        props:{
            msg : String,
            data : Array,
        },
        computed : {
            
        },
        methods:{
            
        },
        created : function() {
            this.length = this.data.length
            this.great4 = this.length > 4 
            this.index = 0
        },
        components : {
            VideoPlayer
        }
    }
</script>
<style>

.rows {
    margin: 40px 0;
}

.rows::after{
    content : '';
    display: block;
    clear: both;
}


</style>