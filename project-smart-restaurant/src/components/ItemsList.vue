<template>
    <div class="items-list">
        {{ selectedCategory }}
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
    created() {},
    computed: {
        selectedCategory: {
            get() {
                // Pega a categoria ao clicar
                return this.$store.state.selectedCategory;
            }
        }
    }, 
    methods: {
        getItemsList() {
            // Atribui o this em ums variavel para ser chamada no itemList
            const self = this
            axios.get(`http://localhost:3000/${self.selectedCategory}`).then(function (response) {
                // manipula o sucesso da requisição
                self.itemsList = response.data
            })
        }
    },
    watch: {
        selectedCategory() {
            this.getItemsList()
        }
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