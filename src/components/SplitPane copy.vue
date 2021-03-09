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
    export default {
        data(){
            return {
                isSyncingLeftScroll:false,
                isSyncingRightScroll: false
            }
        },
        mounted(){
            this.$refs.panetwo.scrollTop = this.$refs.paneone.clientHeight
        },
        methods: {
            handleScroll(){
   
                    this.$refs.panetwo.scrollTop = this.$refs.paneone.scrollTop + this.$refs.paneone.clientHeight
                    document.getElementById("spacer").style.height = this.$refs.paneone.clientHeight+"px"; 
  
                
   
            },
            // handleScrollTwo(){
           
            //         this.$refs.paneone.scrollTop = this.$refs.panetwo.scrollTop - this.$refs.panetwo.clientHeight
            //         document.getElementById("spacer").style.height = this.$refs.paneone.clientHeight+"px";
              

           
            // }
        }
    }
</script>

<style>
    .splitpane_wrapper{
        display:flex;
        height: 100vh;
        overflow-y:hidden;
    }
    .scrollpane1{
        overflow-y:scroll;
    }
    .scrollpane2{
        overflow-y:scroll;
    }
</style>