<template>
    <div id="controller">
        <ul class="shirt-options options-ul">
           <li v-for="(item) of options.body" :key="item.id">{{item.color}}</li> 
        </ul>
        <ul class="pant-main-options options-ul">
           <li v-for="(item) of options.top" :key="item.id">{{item.color}}</li> 
        </ul>
        <ul class="number-options optons-ul">
           <li v-for="(item) of options.number" :key="item.id">{{item.color}}</li> 
        </ul>
    </div>
</template>
<script>
import Strings from '../strings.js'

export default {
    name: 'Controller',
    data() {
        return {
            options: Strings.controller
        }
    }
}
</script>
<style></style>