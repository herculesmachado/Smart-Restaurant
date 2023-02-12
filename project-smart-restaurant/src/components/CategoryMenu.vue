<template>
    <div class="category-menu">
        <ul>
            <li v-for="category in categoriesList" :key="category.id" @click="onCategoryClick(category.id)"
                :class="{ 'active': isActive(category.id) }">
                <component :is="category.icon"></component>
                <p>{{ category.label }}</p>
            </li>
        </ul>
    </div>
</template>

<script>
import Pizza from './icons/pizza.vue';
import Combo from './icons/french-fries.vue';
import Deserts from './icons/ice-scream.vue';
import Drinks from './icons/smothie.vue';
import Burguers from './icons/burguers.vue';

export default {
    name: 'category-menu',
    components: {
        Pizza,
        Combo,
        Deserts,
        Drinks,
        Burguers,
    },
    data() {
        return {
            categoriesList: [
                {
                    label: 'Pizza',
                    icon: Pizza,
                    id: 'pizza',
                },
                {
                    label: 'Combo',
                    icon: Combo,
                    id: 'combo',
                },
                {
                    label: 'Deserts',
                    icon: Deserts,
                    id: 'deserts',
                },
                {
                    label: 'Drinks',
                    icon: Drinks,
                    id: 'drinks',
                },
                {
                    label: 'Burguers',
                    icon: Burguers,
                    id: 'burguers',
                },
            ],
            selectedCategory: 'pizza'
        }
    },
    methods: {
        onCategoryClick(id) {
            this.selectedCategory = id;
        },
        isActive(id) {
            return this.selectedCategory === id;
        }
    },
}
</script>

<style lang="less" scoped>
@import '../assets/variables.less';
.category-menu {
    width: 130px;
    height: 100vh;
    background: white;

    display: flex;
    align-items: center;


    ul {
        width: 100%;

        li {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100px;
            
            transition: all .2s;
            
            p {
                padding-top: 5px;
                font-weight: semi-bold;
                font-size: 14px; 
                color: @dark-grey;
            }

            svg {
                color: @dark-grey;
            }

            &.active {
                background-color: @light-yellow;
                border-radius: 8px;

                svg {
                    color: black;
                }

                p {
                    color:black;
                    font-weight: bold;
                }
            }
        }
    }

    @media @tablet {
        width: 100%;
        height: fit-content;
        
        ul {
            display: flex;
            justify-content: center;
            margin: 20px;
            overflow: scroll;
    
            li {
                width: 78px;
            }
            
        }
    }
}

</style>