<template>
    <div class="row" style="padding:10px;">
        <div class="col col-12 border rounded-lg colored-tiles tiles" v-for="(item, index) in this.wholesomeNews" :key="index" v-show="!item.data.stickied">
            <div class="row">
                
                <div class="col col-lg-12 col-xs-12" >
                    <!-- <h6> {{item.data.title}}</h6> -->
                    <video v-if="item.data.is_video " muted autoplay loop>
                         <source :src="item.data.secure_media.reddit_video.scrubber_media_url" type="video/mp4">
                    </video>
                    <video v-if="item.data.domain == 'gfycat.com' " muted autoplay loop>
                         <source :src="item.data.preview.reddit_video_preview.scrubber_media_url" type="video/mp4">
                    </video>
                    <img class="article-img" :src="item.data.url" v-if="!item.data.is_video && item.data.media == null">
                </div>
                <!-- <div class="col col-lg-9 col-xs-9">
                    <a :href="item.data.url"><strong>{{ item.data.title }}</strong></a>
                </div> -->
            </div>
        </div>
    </div>
</template>
<script>
let axios = require('axios');
export default {
    data() {
        return {
            wholesomeNews : []
        }
    },
    mounted() {
       axios.get('https://www.reddit.com/r/aww/.json?limit=50')
            .then((response) => {
                console.log(response.data)
                this.wholesomeNews = response.data.data.children
            })
    }
}
</script>

<style scoped>
    .colored-tiles {
        background-color: #f5f6fa;
    } 
    .tiles {
        margin-bottom: 20px;
        padding: 20px;
    } 
    .article-img {
        width: 100%;
    }
    video {
        width: 100%;
    }
</style>
