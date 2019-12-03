<template>
  
        
     <div class="tab-bar-item"  @click="itemClick">
         <div v-if="!isActive"><slot  name="item-icon"> </slot></div>
         <div v-if="isActive"><slot  name="item-icon-active"></slot></div>
         <div :style="activeStyle"> <slot name="item-text"> </slot></div>  
       
     </div>
    
</template>

<script>

export default {
    name:"TabBarVue",
    props:{
    path: String,
    activeColor:{
        type:String,
        default:'red'
    }
    },
    data(){
        return{
            // isActive: true
        }
        
    },
    methods:{
        itemClick(){
           this.$router.push(this.path)
        //   this.$router.replace(this.path)区别push可以回退
        }
    },
    computed:{
        isActive(){
            return this.$route.path.indexOf(this.path) !== -1
        },
        activeStyle(){
            console.log(this.isActive);
            return this.isActive ?{color: this.activeColor} :{}
        }
    }

}
</script>

<style>
.tab-bar-item {
    flex: 1;
    text-align: center;
    height: 49px;
}
.tab-bar-item img{
width: 24px;
height: 24px;
}

</style>