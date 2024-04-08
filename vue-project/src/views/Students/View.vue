<template>
   <div class="card">
    <div class="card-header">
        <h4>
            Students
            <RouterLink to="/students/create" class="btn btn-primary float-end">Add Student</RouterLink>
        </h4>
    </div>
    <div class="card-body">
        <table class="table table-bordered">
            <thead>
                <tr>
                    <th>ID</th>
                    <th>Name</th>
                    <th>Address</th>
                    <th>Phone</th>
                    <th>Active</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(student, index) in this.students" v-bind:key="index">
                    <td>{{ student.cusId }}</td>
                    <td>{{ student.name }}</td>
                    <td>{{ student.address }}</td>
                    <td>{{ student.contactNumber }}</td>
                    <td>
                        <RouterLink to="/" class="btn btn-success">
                            Edit
                        </RouterLink>
                        <button type="button" class="btn btn-danger custom-margin">
                            Delete
                        </button> 
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
   </div>
</template>


<script>
import axios from 'axios'

export default{
    name : 'students',
    data(){
        return{
            students : []
        }
    },
    mounted(){
        this.getStudents()
        // console.log('i am here')
    },
    methods: {
        getStudents(){
            axios.get('http://localhost:8080/api/v1/customer/get/all').then((res) => {
                this.students = res.data.data
                console.log(this.students)
                // console.log(res.data.data)
            })
        }
    }
}
</script>


<style>
.custom-margin{
    margin-left: 10px;
}
</style>