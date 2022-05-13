<template>
    <NavBar/>
    <Report @open="toggleModal" />
    <Modal @close="toggleModal" :modalActive="modalActive"/>
</template>

<script>
import NavBar from "@/components/NavBar.vue"
import Report from "@/components/Report.vue"
import Modal from "@/components/Modal.vue"
import { ref } from "vue"
export default{
    components: {
        NavBar,
        Report,
        Modal,
    },
    setup() {
        const modalActive = ref(false)
    
        const toggleModal = () => {
            modalActive.value = !modalActive.value;
        }

        return { modalActive, toggleModal}
    },
}

</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Argentum Sans'
}

* {
    --black: #181818;
    --blue: #4563E6;
    --gray: #CFCFCF;
    --light-black:#565656;
    --ligth-gray:#696969;
    --yellow:#FFBE12;
    --white: #FFFFFF;
    --line-gray:#C4C4C4;
}

html,
body,
.app {
  min-height: 100vh;
  margin: 0;
}

</style>
