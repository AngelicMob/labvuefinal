<template>
  
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
            axios.post(url,{downvote:'', id:id })
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
            axios.post(url, {delete:'',id:id})
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
           window.relo
        },
        unreport(id){
            console.log('unreport called with id:  ' + id )
            axios.post(url, {unreport:'',id:id})
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
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>

