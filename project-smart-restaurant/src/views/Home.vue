<template>
    <div class="home">
        <CategoryMenu />
        <ItemsList />
    </div>
</template>
<script>
import CategoryMenu from '../components/CategoryMenu.vue'
import ItemsList from '../components/ItemsList.vue'
export default {
    name: 'Home',
    components: {
        CategoryMenu,
        ItemsList
    }
}
</script>

<style scoped lang="less">
@import '../assets/variables.less';

.home {
    display: flex;

    @media (max-width: 768px) {
        flex-direction: column;
    }
}


</style>