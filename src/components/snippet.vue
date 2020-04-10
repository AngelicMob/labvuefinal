<template>
<div>
       
            <ul>
                <li><a href="#" @click="getLatest">Latest</a></li> |
                <li><a href="#" @click="getMostUpvoted">Most Upvoted</a></li> |
                <li><a href="#" @click="getReported">Get Reported</a></li>
            </ul> 
            <div class="loader" v-if="snippets.length === 0"> Loading...</div>
            <div class="container" v-for="snippet in snippets" v-bind:key="snippet.id" >      
                <h2>{{snippet.title}}</h2>
                <div class="content">
              
                        <pre>
                            <code>
                                <p>{{snippet.content}}</p>
                            </code>
                        </pre>
            
                    
                </div>
                
                <button class="btn btn1" @click="voteUp(snippet.id)">Vote Up</button>
                <button class="btn btn2" @click="voteDown(snippet.id)">Vote Down</button>
                <button v-if="snippet.is_reported === 0" class="btn btn2 btnR" @click="report(snippet.id)">Report</button>
                <button v-else class="btn btn2 btnR" @click="unreport(snippet.id)">Unreport </button>          
                <button class="btn btn2 btnR" @click="del(snippet.id)">Delete</button>
                
                <div class="rating">
                        <p id="Score">Score : {{snippet.score}}</p>
                        <p id="id">ID: {{snippet.id}}</p>
                </div>        
    </div>


  
</template>
​
<script>
​
import axios from 'axios'
const url = 'https://www.forverkliga.se/JavaScript/api/api-snippets.php?';

export default {
    
    name: 'snippet',
    data(){
        return {
            snippets: []
        }
    },
    methods: {
        getLatest(){
            this.snippets = [];
            axios.get('https://www.forverkliga.se/JavaScript/api/api-snippets.php?latest')
            .then(res => this.snippets = res.data)
            .catch(err => console.log(err))
           
        },
        getMostUpvoted(){
           this.snippets = [];
            axios.get('https://www.forverkliga.se/JavaScript/api/api-snippets.php?best')
            .then(res => this.snippets = res.data)
            .catch(err => console.log(err))
            //console.log(this.snippets)
        },
        getReported(){
            this.snippets = [];
             axios.get('https://www.forverkliga.se/JavaScript/api/api-snippets.php?reported')
            .then(res => this.snippets = res.data)
            .catch(err => console.log(err))
           //console.log(this.snippets)
        },
        voteUp(id){ 
            console.log('vote up called with id:' + id)
            this.snippets = []
            axios.post(url, { upvote:'', id:id})
            .then(res => {console.log(res.data.message)
                if(res !== null){
                    this.getLatest();
                } 
            })
            .catch(err => console.log(err))
          
        },
        voteDown(id){
            console.log('vote down called with id:  ' + id)
            this.snippets = []
            axios.post(url,{downvote:'', id: id })
            .then(res => {console.log(res.data.message)
                if(res !== null){
                    this.getLatest();
                }
            })
            .catch(err => console.log(err))           
        },
        del(id){
            console.log('delete called with id:  ' + id )
            this.snippets = []
            axios.post(url, {delete:'',id: id})
            .then(res => {console.log(res.data.message)
            if(res !== null){
                this.getLatest();
            }
            })
            .catch(err => console.log(err))
            
        },
        report(id){
            console.log('report called with id:  ' + id )
            axios.post(url, {report: '',id: id})
            .then(res => {console.log(res.data.message)
            if(res !== null){
                this.getLatest();
            }
            })
            .catch(err => console.log(err))
           window.relo
        },
        unreport(id){
            console.log('unreport called with id:  ' + id )
            axios.post(url, {unreport: '',id: id})
            .then(res => {console.log(res.data.message)
            if(res !== null){
                this.getLatest();
            }
            })
            .catch(err => console.log(err))
            
        }  
    },
    created(){
            axios.get('https://www.forverkliga.se/JavaScript/api/api-snippets.php?latest')
            .then(res => this.snippets = res.data)
            .catch(err => console.log(err))
            console.log(this.snippets)
    }   
}
</script>
​

<style scoped>
.rating{
        display: flex;
    }
    #Score{
        color: #00877C;
    }
    #id{
        color: #00877C;
        
    }
    ul{
        list-style-type: none;
        float: right;
        padding:0px 10px 30px 5px;
        color:#00877C;
    }
    li{
        display: inline;
    }
    a{
        color: #00877C;
        text-decoration: none;
    }
    a:hover{
        text-decoration: underline;
    }
    h2{
        float: left;
        padding: 10px;
        color: #00877C;
    }
    .container{
        width: 900px;
        min-height:200px;
        height: auto;
        margin: 50px auto 150px auto;
    }
    .content{
        background-color: #2a3439;
        min-height:200px;
        height: 300px;
        width: 870px;
        margin: 50px auto 10px 10px;
        overflow: auto; 
        border: 1px solid #00877C;
        color: rgb(192, 192, 192);
        
    }
    .btn {
        background-color: #0F6775; 
        border: none;
        color: white;
        padding: 7px 32px;
        text-align: center;
        text-decoration: none;
        font-size: 16px;
        margin: 7px 7px;
        transition-duration: 0.4s;
        cursor: pointer;
        float: left;
    }
    .btn1 {
        background-color: #151a1c ;
        color: #00877C; 
        border: 1px solid #00877C;
    }
    .btn1:hover {
        background-color:#00877C;
        color: white; 
    }
    .btn2 {
        background-color: #151a1c; 
        color: #D34040; 
        border: 1px solid #D34040;
    }
    .btn2:hover {
        background-color:#D34040;
        color: white;
    }
    .btnR{
        float: right;
        margin-right:18px;
    }
    p{
        padding: 15px;
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
  
  background: #00877C;
}


</style>

