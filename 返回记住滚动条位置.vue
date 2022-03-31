<template>
    <keep-alive>
        <router-view></router-view>
    </keep-alive>
</template>

<script>
export default {
    data() {
        return {
            scrollTop: 0
        }
    },
    beforeRouteLeave(){
        //注意滚动条的对象是谁？有可能是body 也有可能是你自定义产生的滚动条
        let app = document.getElementById('app')
        this.scrollTop = app.scrollTop || 0
        next()
    },
    activated() {
        document.getElementById('app').scrollTop = this.scrollTop
    }
}
</script>