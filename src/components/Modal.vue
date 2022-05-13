<template>
    <transition name='modal-animation'>
    <div v-show='modalActive' class='modal-background'  @click="close">
        <div class='modal-content' @click.stop>
            <h2>Reporte por fecha de nacimiento</h2>
            <p>Ingrese los siguientes datos para generar tu reporte</p>
            <Form :close="close"/>
        </div>
    </div>
    </transition>
</template>

<script>
import Form from "@/components/Form.vue"
export default {
    components: {
        Form
    },
    props: ["modalActive"],
    setup(props, {emit}) {
        const close = () => {
            emit("close")
        }

        return { close }
    }
}
</script>

<style scoped>
.modal-background{
    display: flex;
    position: fixed;
    justify-content: center;
    align-items: center;
    height: 100vh;
    width: 100vw;
    top:0;
    left:0;
    background: #0000008f;
}

.modal-content{
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 30px 35px 40px;
    position: static;
    width: 526px;
    height: 417px;
    background: var(--white);
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    border-radius: 10px;
}

h2{
    font-weight: 800;
    font-size: 24px;
    line-height: 28px;
    color:var(--black);
    margin-bottom: 18px
}

p{ 
    font-weight: 300;
    font-size: 16px;
    line-height: 16px;
    margin-bottom: 20px;
    color:var(--light-black);
}
</style>