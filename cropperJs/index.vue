<template>
    <div class="main" v-if="isShowSee">
        <!--查看上传图片-->
        <a-modal v-model="isShowSee" centered :footer="null">
            <div class="container">
                <br />
                <div class="img-container">
                    <img :src="imageUrl" ref="image" alt="">
                </div>
                <div class="modal-submit" @click="sureSava">确认裁剪</div>
            </div>
        </a-modal>
    </div>
</template>

<style scoped>
    .modal-submit{
        color: #ffffff;
        padding: 10px;
        cursor: pointer;
        text-align: center;
        border-radius: 4px;
        background: #00AF92;
        margin-top: 20px;
        margin-bottom: 10px;
    }
</style>

<script> 
    import application from '../../common/application';

    import Cropper from 'cropperjs'
    import 'cropperjs/dist/cropper.css'
    import Country from "../../common/country";

    export default {
        props: {
            imageUrl: {
                required: true
            },
            isShowSee: {
                required: true
            }
        },
        components: {
            Cropper
        },
        mixins: [mixins],
        data: () => ({
            application: application,
            country: Country.country_list,
            myCropper: null,
            afterImg: ''
        }),
        mounted () {
            this.init()
        },
        methods: {
            init(){
                this.myCropper = new Cropper(this.$refs.image, {
                    viewMode: 1,
                    dragMode: 'none',
                    initialAspectRatio: 1,
                    aspectRatio: 1,
                    preview: '.before',
                    background: false,
                    autoCropArea: 0.6,
                    zoomOnWheel: false,
                })
            },
            sureSava(){
                this.afterImg = this.myCropper.getCroppedCanvas({
                    imageSmoothingQuality: 'high'
                }).toDataURL('image/jpeg')
               /* console.log(this.afterImg)*/
                this.handleBackImageSrc(this.afterImg);
            },
            handleBackImageSrc(afterImg) {
                this.$emit("handleBackImageSrc", afterImg);
            }
        }
    }
</script>
