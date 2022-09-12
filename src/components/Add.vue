<template>
    <div class="submit-form">
        <div v-if="!submitted">
        <label for="email">Email</label>
        <input type="text" class="form-control" id="email" required v-model="email" name="email">
        <label for="firstname">First Name</label>
        <input type="text" class="form-control" id="firstname" required v-model="firstname" name="firstname">
        <label for="email">Last Name</label>
        <input type="text" class="form-control" id="lastname" required v-model="lastname" name="email">    
    </div>
        <button @click="save" class="btn btn-success">Submit</button>
    </div>
</template>

<script>
    import dataservice from '../services/dataservice';
    export default{
        name:"add",
        data(){
            return{
                email:"",
                firstname:"",
                lastname:"",
                submitted:false
            };
        },
    methods:{
        save(){
            var data={
                email:this.email,
                firstname:this.firstname,
                lastname:this.lastname
            };
            dataservice.create(data)
            .then(response=>{
                this.submitted=true;
                console.log(response.data);
            })
            .catch(e=>{
                console.log(e);
            });
        },
    },
    };
</script>
<style>
    .submit-form{
        margin: auto;
        max-width: 300px;
    }
</style>