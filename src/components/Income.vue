<script>

export default {
    data() {
        return {
            income: [],
            sum: "",
            date: "",
            sourceOfIncome: "",
        }
    },
    methods: {
        add() {
            if (this.sum === '' || this.date === '' || this.sourceOfIncome === '') {
                return
            }
            
            let income = JSON.parse(localStorage.getItem("income"));

            const newIncome = {
                id: this.income.length + 1,
                sum: this.sum,
                date: this.date,
                sourceOfIncome: this.sourceOfIncome,
            }


            if (income == null) {
                this.income.push(newIncome)
                localStorage.setItem("income", JSON.stringify(this.income));
            } else {
                income.push(newIncome);
                localStorage.setItem("income", JSON.stringify(income));
            }


            console.log(this.income)

            this.sum = '';
            this.date = '',
                this.sourceOfIncome = '';
        }
    }
}

</script>

<template>
    <div>

        <form class="Post" @submit.prevent>
            <input v-model="sum" type="number">
            <input v-model="date" type="date">
            <input v-model="sourceOfIncome" type="text">
            <button class="btn-con" @click="add">ADD</button>
        </form>

        <div class="info" v-for="item in income" key="item.id">
            <div>{{ item.sum }}</div>
            <div>{{ item.date }}</div>
            <div> {{ item.sourceOfIncome }}</div>
        </div>

    </div>
</template>

<style>
.Post {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 400px;
    height: 300px;
    margin: 1% auto;
    border: 2px solid #2dcdd3;
    background-color: #f4f7f7;
    border-radius: 20px;
    padding: 2%;
    font-size: 16px;
    margin-top: 50px;
}

input {
    width: 350px;
    height: 20px;
    margin-bottom: 20px;
    padding: 10px;
    font-size: 16px;
    border: 2px solid #5c9ea1;
    background-color: #ffffff9c;
    border-radius: 15px;
}

.btn-con {
    width: 200px;
    height: 30px;
    background-color: #2dcdd3;
    border: 1px solid transparent;
    border-radius: 20px;
    font-size: 16px;
}

.info {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-around;
    width: 400px;
    margin: 1% auto;
    border: 2px solid #2dcdd3;
    background-color: #f4f7f7;
    padding: 2%;
    font-size: 16px;
    margin-top: 50px;
}
</style>