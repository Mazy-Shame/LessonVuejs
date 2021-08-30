<template>
    <div class="root">
       <img v-if="showImg" src="../assets/logo.png" :style="imgStyles">
       <div v-else>hello shawerma kot</div>
    </div>
    <div>
        <button class="shadow" @click="activateShadow">Тень</button>
    </div>
    <button @click="switchImg" :class=" btnClassactive? 'btnactive': '' "> {{ btnClassactive? switchbtntext2 : switchbtntext1}} </button>
    <label>
        Ширина: {{imgSizes.currentWidth}}
        <input type="range" :value="imgSizes.currentWidth" :max="imgSizes.maxWidth" @input="imgSizes.currentWidth = $event.target.value" min="0">
    </label>
    <label>
        Высота: {{imgSizes.currentHeight}}
        <input type="range" :value="imgSizes.currentHeight" :max="imgSizes.maxHeight" @input="imgSizes.currentHeight = $event.target.value" min="0">
    </label>
    <label>
        Угол: {{imgSizes.imgDegreecurrent}}
        <input type="range" :value="imgSizes.imgDegreecurrent" :max="imgSizes.imgDegreemax" @input="imgSizes.imgDegreecurrent = $event.target.value" min="0">
    </label>
    
</template>

<script>
export default {
    name: 'MyComponent',
    data() {
        return{
            showImg: true,
            imgSizes: {
                maxWidth: 680,
                maxHeight: 480,
                currentWidth: 680,
                currentHeight: 480,
                imgDegreemax: 360,
                imgDegreecurrent: 0,
                shawowpx: 0
            },
            btnClassactive: false,
            switchbtntext1: "нажмите чтобы изменить",
            switchbtntext2: "изменилося"

        }
    },
    
    methods: {
        switchImg() {
            if (this.showImg == true){
                this.showImg = false
            }
            else{
                this.showImg = true
            }

            if (this.btnClassactive == true){
                this.btnClassactive = false
            }
            else{
                this.btnClassactive = true
            }
        },

        activateShadow() {
            if( this.imgSizes.shawowpx == 0 ){
                this.imgSizes.shawowpx = 10
            }
            else{
                this.imgSizes.shawowpx = 0
            }
        }
    },

    computed: {
        imgStyles() {
            return {
                width: `${this.imgSizes.currentWidth}px`,
                height: `${this.imgSizes.currentHeight}px`,
                transform: `rotate(${this.imgSizes.imgDegreecurrent}deg)`,
                boxShadow: `${this.imgSizes.shawowpx}px ${this.imgSizes.shawowpx}px ${this.imgSizes.shawowpx}px ${this.imgSizes.shawowpx}px #000`
            }
        }
    }

    
    
}
</script>

<style scoped>
   button {
       margin-right: 10px;
   }
   
   .btnactive {
       background-color: burlywood;
   }

</style>