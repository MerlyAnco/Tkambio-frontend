<template>
    <main>
        <h1 class="title">Generador de reportes TK</h1>
        <Table/>
        <Button @click="open"/>
    </main>
</template>

<script>
import Table from "@/components/Report-Table.vue"
import Button from "@/components/Button.vue"

export default{
    components: {
        Table,
        Button
    },
    setup(props, { emit }) {
        const open = () => {
            emit("open")
        }

        return { open }
    }
}

</script>

<style scoped>

main{
    display: flex;
    flex-direction: column;
    align-items: center;
    padding-top:38px;
    min-height: auto;
}
.title{
    font-style: normal;
    font-weight: 400;
    font-size: 28px;
    line-height: 33px;
    text-align: center;
    color: var(--black);
}
</style>