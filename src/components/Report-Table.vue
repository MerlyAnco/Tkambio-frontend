<template>
    <div class="table-container">
        <div class="table-row header">
            <div class="cell">
                    Título
            </div>
            <div class="cell">
                    Fecha de creación
            </div>
            <div class="cell">
                    Acción
            </div>
        </div>
        <div class="table-row content" v-for="report in reportList">
            <div class="cell title">
                    {{ report.title }}
            </div>
            <div class="cell date">
                    {{ report.create_at }}
            </div>
            <div class="cell action">
                <button type="button" class="download-btn" @click="downloadFile()">
                        <p>Descargar</p>
                        <img class="icon" src="@/assets/download.svg"/>
                </button>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    data(){
        return{
            reportList:[]
        }
    },
    setup() {
        const reportList = JSON.parse(localStorage.getItem("Registers"))
        return { reportList }
    },
    methods:{
        downloadFile(){
            alert('Este es un modelo de prueba')
        }
    }
}
    
</script>

<style scoped>

.table-container {
    margin-top:50px;
    width: 690px;
    align-items: center;
    padding: 0px 30px 30px;
    background-color: var(--blue);
    border-radius: 10px;
    color: var(--white)
}

.table-row{
    display:grid;
    grid-template-columns: 1fr 1fr 1fr;
    padding: 15px 0;
    text-align: center;
}

.cell:first-child{
    text-align: left;
}

.cell:last-child{
    text-align: right;
}

.header{
    padding-bottom: 10px;
    border-bottom: 4px solid var(--line-gray);
}

.content{
    border-top:1px solid var(--line-gray);
}

.content .title,
.content .date {
    border-right: 4px solid var(--line-gray);
}

.action{
    display: flex;
    justify-content: flex-end;
    align-items: center;
}
.download-btn{
    display:flex;
    border:none;
    background: none;
    color: var(--white);
    width: auto;
    cursor:pointer
}

.download-btn p{
    font-weight: 600;
    margin: 0;
    color: var(--white);
    font-size:16px;
}
.date{
    font-weight: 400;
    font-size: 16px;
    line-height: 24px;
}

.title{
    font-weight: 400;
    font-size: 12px;
    line-height: 14px;
}
.icon{
    height: 20px;
    width: 20px;
    margin-left: 5px;
}
</style>