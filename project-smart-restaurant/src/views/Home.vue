<template lang="">
    <categoryMenu/>
</template>
<script>
import categoryMenu from '../components/CategoryMenu.vue'
import axios from 'axios'
export default {
    name: 'Home',
    components: {
        categoryMenu
    },
    created() {
        axios.get('http://localhost:3000/burguers').then(function (response) {
            // manipula o sucesso da requisição
            console.log(response);
        })
    }
}
</script>