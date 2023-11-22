<template>
   <div class="row">
        <div id="box">
          <div class="isi">
          <h1>Mall A</h1>
          <p>{{slot_a}}</p>
          <span class="badge text-bg-success rounded-pill">Available</span> 
        </div>
        </div>
        <div id="box">
          <div class="isi">
          <h1>Mall B</h1>
          <p>{{slot_b}}</p>
          <span class="badge text-bg-success rounded-pill">Available</span> 
        </div>
        </div>
    </div> 

    <!-- 495057 -->
    
</template>

<script>
import {db} from './func/firedata'
import { getDocs, query, collection, where,onSnapshot} from "firebase/firestore";
 
export default { 

    data() {
        return {
            slot_a : 100,
            pending_a : 0,
            occ_a : 0,
            money_a : 0,
            slot_b : 100,
            pending_b : 0,
            occ_b : 0,
            money_b : 0,
            state :false
        }
    },

    mounted() { 
        this.starter()
    },
    methods: {
        async start_data1() {
            const userdataRef = collection(db, "location");
            const q = query(userdataRef, where("nama", "==", "Mall A"));

            onSnapshot(q, (snapshot) => {
                snapshot.forEach((doc) => {
                this.slot_a = doc.data().slot;
                this.pending_a = doc.data().pending;
                this.occ_a = doc.data().occupied;
                this.money_a = doc.data().money;
                });
            });
        },


        async start_data2() {
            const userdataRef = collection(db, "location");
            const q = query(userdataRef, where("nama", "==", "Mall B"));
            
            onSnapshot(q, (snapshot) => {
                snapshot.forEach((doc) => {
                this.slot_b = doc.data().slot;
                this.pending_b = doc.data().pending;
                this.occ_b = doc.data().occupied;
                this.money_b = doc.data().money;
                });
            });
        },

        async starter(){
            await this.start_data1()
            await this.start_data2()
        }
    },

}
</script>

<style>
.row {
	--bs-gutter-x: 1.5rem;
	--bs-gutter-y: 0;
	display: flex;
	flex-wrap: wrap; 
  justify-content : center;
  /* flex-direction: column; */
	/* margin-top: calc(-1 * var(--bs-gutter-y));
	margin-right: calc(-.5 * var(--bs-gutter-x));
	margin-left: calc(-.5 * var(--bs-gutter-x));  */
}

.row h1{
    font-family: 'Inter-ExtraBold';
}

.row p{
    font-family: 'Inter-Medium';    
}

#box{
  background-color: #212529;
  border-radius: 15px; 
  width: 200px; /* Lebar kotak */
  height: 200px; /* Tinggi kotak */ 
  padding: 10px;
  margin: 10px; 
  display: flex;
  align-items: center; /* Menengahkan vertikal */
  justify-content: center; /* Menengahkan horizontal */


}

 

@media (max-width: 777px) {

  #box{
    width: 200px;
    margin: 5px;
    height: 185px;
  }

  .row{  
    display: flex;
    flex-direction: row;
  }

}

</style> 