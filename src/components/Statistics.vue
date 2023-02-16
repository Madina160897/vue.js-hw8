<script >

export default {
    data() {
        return {
            purchase: JSON.parse(localStorage.getItem("purchase")),
            income: JSON.parse(localStorage.getItem("income")),
            purchaseAll: 0,
            incomeAll: 0,
            bigSum: 0,
        }
    },
    computed: {
        allPurchase() {
            this.purchaseAll = this.purchase.map(item => item.sum).reduce((a, b) => a + b, 0)
            return this.purchaseAll
        },

        allIncome() {
            this.incomeAll = this.income.map(item => item.sum).reduce((a, b) => a + b, 0)
            return this.incomeAll
        },

        foodIncome() {
            let food = this.purchase.filter(item => item.category == "Food")
            let all = food.map(item => item.sum).reduce((a, b) => a + b, 0)
            return all
        },

        clothIncome() {
            let cloth = this.purchase.filter(item => item.category == "Cloth")
            let all = cloth.map(item => item.sum).reduce((a, b) => a + b, 0)
            return all
        },

        enterIncome() {
            let entertainment = this.purchase.filter(item => item.category == "Entertainment")
            let all = entertainment.map(item => item.sum).reduce((a, b) => a + b, 0)
            return all
        },

        techIncome() {
            let technique = this.purchase.filter(item => item.category == "Technique")
            let all = technique.map(item => item.sum).reduce((a, b) => a + b, 0)
            return all
        },

        otherIncome() {
            let other = this.purchase.filter(item => item.category == "Other")
            let all = other.map(item => item.sum).reduce((a, b) => a + b, 0)
            return all
        },

        bigIncome() {
            this.purchase.forEach(item => { this.bigSum < item.sum ? this.bigSum = item.sum : item });
            let bigSumProd = this.purchase.find(item => item.sum == this.bigSum)
            return (`${bigSumProd.sum}`)
        },

    },
}

</script>

<template>
    <div class="block">
        <h2>Statistics:</h2>
        <b> Final expense: {{ allPurchase }} </b>
        <b>Final income: {{ allIncome }}</b>
        <div>
            <p>Costs by category:</p>
            <div>Food: {{ foodIncome }}</div>
            <div>Cloth: {{ clothIncome }}</div>
            <div>Entertainment: {{ enterIncome }}</div>
            <div>Technique: {{ techIncome }}</div>
            <div>Other: {{ otherIncome }}</div>
        </div>
        <p>Biggest expenses in the last month: {{ bigIncome }}</p>
    </div>
</template>

<style>
.block{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 400px;
    height: 350px;
    margin: 1% auto;
    border: 2px solid #2dcdd3;
    background-color: #f4f7f7;
    border-radius: 20px;
    padding: 2%;
    font-size: 20px;
    margin-top: 50px;
}

p{
    font-weight: 700;
}

</style>