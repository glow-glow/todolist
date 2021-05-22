<template>
    <div class="todoListContainer">
        <div class="heading">
            <h2 id="title">Todo list</h2>
            <add-item-form
                v-on:reloadlist="getList()"
            />
        </div>
        <div>
        <list-view
        :items="items"
        v-on:reloadlist="getList()"
        />
        </div>
    </div>
</template>

<script>
import listView from "./listView";
import addItemForm from "./addItemForm";
import AddItemForm from "./addItemForm";
import ListItem from "./listItem";
import ListView from "./listView";
export default {
    components: {ListView, ListItem, AddItemForm},

    data:function (){
        return{
            items:[]
        }

    },
    methods:{
        getList(){
            axios.get('api/items')
            .then(response=>{
                this.items= response.data
            })
            .catch(error=>{
                console.log(error);
            })
        }

        },
    created(){
        this.getList();
    }
}
</script>

<style scoped>
.todoListContainer{
    width: 350px;
    margin:auto;
}
.heading{
    background: aliceblue;
    padding: 10px;
}
#title{
    text-align: center;
    margin: auto;
}
</style>
