<template>
    <div class="container">
        <h1 class="notes_title">Notes App</h1>
        <div class="notes-form_item">
                <p>Title</p>
                <input v-model="title" class="notes-form_input">
                <p>Description</p>
                <input v-model="body" class="notes-form_input">
            </div>
            <button class="notes-form_btn" @click="createCard">NEW NOTE</button>
            <div class="block">
                <span>Notes App</span>
                <input class="search" v-model="searchQuery" placeholder="Find your note">
            </div>
        <div class="cards">
            <div class="card" v-for="card in cards" :key="card.id">
                <div class="card-title" :title="card.title">{{ card.title }}</div>
                <div class="card-body" :title="card.body">{{ card.body }}</div>
                <div class="card-date">{{ card.date}}</div>
                <span class="close" @click="removeItem(card.id)">x</span>
            </div>
        </div>
    </div>           
</template>

<script>
export default {
    data() {
        return {
            cards: [],
            title: '',
            body: '',
       }
    },
    methods: {
        createCard() {
            const res = {id: new Date(), title: this.title , body: this.body, date:new Date().toLocaleString()}
             this.cards.push(res)
            this.title= '';
            this.body= '';
        },
        removeItem:function(id) {
            this.cards = this.cards.filter((card) => {
			return card.id !== id;
        })
	},
    },
}
</script>

<style>
.container {
    margin: 0 auto;
    max-width: 600px;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items:center;
    flex-direction: column;
}
.notes_title {
    color:blueviolet;
}
.notes-form_item {
    font-size: 18px;
    text-align: center;
    width: 100%;
    justify-content: center;
}
.notes-form_input {
    border-radius: 10px;
    border: 1px solid gray;
    padding: 5px 10px;
    font-size: 20px;
    color: #423e3e;
    font-family:monospace;
    width: 100%;
}
.notes-form_btn {
    background: blueviolet;
    color: white;
    padding: 15px 45px;
    border: none;
    border-radius: 10px;
    font-size: 10px;
    cursor: pointer;
    text-transform: uppercase;
    font-weight: bold;
    margin-top: 10px;
}
.block {
    justify-content: space-between;
    display: flex;
    padding-top: 35px;
    width: 100%;
}
span {
    font-size: 25px;
}
.search {
    max-width: 450px; 
    width: 100%;
    border-radius: 10px;
    border: 1px solid gray;
    padding: 5px 10px;
    margin-left: 10px;
    font-size: 20px;
    color: #423e3e;
    font-family:monospace;
}
button {
    background-color: white;
    border: none;
    cursor: pointer;
    color: purple;
}
.cards {
 display: grid;
 grid-template-columns: 2fr 2fr;

}
.card {
 border: 2px solid purple;
 border-radius: 20px;
 margin-top: 25px;
 margin-left: 10px;
 margin-right: 10px;
 padding: 10px 20px;
 height: 120px;
 width: 300px;
 font-family: Verdana, Geneva, Tahoma, sans-serif;
 position: relative;
 }
 .card-title {
 color: purple;
 font-size: 25px;
 white-space: nowrap;
 overflow: hidden;
 text-overflow: ellipsis;
 }
 .card-body {
margin-top: 10px;
margin-bottom: 10px;
white-space: nowrap;
overflow: hidden;
text-overflow: ellipsis;
 }
 .card-date {
    font-size: 12px;
    color: darkgray;
    padding-top: 15px;
 }
.close {
    text-align: right;
    color: purple;
    cursor: pointer;
    position: absolute;
    top: 10px;
    right: 10px;
}
</style>