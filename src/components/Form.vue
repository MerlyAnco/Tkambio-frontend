<template>
    <form @submit.prevent="addRegister" class="form-content">
         <div class="form-group">
            <label for="description">Descripcion del reporte</label>
            <input type="text" id="description" v-model="description">
        </div>
        <p>Fecha de nacimiento</p>
        <div class="birth-date">
            <div class="form-group">
                <label for="start">Inicio</label>
                <input type="date" id="start" v-model="startDate">
            </div>
            <div class="form-group">
                <label for="end">Fin</label>
                <input type="date" id="end" v-model="endDate">
            </div>
        </div>
        <div class="content-btn">
            <input type="submit" class="download-btn" value="Generar Reporte"/>        
        </div>
    </form>
</template>

<script>
export default {
    data() {
        return{
            title: "",
            start:"",
            end:"",
            create_at: "",
            registerList:[]
        }
    },
    props:{
        close:{
            type:Function
        },
    },
  mounted() {
    if (localStorage.getItem('Registers')) {
      try {
        this.registerList = JSON.parse(localStorage.getItem('Registers'));
      } catch(e) {
        localStorage.removeItem('Registers');
      }
    }
  },
    methods: {
        getDate(){
            let date = new Date();
            const months = ["01", "02", "03", "04", "05", "06", "07", "08", "09", "10", "11", "12"];
            const dateExact = `${date.getDate()}/${months[date.getMonth()]}/${date.getFullYear()}`

            return dateExact
        },



        addRegister(){
            var data = {
                title: this.description,
                start:this.startDate,
                end:this.endDate,
                create_at: this.getDate(),
            }
        
            this.registerList.push(data);
            this.updateStorage()
            this.description="";
            this.startDate="";
            this.endDate="";
            this.createDate="";
            location.reload()
        },
        updateStorage(){
            localStorage.setItem("Registers", JSON.stringify(this.registerList))
        },
        
    },
}
</script>

<style scoped>
.form-content{
    width: 100%;
}
.form-group{
    position: relative;
    display: flex;
    margin:14.5px 0px;
}

p{
    font-weight: 300;
    font-size: 12px;
    line-height: 16px;
    letter-spacing: 0.2px;
    color: var(--ligth-gray);
}

label{
    position: absolute;
    background-color: var(--white);
    font-weight: 300;
    font-size: 12px;
    color: var(--ligth-gray);
    top: -10px;
    left: 3%;
    padding: 0 5px;
    line-height: 16px;
    letter-spacing: 0.2px;
}

input{
    width: 100%;
    height: 54px;
    padding: 0 10px;
    border: 1px solid rgba(0, 0, 0, 0.12);
    border-radius: 6px;
}
.birth-date {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-column-gap: 15px;
}

.content-btn{
    display: flex;
    width: 100%;
    justify-content: center;
    margin-top: 27px;
}
.download-btn{
    padding: 16px 50px;
    background: var(--gray);
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    border-radius: 50px;
    border:none;
    width: 227px;
    height: 51px; 
    font-size:16px;  
    font-weight: 400;
    cursor:pointer;
    
}
</style>