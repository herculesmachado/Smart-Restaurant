<template>
    <div class="items-list">
        <Item v-for="item in itemsList" :key="item.id" :item="item" />
    </div>
</template>
<script>
import Item from './Item.vue'
import axios from 'axios'

export default {
    name: 'ItemsList',
    components: {
        Item
    },
    data() {
        return {
            itemsList: []
        }
    },
    created() {
        // Atribui o this em ums variavel para ser chamada no itemList
        let self = this
        axios.get('http://localhost:3000/burguers').then(function (response) {
            // manipula o sucesso da requisição
            self.itemsList = response.data
        })
    }
}
</script>
<style lang="less" scoped>
@import '../assets/variables.less';
.items-list {
    display: flex;
    margin: 50px;
    
    @media (max-width: 768px) {
        flex-wrap: wrap;
        margin: 10px;
    }
    
}

</style>