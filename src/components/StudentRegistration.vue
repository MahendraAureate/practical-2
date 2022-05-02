<template>
    <div class="container">
        <div class="row"> 
            <template v-if="studentsGetData">
                <studentCard class="student__parent" v-for="student in studentsGetData" :key="student.id" :student="student" @studentRemoveId="studentRemoveId"/>
            </template>
            <template v-else>
                <div class="not__available">
                    Data not available
                </div>
            </template>
        </div>
    </div>
</template>

<script>
// const jsonServer = require('json-server')


import studentCard from './studentCard.vue'
// import studentData from '../data/studentData.json'
// http://localhost:3000/studente


export default {
    name: 'StudentRegi',
    components:{
        studentCard
    },
    data() {
        return {
            studentsGetData: []
            // studentsGetData: studentData,
        }
    },
    methods: {
        studentRemoveId(studid){

            fetch(`http://localhost:3001/studente/${studid.id}`, 
            {
                method: 'DELETE', 
                headers: {
                    'Accept': 'application/json',
                    'Content-Type': 'application/json'
                }
            }).then(resp => {
                console.log('res ::=> ', resp.data);
                resp.data;
            }).catch(error => {
                console.log(error);
            });
                
           
            this.studentsGetData = this.studentsGetData.filter( item => {
                return item.id !== studid.id
            });            
            
        }
    },
    async created(){
        await fetch('http://localhost:3001/studente')
        .then(res => res.json())
        .then(data => { 
            console.log('data ::=> ', data);
            this.studentsGetData = data
        } )
        .catch(err => console.log(err.message))
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
    margin: 40px 0 0;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    display: inline-block;
    margin: 0 10px;
}

a {
    color: #42b983;
}
.not__available{
    font-weight: 600;
    text-align: center;
    width: 100%;
}


</style>
