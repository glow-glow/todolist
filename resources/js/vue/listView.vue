<template>
    <div>
       <div v-for="(item,index) in items" :key="index">
           <list-item
               :item="item"
               class="item"
               v-on:itemChanged="$emit('reloadlist')"

           />
       </div>
    </div>
</template>

<script>
import listItem from "./listItem";
import ListItem from "./listItem";
export default {
    components: {ListItem},
    props: ['items'],
comments:{
    listItem
}
}
</script>

<style scoped>
.item{
    background: aquamarine;
    padding: 5px;
    margin-top: 5px;
}

</style>

