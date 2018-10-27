<template>
    <div style="margin: auto; margin-top: 10vh;margin-right:15vh" >         
        <div >
            <h1>View All </h1>  
            <table class="table" style="margin: 10vh; margin-right :10vh;"  >
                <thead>
                    <tr>
                        <th>No.</th>
                        <th v-for="(res,index) in surveys" :key="index" >
                            Question<br>{{res.qid}}
                        </th>
                        
                    </tr>
                </thead>
                <tbody >
                    
                    <tr v-for="a in answers" :key="a.datetime"  >

                        <td>Tourist {{a.datetime}}</td>
                        <td  v-for="ans in a.answered" :key="ans.qid" >
                        
                            <p v-for="aa in ans.selectedChoice" :key="aa" >{{aa}}</p>
                            <p v-for="(qq,index) in ans.value" :key="index">{{qq}}</p>
                            
                            <p>{{ans.selectedA}}</p> 
                            <p>{{ans.selectedB}}</p>
                            <p >{{ans.selectedE}} </p> 
                            <p>{{ans.selectedS}}  </p>
                            
                            <p>{{ans.selected}}  </p>   
                            <p>{{ans.text}}</p>
                            <p>{{ans.selectedRadio}}  </p>
                            
                        </td >
                        
                    </tr> 
                </tbody>
            </table>
        </div>
    </div>   
</template>

<script>
import {firestore} from '../firebase.js'

export default {
    
    data (){
        return{
            surveys: [],
            answers: [] ,
            
        }
    },
    firestore (){
        return {
            surveys : firestore.collection('surveys').orderBy("qid"),
            //answers : firestore.collection('answers').doc('tourist1').collection('responses').doc('r1')
            answers : firestore.collection('answers')
        }
    }
}
</script>

<style scoped>
.marginTop {
  margin-top: 7vh; 
}
p{
    color: black;
}
.input{
    width: 70vw;
    height: 11vh;
}
.center{
    width: 37vw;
    height: 8.5vh;
     margin: auto;
    border: 3px ;
    padding: 10px;
}

.buttonCSS {
  background-color: green;
  border-radius: 40px;
  width: 12vw;
  height: 12vh;
  font-size: 3.5vh;

  margin-top: 30px;
  margin-right: 70px;
  margin-bottom: 50px;
  margin-left: 80px;
}
.buttonCSS2{
     background-color: red;
  border-radius: 40px;
  width: 12vw;
  height: 12vh;
  font-size: 3.5vh;

  margin-top: 30px;
  margin-right: 70px;
  margin-bottom: 50px;
  margin-left: 80px;
}

h1 {
  color: white;
  margin-right: 1000px;
  margin-bottom: 50px;
}
.img-body {
  height: 20vh;
}
</style>
