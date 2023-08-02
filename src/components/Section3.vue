<script setup>
import photos from '../data/photos.json'

const prop = defineProps({
        theme: Object,
        data: Object,
          })


</script>

<template>

    <span
    id="productos"
    ></span>

  <div 
  class="sect3-container">

    <div
    class="left"
    v-for="photo of photos.slice(0,1)">
        <div>
            <h1>{{ photo.name }}</h1>
            <p>{{ photo.text }}</p>
        </div>

        <img :src="photo.url" alt="Photo">
    </div>
    
    <div
        class="right"
        v-for="photo of photos.slice(1, 2)">
        <img :src="photo.url" alt="Photo">
        
        <div>
            <h1>{{ photo.name }}</h1>
            <p>{{ photo.text }}</p>
        </div>
    </div>

    <div
    class="left"
    v-for="photo of photos.slice(2,3)">
        <div>
            <h1>{{ photo.name }}</h1>
            <p>{{ photo.text }}</p>
        </div>

        <img :src="photo.url" alt="Photo">
    </div>

    <div
        class="right"
        v-for="photo of photos.slice(3, 4)">
        <img :src="photo.url" alt="Photo">
        
        <div>
            <h1>{{ photo.name }}</h1>
            <p>{{ photo.text }}</p>
        </div>
    </div>

    
  </div>

 
</template>

<style lang='scss' scoped>

span {
    padding-top: 120px;
    margin-top: -120px;
  }

.sect3-container {
    padding: 100px 10px;
    width: calc(100% - 20px);
    height: auto;
    background-color: v-bind('prop.theme.second');
    display: flex;
    justify-content: flex-start;
    flex-direction: column;
    align-items: center;
    gap: 30px;

    @media (max-width: 764px) {
        padding: 50px 5px;
        width: calc(100% - 10px);
    }

    .left, .right {
        display: flex;
        flex-direction: row;
        justify-content: space-evenly;
        align-items: center;
        gap: 0 20px;
        width: calc(100% - 100px);
        padding: 0 50px;
        height: 30vh;

        @media (max-width: 1100px) {
            height: auto;
        }

        @media (max-width: 764px) {
            padding: 0 10px;
            width: calc(100% - 20px);
            height: auto;
        }

        div {
            width: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;

            @media (max-width: 764px) {
                width: 100%;
            }        


            h1 {
            text-align: center;
            color: white;
            font-size: 40px;
            margin: 0;

            @media (max-width: 764px) {
                font-size: 30px;
            }

        }
            p {
                text-align: center;
                color: white;
                font-size: 24px;
                width: 80%;

                @media (max-width: 764px) {
                font-size: 20px;
                width: 100%;
                margin: 5px;
            }
                }
            }

        img {
            width: 45%;
            height: 100%;
            object-fit: cover;
            border-radius: 15px;
            box-shadow: 0px 0px 5px 5px rgba(255, 192, 203, 0.527);
            transition: 500ms ease all;
            &:hover {
                transform: scale(1.05);
                filter: brightness(110%)
            }
        }

    }

  }


</style>
