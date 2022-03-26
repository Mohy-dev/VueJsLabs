<template>
    <div class="container mt-2">
        <div class="row">
            <div class="col-12">
                <headercomp/>
            </div>
        </div>
        <div class="row">
            <div class="col-4">
                <linkscomp/>
            </div>
            <div class="col-8" id="body">
                <bodycomp/>
            </div>
        </div>
        <div class="row">
            <div class="col-12">
                <footercomp/>
            </div>
        </div>
    </div>
</template>


<script>
import headercomp from './components/headercomp.vue'
import linkscomp from './components/linkscomp.vue'
import footercomp from './components/footercomp.vue'
import bodycomp from './components/bodycomp.vue'
import $ from 'jquery'
export default {
    components:{
        headercomp,
        bodycomp,
        linkscomp,
        footercomp,
        $
    }
}
</script>

<style scoped>
#body{
    height:45%;
    position: relative;
}
</style>