<script>

export default {
    data() {
        return {
            products: [],
            sum: "",
            date: "",
            category: "",
        }
    },
    methods: {
        add() {
            if (this.sum === '' || this.date === '' || this.category === '') {
                return
            }

            let purchase = JSON.parse(localStorage.getItem("purchase"));

            const newPurch = {
                sum: this.sum,
                date: this.date,
                category: this.category,
            }

            if (purchase == null) {
                this.products.push(newPurch)
            localStorage.setItem("purchase", JSON.stringify(this.products));
            } else {
                purchase.push(newPurch);
                localStorage.setItem("purchase", JSON.stringify(purchase));
            }

            
            console.log(this.products)

            this.sum = '';
            this.date = '',
                this.category = '';
        }
    }
}

</script>

<template>
    <div>

        <form class="Post" @submit.prevent>
            <input v-model="sum" type="number">
            <input v-model="date" type="date">
            <select v-model="category">
                <option value="Food">Food</option>
                <option value="Cloth">Cloth</option>
                <option value="Entertainment">Entertainment</option>
                <option value="Technique">Technique</option>
                <option value="Other">Other</option>
            </select>
            <button class="btn-con" @click="add">ADD</button>
        </form>

        <div class="info" v-for="post in products" key="post.id">
            <div>{{ post.sum }}</div>
            <div>{{ post.date }}</div>
            <div> {{ post.category }}</div>
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

select {
    width: 375px;
    height: 40px;
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