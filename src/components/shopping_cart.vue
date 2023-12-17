<script setup>
import { ref, watch, computed } from 'vue'
//商品
let list = ref([
    {
        id: 1,
        img: 'https://gw.alicdn.com/imgextra/i1/2084007988/O1CN01qW2y0128sYclLw9nx_!!2084007988.jpg_110x10000Q75.jpg_.webp',
        name: '老式怀旧儿童小吃',
        price: 100,
        stock: 10,
        num: 1,
        active: false,
    },
    {
        id: 2,
        img: 'https://gw.alicdn.com/imgextra/i1/2084007988/O1CN016QjHUJ28sYchdwlTQ_!!2084007988.jpg_110x10000Q75.jpg_.webp',
        name: '星球杯桶装巧克力夹心饼干',
        price: 200,
        stock: 30,
        num: 1,
        active: false,
    },
    {
        id: 3,
        img: 'https://gw.alicdn.com/imgextra/i1/2084007988/O1CN01qW2y0128sYclLw9nx_!!2084007988.jpg_110x10000Q75.jpg_.webp',
        name: '星球杯1000g大杯+旺仔牛奶糖7包',
        price: 300,
        stock: 2,
        num: 1,
        active: false,
    },
])



function totalPrice() {
    let total = 0;
    for (let i = 0; i < list.value.length; i++) {
        total += list.value[i].price * list.value[i].num;
    }
    return total;
}

const isAll = computed(() => list.value.every(item => item.active))

function selectAll() {
    const isSelectAll = isAll.value;
    list.value.forEach(item => item.active = !isSelectAll)
}


watch(() => list.value, (val) => {
    for (let i = 0; i < val.length; i++) {
        if (val[i].num > val[i].stock) {
            val[i].num = val[i].stock;
        }
        if (val[i].num < 0) {
            val[i].num = 0;
        }
    }
}, { deep: true })


</script>
<template>
    <section class=" container py-5">
        <p>使用bootstrap5</p>
        <h1 class=" text-primary border-bottom border-5 border-primary">购物车</h1>
        <ul class="bg-secondary-subtle d-flex list-unstyled fw-bold px-2">
            <li class="col">
                <input type="checkbox" @click="selectAll" :checked="isAll" id="all" class=" form-check-input">
                全选
            </li>
            <li class="col ">详情图</li>
            <li class="col text-center">商品名称</li>
            <li class="col text-center">单价</li>
            <li class="col text-center">数量</li>
            <li class="col text-center">合计</li>
        </ul>
        <ul class="d-flex list-unstyled px-2 align-items-center" v-for="item in list" :key="item.id">
            <li class="col"><input type="checkbox" class=" form-check-input" v-model="item.active" :id="item.id">选择
            </li>
            <li class="col"><img style="max-width: 80%;" class="" :src="item.img" alt=""></li>
            <li class="col text-center">{{ item.name }}</li>
            <li class="col text-center">{{ item.price }}</li>
            <li class="col text-center d-flex btn-group-sm" style="height: 100%;">
                <button class="btn btn-danger " @click="item.num--" :disabled="item.num <= 0">-</button>
                <input type="text" class=" input-group text-center" v-model="item.num" style="width: 50px;">
                <button class="btn btn-success" @click="item.num++" :disabled="item.num >= item.stock">+</button>
            </li>
            <li class="col text-center text-warning">{{ item.price * item.num }}</li>
        </ul>
        <div class=" d-flex justify-content-between">
            <p class="text-end text-primary">总价：{{ totalPrice() }}</p>
            <button class=" shadow-lg btn px-4 btn-primary">立即下单</button>
        </div>
    </section>
</template>
<style></style>