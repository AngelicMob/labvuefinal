<template>
<div class="form">
        <h3>Post new Snippet</h3>
        <form id="form1"> 
            <input v-model="title" type="text" id="title" placeholder="Title no less than 5 characters">
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
import axios from 'axios'
const url = 'https://www.forverkliga.se/JavaScript/api/api-snippets.php?';
export default {
    name:"newSnippet",
     data(){
        return {
            title: '',
            content: ''
        }
    },
    methods:{
        add(){
            if(this.title.length < 5 && this.content.length < 15){
                alert('Please follow the requirements')
                }else{
    
                    console.log('add called with id:  ' + this.title + '  and content: ' + this.content)
                    axios.post(url, { add:'', title: this.title, content: this.content})
                    .then(res => console.log(res.data.message))
                    .catch(err => console.log('Of course it dosent work' + err))
                    this.title = ''
                    this.content = ''
                }
            }
        }
    }
​
​
​
​
</script>
​
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
