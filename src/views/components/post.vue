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
                <p class="text-uppercase text-sm">Tambah User</p>
                <div class="row">
                  <div class="col-md-12">
                    <label for="example-text-input" class="form-control-label"
                      >Name</label
                    >
                    <input class="form-control" type="text" v-model="postName"/>
                  </div>
                  <div class="col-md-12">
                    <label for="example-text-input" class="form-control-label"
                      >Job</label
                    >
                    <input class="form-control" type="text" v-model="postJob"/>
                  </div>
                  
                </div>
              </div>
              <button class="btn mb-0 btn-outline-success btn-sm null null"  @click="postPost()">Tambah</button>
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
          postBody: '',
          postName: '',
          postJob: '',
          errors: []
        }
      },
    
      methods: {
        // Pushes posts to the server when called.
        postPost() {
          var text = {
            name: this.postName,
            job: this.postJob
          }
          this.postBody = JSON.stringify(text)
          axios.post(`https://reqres.in/api/users`, {
            body: this.postBody
          })
            .then(response => { })
            .catch(e => {
              this.errors.push(e)
            })
            document.getElementById('name').innerHTML = '<div class="fs-4">Nama : ' + this.postName + '</div>'
            document.getElementById('job').innerHTML = '<div class="fs-4">Job : ' + this.postJob + '</div>'
          console.log(this.postBody)
        }
      }
    }
    </script>
  