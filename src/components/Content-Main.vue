<template>
    <div>
        <div class="categories">
            <div class="category" v-for="i in tag.length > 10 ? 10 : tag.length" :key="i" :class="[{categoryActive : index == i-1}]" @click="filterbyTag(i-1,tag[i-1])">
                {{ tag[i-1] }}
            </div>
        </div>
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
                :gif="data[i-1].gif"
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
                great4 : false,
                // tag : ['All','Music','Bình Gold']
            }
        },
        props:{
            msg : String,
            data : Array,
            index : Number,
            filterTag : String,
            tag : Array
        },
        watch : {

        },
        methods:{
            filterbyTag : function(idx,value){
                this.$emit('update:filterTag',value)
                this.$emit('update:index',idx)
            }
        },
        created : function() {
            var self = this
            this.length = this.data.length
            this.great4 = this.length > 4 
            this.data.forEach(function(item){
                if(self.tag.length >= 10) {
                    return
                }
                if(self.tag.includes(item.author) == false) self.tag.push(item.author)
            })
        },
        components : {
            VideoPlayer
        }
    }
</script>
<style scoped>

div.categories{
    position: fixed;
    width: 100%;
    height: 50px;
    top : 60px;
    background-color : #0f0f0f;
    z-index: 1;
}

.category{
    float : left;
    margin-top : 10px;
    margin-right : 16px;
    background-color: black;
    color : #fff;
    padding : 6px 12px;
    width : auto;
    border-radius: 8px;
    cursor: pointer;
    font-weight: 400;
}

.category:hover{
    background-color : rgba(255, 255, 255, 0.2)
}

.categoryActive{
    color : #000 !important;
    background-color: #f1f1f1 !important;
}

div.categories::after{
    content: '';
    display: block;
    clear: both;
}



.rows {
    margin: 40px 0;
}

.rows::after{
    content : '';
    display: block;
    clear: both;
}


</style>