<template>
    <div>
        <span class="student__remove" @click="removeStudent(student)">X</span>
        <div class="student__inner">
            <div class="student__image">
                <img :src="student.avatar" alt="">
            </div>
            <div class="student__name student-detail">
                <div>Name</div>
                <div>{{student.fname}} {{student.lname}}</div>
            </div>
            <div class="student__age student-detail">
                <div>Age</div>
                <div>{{student.age}}</div>
            </div>
            <div class="studet_email student-detail">
                <div>Email</div>
                <div>{{student.email}}</div>
            </div>
            <div class="student__phone student-detail">
                <div>Phone</div>
                <div>{{student.phone}}</div>
            </div>
        </div> 
        
    </div>
</template>

<script>
import studentData from '../data/StudentData.json'


export default {
    name:'StudentCard',
    props:['student'],
    data() {
        return {
            studentData:studentData
        }
    },
    methods: {
        removeStudent(studid){
            this.$emit('studentRemoveId', studid);

            // state.cart = state.cart.filter( item => {
            //     return item.product.id !== product.id
            // });

            // console.log('student ::=> ', studid);
            // this.studentData.splice(student, 1);
            // console.log('this.studentData ::=> ', this.studentData);
        }
    },

}
</script>

<style  scoped>
.student__remove {
    cursor: pointer;
    position: absolute;
    z-index: 1;
    transition: 0.3s ease;
    color: #212121;
    background-color: #fff;
    top: 0;
    right: 15px;
    padding: 10px 13px 13px 20px;
    border-radius: 0% 0% 0% 31px;
}
.student__remove:hover{
    color: red;
}
.student__image{
    height: 200px;
    margin-bottom: 15px;
    overflow: hidden;
    border-radius: 10px;

}
.student__image:hover img{
    transform: scale(1.05);
}
.student__inner{
    position: relative;
    margin-bottom: 25px;
    background-color: #fff;
    padding: 15px;
    border-radius: 15px;
    box-shadow: 0px 0px 10px -5px rgb(0 0 0 / 50%);
}
.student__inner img{
   width: 100%;
    height: 100%;
    -o-object-fit: cover;
    object-fit: cover;
    border-radius: 10px;
    transition: 0.2s ease;
    cursor: pointer;
}

.down-content {
    /* opacity: 0;
    visibility: hidden;
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    text-align: center;
    background-color: rgb(66 185 131 / 90%);
    color: #212121;
    height: 100%;
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    transition: 0.5s;
    padding: 0 10px; */
    
}
/* .selected{
    opacity: 1;
    visibility: visible;
} */


.student-detail{
    display: flex;
    justify-content: space-between;
}
.student-detail:not(:last-child){
    margin-bottom: 8px;
}
</style>