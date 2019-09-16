<template>
    
    <div>
        <ul class="mu-tab">
            <li v-for="tab in tabs" :class="{ 'active': tab.isActive}" v-bind:key="tab.name" v-show="!tab.hidden"> 
                <!--
                <a :href="tab.href" @click="onClickTab(tab)">{{tab.name}}</a>  
                -->
                <a @click="onClickTab(tab)">{{tab.name}}</a>  
            </li>
        </ul>

        <div class="mu-tab-body">
            <slot name="add-condition"></slot>
            <slot></slot>
        </div>

    </div>
</template>

<script>

import DrTab from "./DrTab.vue";

export default {
    
    props:{       
    },
    data(){
        return{
            tabs:[]
        }        
    }    
    ,created() {
        this.tabs=this.$children;
    },
    mounted() {
        
    }
    ,methods: {
        onClickTab(selectedTab){
            let selInfo = null;
            this.tabs.forEach((tab,idx) =>{
                tab.isActive = (tab.name == selectedTab.name);
                if (tab.isActive){
                    selInfo = {tabIndex:idx,tabName:selectedTab.name};                    
                }
            });

            this.$emit("onChange",selInfo);
        },
    }    
}
</script>

<style>
    
    
    .mu-tab{display:inline-block;width:100%;background-color:#fff}
    .mu-tab:after{display:block;content:'';clear:both;visibility:hidden;height:0}
    .mu-tab > li{float:left;position:relative}
    .mu-tab > li > a{display:block;min-width:130px;padding:11px 15px 10px;border-top-left-radius:4px;border-top-right-radius:4px;background-color:#98a9c4;text-align:center;color:#fff}
    .mu-tab > li > a:hover{background-color:#4d88db}
    .mu-tab > li > a:active,.mu-tab > li.active > a{background-color:#75a3e4}
    .mu-tab > li.disabled > a{background-color:#f5f5f5;color:#bbb;cursor:no-drop}

    
    /* tab */
    .mu-tab{background:none;display:block;}
    .mu-tab > li{list-style-type:none;}
    .mu-tab > li + li{margin:0;}
    .mu-tab > li > a{background-color:#2b3036;border:1px solid #212428;border-radius:0;min-width:90px;height:27px;line-height:25px;font-size:13px;color:rgba(255, 255, 255, 0.5);font-weight:400;padding:0 15px;}
    .mu-tab > li > a:hover{background-color:#23262b;border-color:#181818;}
    .mu-tab > li.active > a{background-color:#4f26ad;border-color:#44228a;color:#fff;}
    .mu-tab > li.disabled > a{background:#b6b6b6;color:#dbdbdb;}
    .mu-tab-body{position:relative;padding:10px;}
    .mu-tab-body > .mu-btn{float:right;margin-top:-42px;}
    .mu-tab-sub{height:27px;margin-bottom:10px;}
    .mu-tab-sub > li + li{margin-left:6px;}
    .mu-tab-sub > li a{background-color:#2b3036;border:1px solid #181818;border-radius:13px;min-width:100px;height:27px;line-height:25px;font-size:13px;font-weight:400;padding:0 10px;}
    .mu-tab-sub > li.active > a{background-color:#4f26ad;border-color:#44228a;}
    .mu-tab-option{position:absolute;top:-30px;right:0;line-height:26px;font-size:0;}
    .mu-tab-option > *{vertical-align:middle;}
    .mu-tab-option > * + *{margin-left:10px;}
    .mu-tab-option > span{font-size:13px;}
    .mu-tab{flex:0 0 0;}
    .mu-tab-body{flex:1;}
    .mu-tab-cont{height:100%;display:flex;flex-direction:row;justify-content:center;flex-wrap:wrap;}
    .mu-tab-sub{flex:0 0 0;}

</style>
