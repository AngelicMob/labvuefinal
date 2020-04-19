<template>
<div class="form">
        <h3>Create a new Snippet</h3>
        <form id="form1"> 
            <input v-model="title" type="text" id="title" placeholder="Title">
            <textarea v-model="content" name="content" id="content" cols="30" rows="20" placeholder="Content no less than 15 characters"></textarea>
               
        </form>
         <div class="controls">
                    <button class="btn btn1" @click="add">Upload</button>
                    <button class="btn btn2">Cancel</button>          
                </div>
    </div>
  
</template>
​
<script>
​
import axios from 'axios';
const url = 'https://www.forverkliga.se/JavaScript/api/api-snippets.php?';


export default {
    name: 'createsnippet',
     data(){
        return {
            title: '',
            content: ''
        }
    },
    methods:{
        add(){
           
    
            console.log('add called with id:  ' + this.title + '  and content: ' + this.content)
            axios.post(url, { add:'', title: this.title, content: this.content})
            .then(res => console.log(res.data.message))
            .catch(err => console.log('does not work' + err))
            this.title = ''
            this.content = ''
              
        }
​
​   }

}
​
</script>
​

<style scoped>

@import url('https://fonts.googleapis.com/css2?family=Quicksand:wght@300&display=swap');

h3{
    color: antiquewhite;
    padding-bottom: 20px;
    font-family: 'Quicksand', sans-serif;
}
.form{
    padding: 20px;  
}
input {
    width: 500px;
    padding: 12px 20px;
    margin: 8px 0;
    
    background-color: grey;
    border: white 1px solid;
    color: antiquewhite;
}
textarea{  
    background-color: rgba(0, 0, 0, 0.5);
    border: white 1px solid;
    color: antiquewhite;
    padding: 12px 20px;
    width: 500px;
    
}
::placeholder{
    color: antiquewhite;
}
.controls{
    float: right;
    padding-top: 10px;   
}
.btn {
    background-color: #00877C; 
    border: none;
    color: white;
    padding: 7px 32px;
    text-align: center;
    text-decoration: none;
    font-size: 16px;
    margin: 7px 7px;
    transition-duration: 0.4s;
    cursor: pointer;
    
}
.btn1 {
        background-color: black ;
        color: #00877C; 
        border: 1px solid #00877C;
    }
    .btn1:hover {
        background-color: #00877C;
        color: white; 
    }
    .btn2 {
        background-color: black; 
        color: red; 
        border: 1px solid red;
    }
    .btn2:hover {
        background-color: red;
        color: white;
    }
::-webkit-scrollbar {
  width: 5px;
}
/* Track */
::-webkit-scrollbar-track {
  background: rgb(102, 102, 102); 
}
 
/* Handle */
::-webkit-scrollbar-thumb {
  /* background: #888;  */
  background: antiquewhite;
}

</style>
