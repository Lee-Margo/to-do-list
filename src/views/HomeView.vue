<script>
export default {
    data() {
        return {
            selectedTab:'',
            text:'',
            lastId:0,
            listData:[
                {id: 1,
                checked:false,
                content: '你好啊',},
            ],
        }
    },
    computed:{
        filterListData(){
            if(this.selectedTab === ''){
                return this.listData;
            }
            return this.listData.filter( list => list.checked === this.selectedTab);
        },
    },
    methods: {
        changeTab(tab){
            this.selectedTab = tab;
        },
        deleteList(id){
            this.listData = this.listData.filter((list)=>list.id !== id);
        },
        importList(){
            if(this.listData != ''){
                this.lastId = this.listData.at(-1).id;
            };
            if(this.text != ''){
                this.listData.push({
                    id: this.lastId+1,
                    checked:false,
                    content: this.text,
                });
            };
            this.text = '';
        },
        editList(list){
            const editContent = prompt('change the content');
            list.content = editContent;
        },
    },
};
</script>


<template>
<main>
    <div class="h-[30px] flex m-[10px]">
        <input type="text" class="w-8/12 " placeholder="請填寫事項" v-model="text">
        <button class="w-12 bg-slate-400 ml-1" @click="importList()">輸入</button>
    </div>
    <div class="bottom">
        <div class="tag-list flex">
            <button class="tag" @click="changeTab('')" :class="{ 'active': selectedTab==='' }">全部</button>
            <button class="tag" @click="changeTab(true)" :class="{'active': selectedTab === true }">已執行</button>
            <button class="tag" @click="changeTab(false)" :class="{'active': selectedTab === false }">未執行</button>
        </div>
        <table>
            <thead>
                <tr>
                    <th class="w-1/12">執行</th>
                    <th>事項</th>
                    <th class="w-1/12">功能</th>
                </tr>                
            </thead>
            <tbody class="data-show">
                <tr v-for="list in filterListData" :key="list.id">
                    <th><input type="checkbox" v-model="list.checked" ></th>
                    <th class="text-wrap">{{list.content}}</th>
                    <th >
                        <button @click="editList(list)" class="edit">Edit</button>
                        <button @click="deleteList(list.id)" class="delete">Delete</button>
                    </th>
                </tr>
            </tbody>            
        </table>
    </div>
</main>
</template>

<style scoped>
.active{
    @apply bg-red-100 text-black
}
.delete{
    @apply bg-blue-500 hover:bg-blue-700 text-white font-bold px-2 border border-blue-700 rounded
}
.edit{
    @apply bg-blue-500 hover:bg-blue-700 text-white font-bold px-2 mr-1 border border-blue-700 rounded
}
</style>
