<template>
    <main>
  
      <div class="py-4 container-fluid">
        <div class="row">
          <div class="col-md-8">
            <div class="card">
              <div class="card-header pb-0">
                <div class="d-flex align-items-center">
                </div>
              </div>
              <div class="card-body">
                <p class="text-uppercase text-sm">Update User</p>
                <div class="row">
                  <div class="col-md-12">
                    <label for="example-text-input" class="form-control-label"
                      >Name</label
                    >
                    <input class="form-control" type="text" v-model="name"/>
                  </div>
                  <div class="col-md-12">
                    <label for="example-text-input" class="form-control-label"
                      >Job</label
                    >
                    <input class="form-control" type="text" v-model="job"/>
                  </div>
                  
                </div>
              </div>
              <button class="btn mb-0 btn-outline-success btn-sm null null"  @click="updateUser()">Update</button>
              <div id="name"></div>
              <div id="job"></div>
              <ul v-if="errors && errors.length">
          <li v-for="error of errors">
            {{error.message}}
          </li>
        </ul>
              </div>
            </div>
          </div>
          <div class="col-md-4">
            <profile-card />
          </div>
        </div>
  
    </main>
  </template>

<script>
    import axios from 'axios';
    
    export default {
        data() {
            return {
                name: '',
                job: ''
    
            }
    
    
    
        },
    
        methods: {
            async updateUser() {
                try {
                    const user = await axios.put(
                        "https://reqres.in/api/users/2",
                        {
                            name: this.name,
                            job: this.job,
                        }
                    );
    
                    console.log(user);
                    alert("User updated!");
                } catch (e) {
                    console.log(e);
                }
            }
        },
    }
    </script>