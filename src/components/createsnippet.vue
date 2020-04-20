<template>
<div class="form">

        <h1>Welcome!</h1>
        <h3>Create a new Snippet</h3>
        <img src="@/assets/code.svg" alt="code-icon">

        <!-- create snippet inputform -->
        <form id="input-form">
            <input type="text" id="title" v-model="title" placeholder="Title">
            <textarea name="content" id="content" cols="35" rows="20" v-model="snippetcode" placeholder="Post your snippet code here..."></textarea>

        </form>

         <div class="controls">
            <button class="btn btn1" @click="add">Upload</button>
            <button class="btn btn2">Cancel</button>
        </div>

</div>

</template>

<script>
import axios from 'axios';
const url = 'https://www.forverkliga.se/JavaScript/api/api-snippets.php?';

    export default {
        name: "createsnippet",
        data(){
            return {
                title: '',
                snippetcode: ''
            }
        },
            methods: {
                add(){
                    axios.post(url, { add:'', title: this.title, content: this.snippetcode})
                    .then(res => console.log(res.data.message))
                    .catch(err => console.log('does not work' + err))
                    this.title = '';
                    this.snippetcode = '';
                }
           }
        }
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css?family=Quicksand&display=swap%22");

* {

    font-family: 'Quicksand', sans-serif;
}

.form{
    padding: 35px;

}

img {

    width: 30px;
    background-position: center;

}

h1 {
     color: white;
     text-align: center;
     font-weight: bold;
     padding-bottom: 16px;

}

h3{
    color: white;
    padding-bottom: 20px;
    text-align: center;

}

input {
    width: 880px;
    padding: 12px 20px;
    margin: 8px 0;
    background-color: grey;
    border: white 1px solid;
    border-radius: 1px;
    color: white;
    opacity: 0.7;

}

input[type=submit]{

     color: #00877C;
}
textarea{
    background-color: rgba(0, 0, 0, 0.5);
    border: white 1px solid;
    border-radius: 6px;
    color: antiquewhite;
    padding: 12px 20px;
    width: 880px;
    display: block;
    font-family: 'Quicksand', sans-serif;

}
::placeholder{
    color: white;
}
.controls{
    float: right;
    padding-top: 10px;

}
.btn {
    background-color: #2EA19C;
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
        background-color:white;
        font-weight: bold;
        color: #00877C;
        border: 1px solid #00877C;
        border-radius: 6px;
    }
    .btn1:hover {
        background-color: #00877C;
        color: white;
        opacity: 0.8;
    }
    .btn2 {
        background-color: rgb(7, 5, 5);
        color: rgb(255, 1, 1);
        border: 1px solid rgb(255, 1, 1);
        border-radius: 6px;
        font-weight: bold;
    }
    .btn2:hover {
        background-color:rgb(255, 1, 1);
        color: white;
        opacity: 0.7;
    }
::-webkit-scrollbar {
  width: 5px;
}

::-webkit-scrollbar-track {
  background: rgb(102, 102, 102);
}


::-webkit-scrollbar-thumb {

  background: antiquewhite;
}

</style>
