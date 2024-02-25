<script setup>
import TheWelcome from '../components/TheWelcome.vue'
</script>

<template>
  <main>
    <div class="h-[30px] flex m-[10px]">
        <input type="text" class="w-8/12 " placeholder="請填寫事項">
        <button class="w-12 bg-slate-400 ml-1">輸入</button>
    </div>
    <div class="bottom">
        <div class="tag-list flex">
            <button class="tag bg-red-100 text-black" data-tag = "all">全部</button>
            <button class="tag" data-tag = "execute">已執行</button>
            <button class="tag" data-tag = "nonExecute">未執行</button>
        </div>
        <table>
            <thead>
                <th>執行</th>
                <th>事項</th>
                <th>功能</th>
            </thead>
            <tbody class="data-show">
                <th><input type="checkbox" ></th>
                    <th>第一項</th>
                    <th>
                        <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold px-2 mr-1 border border-blue-700 rounded">Edit</button>
                        <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold px-2 border border-blue-700 rounded">Delete</button>
                    </th>
            </tbody>            
        </table>
    </div>
  </main>
</template>
