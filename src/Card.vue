<template>
    

    <div>
      <!-- <div @click="모달창열렸니=true; 누른거=i"> -->
        <div>
        <img :src="a.image">
        <h4 @click="send()">{{ a.title }}</h4>
        </div>
        <p>{{ a.price }} 원</p>
        
    </div>

</template>

<script>
export default {
    name:'CardComponent',
    props:{
        a: Object,
        모달창열렸니: Boolean,
        누른거 : Number,
        
    },
    methods:{
        send(){
            this.$emit('openModal', this.a.id)
        }
        
    }
}
</script>

<style>

</style>