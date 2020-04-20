<template>
<div>

            <ul>
                <li><a href="#" @click="getLatest">Latest</a></li> |
                <li><a href="#" @click="getMostUpvoted">Most Upvoted</a></li> |
                <li><a href="#" @click="getReported">Reported</a></li>
            </ul>

            <div class="container" v-for="snippet in snippets" v-bind:key="snippet.id" >


                <h2>{{snippet.title}}</h2>
                <div class="content">

                        <pre>
                            <code>
                                <p>{{snippet.content}}</p>
                            </code>
                        </pre>


                </div>


            <div class="score-rating">
                <p id="score-point">Score: {{snippet.score}}</p>
            </div>
                <button class="btn vote" @click="voteUp(snippet.id)">Vote Up +</button>
                <button class="btn btn2" @click="voteDown(snippet.id)">Vote Down -</button>
                <button class="btn btn1" @click="del(snippet.id)">Delete x</button>s
                <button v-if="snippet.is_reported === 0" class="btn btn1 report" @click="report(snippet.id)">! Report</button>
                <button v-else class="btn btn1 report" @click="unreport(snippet.id)">Unreport </button>

    </div>

</div>

</template>
<script>

import axios from 'axios';
const url = 'https://www.forverkliga.se/JavaScript/api/api-snippets.php?';
export default {

    name: 'Snippet',
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

        },
        getReported(){
            this.snippets = [];
             axios.get('https://www.forverkliga.se/JavaScript/api/api-snippets.php?reported')
            .then(res => this.snippets = res.data)
            .catch(err => console.log(err))

        },
        voteUp(id){
            console.log('vote up called with id:' + id)
            this.snippets = []
            axios.post(url, { upvote:'', id: id})
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
            axios.post(url, {report:'',id:id})
            .then(res => {console.log(res.data.message)
            if(res !== null){
                this.getLatest();
            }
            })
            .catch(err => console.log(err))

        },
        unreport(id){
            console.log('unreport called with id:  ' + id )
            axios.post(url, {unreport:'', id:id})
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


<style scoped>
@import url("https://fonts.googleapis.com/css?family=Quicksand&display=swap%22");
* {

    font-family: 'Quicksand', sans-serif;
}


.score-rating{
        display: flex;
        font-family: 'Quicksand', sans-serif;

    }
    #score-point{
        color: rgb(85, 219, 201);
    }
    #id{
        color: white;

    }
    ul{
        list-style-type: none;
        text-align: center;
        padding: 47px 3px 28px 58px;
        color: transparent;

    }


    li{
        display: inline;
    }
    a{
        color: antiquewhite;
        text-decoration: underline;
        letter-spacing: 2px;
    }
    a:hover{
        text-decoration: none;
        color:rgb(33, 180, 160);
    }

    h2{
        float: left;
        padding: 10px;
        color: antiquewhite;
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
        width: 880px;
        margin: 50px auto 10px 8px;
        overflow: auto;
        border: 1px solid #519996;
        color: rgb(192, 192, 192);
        opacity: 0.8;

    }

    .btn {
        background-color: #519996;
        border: none;
        color: white;
        padding: 7px 30px;
        text-align: center;
        text-decoration: none;
        font-size: 16px;
        margin: 7px 7px;
        transition-duration: 0.4s;
        cursor: pointer;
        float: left;
    }
    .vote {
        background-color: #5fcf50;
        color: white;
        font-weight: bold;
    }
    .vote:hover {
        background-color: white ;
        color: #27a816;
        border: 0.5px solid #5fcf50;
        font-weight: bold;

    }
    .btn1 {

        background-color: black;
        color: rgb(204, 60, 60);
        border: 0.5px solid rgb(204, 60, 60);
        font-weight: bold;



    }
    .btn1:hover {

        background-color: red;
        color: white;

    }

    .btn2 {
        background-color: rgb(204, 61, 61);
        color: white;
        font-weight: bold;


    }
    .btn2:hover {

        background-color: white ;
        color: #27a816;
        border: 0.5px solid #5fcf50;
        font-weight: bold;
    }

    .report{
        float: right;
        margin-right: 9px;
    }
    p{
        padding: 15px;
    }
::-webkit-scrollbar {
  width: 5px;
}

::-webkit-scrollbar-track {
  background: rgb(102, 102, 102);
}

::-webkit-scrollbar-thumb {
  /* background: #888;  */
  background: #519996;
}


</style>
