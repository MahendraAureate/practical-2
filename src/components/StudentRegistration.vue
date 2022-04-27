<template>
<div class="container">
        <div class="row"> 
            <template v-if="students.length">
                <!-- {{student.length}} -->
                <studentCard class="student__parent" v-for="student in students" :key="student.id" :student="student" @studentRemoveId="studentRemoveId"/>
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

import studentCard from './studentCard.vue'
import studentData from '../data/StudentData.json'


export default {
    name: 'StudentRegi',
    components:{
        studentCard
    },
    data() {
        return {
            students: studentData,
            
        }
    },
    methods: {
        studentRemoveId(studid){
            // console.log('studid ::=> ', studid);
            // console.log('this.students ::=> ', this.students);
            
            // this.students.forEach((value) => {
            //     console.log('value ::=> ', value.id);
            //     if (value.id == studid ){
            //         console.log('Yes')
            //     }
            // });

            this.students = this.students.filter( item => {
                console.log('hey there ::=> ', item);
                return item.id !== studid.id
            });            

        }
    },
    
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
