<template>
    <div class="content">
        <table>
            <thead>
            <tr>
                <th>ID</th>
                <th>Цена</th>
                <th>Сроки аренды</th>
                <th>Инструменты</th>
                <th>Способ получения</th>
                <th>Способ оплаты</th>
                <th>Создано</th>
            </tr>
            </thead>
            <tbody>
            <tr v-for="order in orders" :key="order.id">
                <td style="word-wrap: break-word; max-width: 100px;" class="id" @click="openOrderDetails(order.id)">{{ order.id }}</td>
                <td>{{ order.price }}</td>
                <td>{{ getDate(order.start_leasing) }} - {{getDate(order.end_leasing)}}</td>
                <td>
                    <table style="max-width: 250px">
                        <tr v-for="name in getToolsNames(order.tools)">
                            <td>
                                {{ name }}
                            </td>
                        </tr>
                    </table>
                </td>
                <td>{{ getGetting(order.delivery_type) }}</td>
                <td>{{ getPayment(order.payment_type) }}</td>
                <td>{{ getDate(order.create_order_time) }}</td>
            </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
//import axios from 'axios';

import router from "@/js/router.js";

export default {
    name: 'OrdersTable',
    props: {
        orders: {
            required: true,
            type: Array
        }
    },
    mounted() {
    },
    methods: {
        getToolsNames(tools) {
            let names = []
            tools.map((tool) => {
                names.push(tool.name)
            })
            return names
        },
        getDate(isoString) {
            const date = new Date(isoString);
            const options = {
                year: 'numeric',
                month: 'long',
                day: 'numeric',
            };
            return date.toLocaleString('ru-RU', options);
        },
        getPayment(method) {
            if(method === "card") return "Банковской картой"
            else return "Наличными"
        },
        getGetting(method) {
            if(method === "to_door") return "Доставка"
            else return "Самовывоз"
        },
        openOrderDetails(id) {
            this.$router.push({name: "order-details", params: {id: id}})
        }
    },
};
</script>

<style scoped>
table {
    width: 870px;
    border-collapse: collapse;
}

th, td {
    border: 1px solid #ddd;
    padding: 8px;
}

th {
    background-color: #A1DA68;
}

.content {
    width: 100%;
}

.id {
    cursor: pointer;
    color: #6A983C;
}
</style>