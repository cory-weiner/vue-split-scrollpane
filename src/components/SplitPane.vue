<template>
    <div class="splitpane_wrapper">
        <div class="scrollpane1" ref="paneone" v-on:scroll="handleScroll"><slot ></slot></div>
        <div class="scrollpane1" ref="panetwo">
        <slot class="scrollpane2"></slot>
        <div id="spacer"></div>
        </div>
    </div>
</template>

<script>
const _ = require('lodash')
    export default {
        data(){
            return {
                
            }
        },
    
        mounted(){
            this.$refs.panetwo.scrollTop = this.$refs.paneone.clientHeight
        },
        methods: {
         handleScroll(){
                // console.log(this.$refs.paneone.scrollTop)
                this.$refs.panetwo.scrollTop = this.$refs.paneone.scrollTop + this.$refs.panetwo.clientHeight
                document.getElementById("spacer").style.height = this.$refs.paneone.clientHeight+"px"; 
            },
            // handleScroll: _.debounce(function (){
            //     // console.log(this.$refs.paneone.scrollTop)
            //     this.$refs.panetwo.scrollTop = this.$refs.paneone.scrollTop + this.$refs.panetwo.clientHeight
            // }, 5),

            
            handleScroll2: _.debounce(function (){
                // console.log(this.$refs.paneone.scrollTop)
                this.$refs.paneone.scrollTop = this.$refs.panetwo.scrollTop - this.$refs.panetwo.clientHeight
            }, 5)
      
        }
    }
</script>

<style>
    .splitpane_wrapper{
        padding: 40px;
        background-color:#999999;
        display:flex;
        gap: 20px;
        height: calc(100vh - 80px);
        overflow-y:hidden;
    }
    .scrollpane1{
        background-color:white;
        overflow-y:scroll;

    }
    .scrollpane2{
        overflow-y:scroll;
        
    }

    .scrollpane1::-webkit-scrollbar {
  display: none;
}

/* Hide scrollbar for IE, Edge and Firefox */
.scrollpane1 {
  -ms-overflow-style: none;  /* IE and Edge */
  scrollbar-width: none;  /* Firefox */
}
</style>