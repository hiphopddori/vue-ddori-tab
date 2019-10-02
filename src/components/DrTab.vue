<template>
    <div class="mu-tab-cont" v-show="isActive">
        <slot></slot>
    </div>
</template>

<script>
export default {
    props:{
        name:{
            type:String,
            required:true
        },
        selected:{
            default:false
        },
        hidden:{
            default:false
        }
    },
    data(){
        return{
            isActive:false,            
        }
    }    
    ,mounted() {
        this.isActive = this.selected;
    },
    computed: {
        href(){
            return '#' + this.name.toLowerCase().replace(/ /g,'-');
        }
    },
    watch:{
        selected(value) {            
            this.isActive = value;
        },
    }
}
</script>

<style>
    .mu-tab-cont{height:100%;display:flex;flex-direction:column;/* justify-content:space-between; */}
</style>
