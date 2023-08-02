<script setup>
import { ref } from 'vue'
 
const prop = defineProps({
        theme: Object,
        data: Object
          })

const name = ref('')        
const address = ref('')        
const tel = ref('')        
const message = ref('')     

const formArray = ref([])

const onSubmit = () => {

  if (name.value != '' && address.value != '' && tel.value != '' && message.value != '') {

    formArray.value.push({
      name: name.value,
      address: address.value,
      tel: tel.value,
      message: message.value,
    });
  
    name.value = '';
    address.value = '';
    tel.value = '';
    message.value = '';

  }

}


</script>

<template>

<span
  id="contacto"></span>


  <div 
  id="form"
  class="sect4-container">

        <form 
        @submit.prevent='onSubmit'
        action="">

          <div>
            <label for="">Nombre: </label>
            <input 
            v-model="name"            
            type="text">
          </div>
          
          <div>
            <label for="">Dirección: </label>
            <input 
            v-model="address"            
            type="text">
          </div>

          <div>
            <label for="">Teléfono: </label>
            <input 
            v-model="tel"
            type="text">
          </div>
          
          <div>
            <textarea
            v-model="message"
            name="" id="" cols="30" rows="10"></textarea>
          </div>

          <button>Enviar</button>

        </form>

        <div
        class="info-map"
        >

          <div
          class="info"
          >
          <p><span>Dirección:</span> 
            <br>
            {{ data.address }}
            <br>
            ({{ data.address2 }})          
          </p>         
          <p><span>Correo:</span>
          <br>
            {{ data.email }}
          </p>
          
          <p><span>Teléfono:</span> 
            <br>
            {{ data.tel1 }}</p>
          <p><span>Teléfono:</span> 
            <br>
            {{ data.tel2 }}</p>
        </div>

          <iframe frameborder="0" scrolling="no" marginheight="0" marginwidth="0" id="gmap_canvas" src="https://maps.google.com/maps?width=520&amp;height=400&amp;hl=en&amp;q=Av.%20Rivadavia%2012541%20Haedo+(Negocio)&amp;t=&amp;z=15&amp;ie=UTF8&amp;iwloc=B&amp;output=embed"></iframe>
          
        </div>

    
  </div>

 
</template>

<style lang='scss' scoped>

span {
    padding-top: 120px;
    margin-top: -120px;
  }

.sect4-container {
    padding: 30px 10px;
    width: calc(100% - 20px);
    min-height: calc(60vh - 60px);
    height: auto;
    background-color: v-bind('prop.theme.second');
    display: flex;
    justify-content: flex-start;
    flex-direction: column;
    align-items: center;
    gap: 100px;


    .info-map {
      height: calc(auto - 100px);
      display: flex;
      flex-direction: row;
      gap: 50px;
      align-items: flex-start;
      justify-content: space-between;
      width: calc(70% - 100px);
      background-color: v-bind('prop.theme.third');
      padding: 50px;
      border-radius: 20px;     
      box-shadow: 0px 0px 10px 5px rgba(255, 48, 255, 0.753);

      @media (max-width: 1100px) {
      flex-direction: column;
      justify-content: center;
      align-items: center;

      @media (max-width: 764px) {
        height: 45h;
        padding: 10px;
        width: calc(100% - 20px);
      }

    }
 

      span {
        font-weight: bold;
      }

      p {
        color: white;
        font-size: 22px;
      }

      iframe {
        height: 40vh;
        width: 40vw;
        border-radius: 20px;

        @media (max-width: 764px) {
        height: 40vh;
        width: calc(90%);
      }

      }
    }

    form {
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      background-color: v-bind('prop.theme.first');
      width: calc(70% - 100px);
      height: calc(45vh - 40px);
      border-radius: 20px;
      box-shadow: 0px 0px 10px 5px rgba(255, 48, 255, 0.753);
      gap: 10px 0;
      padding: 20px 50px;

      @media (max-width: 1100px) {
        height: auto;
      }

      @media (max-width: 764px) {
        width: calc(100% - 100px);
      }

      button {
        border: none;
        background-color: v-bind('prop.theme.fourth');
        color: white;
        padding: 10px 50px;
        border-radius: 15px;
        transition: 300ms ease all;

        &:hover {
          cursor: pointer;
          filter: contrast(50%);
        }

      }

      div {
        width: 100%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;

        textarea {
          resize: none;
          width: 100%;
          height: 100px;
          background-color: inherit;
          border: 2px solid violet;

          &:focus {
            outline: none;
            border: 2px solid rgb(182, 0, 182);

          }
        }

        label {
          width: 100%;
          font-weight: 700;
        }

        input {
          width: 100%;
          background-color: inherit;
          border: none;
          border-bottom: 2px solid violet;

          &:focus {
            outline: none;
            border-bottom: 2px solid rgb(182, 0, 182);
          }
        }
      }
    }

    h1 {
      color: white;
      font-size: 100px;
    }
  }


</style>
