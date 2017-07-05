<template>
    <div class="container" role="main" id="app">
        <div class="content">
            <img class="content__logo" src="./assets/logo.png">
            <h1 class="content__title" role="heading">TODO</h1>
        </div>
        
        <div class="task">
            <input class="task__input" role="textbox" v-model="newItem" type="text">
            <button class="task__button" role="button" v-on:click="addItem(newItem)">+</button>
            
            <ul class="task__list" role="list">
                <li class="task__list__item" role="listitem"
                    v-for="(item, index) in list" :key="index">
                    <button class="task__list__button" v-on:click="removeItem(index)">-</button>
                    {{ item.text }}
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    name: 'app',
    data () {
      return {
        list: [ ],
        newItem: ""
      }
    },
    methods: {
        addItem (newItem) {
            if(newItem){
                this.list.push({
                text: newItem
                })
            }
            this.newItem= "";
        },

        removeItem (index) {
            const newList = this.list.filter(function(item, i) {
                return index !== i;
            })
            this.list = newList;
        }
    }
}
</script>

<style>
    .container {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }

    .content {
        width: 50%;
        display: flex;
        margin: 0 auto;
        justify-content: center;
    }

    .content__logo {
        width: 100px;
        height: 100px;
        transform: scale(.7);
    }

    .content__title {
        text-align: start;
        margin-top: 40px;
        font-weight: normal;
    }

    .task {
        width: 50%;
        margin: 0 auto;
    }

    .task__list {
        list-style-type: none;
        padding: 0;
        width: 400px;
        margin: 10px auto;
    }

    .task__list__item {
      width: 50%;
      margin: 0 auto;
      text-align: left;
    }

</style>
