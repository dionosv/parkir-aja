<template>
    <div class="pesan">
        <!-- <img src="/src/assets/whitetext.png" class="foto"> -->
        <h1>Hello</h1>
        <h3>Parking spot booking never been easier than this</h3>
        <div class="extra-content">
            <widget></widget>
        </div>
        <!-- <div class="imageslogo">
            <img src="@/assets/whitetext.png" alt="">
        </div> -->

        <button @click="redirect" class="btn btn-primary">Book now</button>
    </div>
    
</template>

<script>
import router from "../router"
import widget from './home_widget.vue';

export default {
    components : {widget},
    methods: {
        redirect(){
            router.push({name : 'decide'})
    }}
}
</script>

<style scoped>
img{
    width: 35%;
    height: auto;
}

.pesan h1{
    margin-top: 2%;
    margin-bottom: 2%;
    font-size: 80px;
    font-family: 'Inter-ExtraBold';
}

.extra-content{
    margin-top: 40px;
    margin-bottom: 40px;
}


.pesan h3{
    /* margin-top: 3%;
    margin-bottom: 3%; */
    font-family: 'Inter-Medium';
}

.pesan button{
    font-family: 'Inter-SemiBold';
}

.pesan{
    -webkit-user-select: none; /* Safari */
    -ms-user-select: none; /* IE 10 and IE 11 */
    user-select: none; /* Standard syntax */
 
}

.imageslogo img{
    width: 200px;
    height: auto;
}

@media (max-width: 777px) {

.pesan h1{
    margin-top: 25%;
}


.pesan button{
    font-family: 'Inter-SemiBold';
    margin-bottom: 35%;
}

}


</style>