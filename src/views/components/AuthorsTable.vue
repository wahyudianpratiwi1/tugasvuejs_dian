<template>
  <div class="card">
    <div class="card-header pb-0">
      <h6>Authors table</h6>
      <button class="btn mb-0 btn-outline-success btn-sm null null"><router-link to="/post" class="nav-link">Tambah</router-link></button>
    </div>
    <div class="card-body px-0 pt-0 pb-2">
      <div class="table-responsive p-0">
        <table class="table align-items-center mb-0">
          <thead>
            <tr>
            <th class="text-uppercase font-weight-bolder opacity-7">
              Foto
            </th>
            <th class="text-uppercase font-weight-bolder opacity-7">
              First Name
            </th>
            <th class="text-uppercase font-weight-bolder opacity-7">
              Last Name
            </th>
            <th class="text-uppercase font-weight-bolder opacity-7">
              Email
            </th>
            <th class="text-uppercase font-weight-bolder opacity-7">
              Actions
            </th>
            </tr>
          </thead>
          <tbody v-if="posts && posts.length">
          <tr v-for="post of posts">
              <td>
                <div class="d-flex px-2 py-1">
                  <div>
                    <img
                      :src=post.avatar
                      class="avatar avatar-sm me-3"
                      alt=""
                    />
                  </div>
                  <div class="d-flex flex-column justify-content-center">
                    <h6 class="mb-0 text-sm">{{post.first_name}}</h6>
                    <p class="text-xs text-secondary mb-0">{{post.email}}</p>
                  </div>
                </div>
              </td>
              <td>
                <p class="text-xs font-weight-bold mb-0">
                  {{post.first_name}}
                </p>
              </td>
              <td>
                <p class="text-xs font-weight-bold mb-0">
                  {{post.last_name}}
                </p>
              </td>
              <td>
                <p class="text-xs font-weight-bold mb-0">
                  {{post.email}}
                </p>
              </td>
              <!-- <td class="align-middle text-center text-sm">
                <span class="badge badge-sm bg-gradient-success">Online</span>
              </td> -->
              <!-- <td class="align-middle text-center">
                <span class="text-secondary text-xs font-weight-bold">23/04/18</span>
              </td> -->
              <td class="align-middle">
                <a
                  href="javascript:;"
                  class="text-secondary font-weight-bold text-xs"
                  data-toggle="tooltip"
                  data-original-title="Edit user"
                  @click="updateUser"
                ><router-link to="/put" class="nav-link">Edit</router-link></a>
              </td>
              <td class="align-middle">
                <a
                  href="javascript:;"
                  class="far fa-trash-alt me-2 text-xs " aria-hidden="true"
                  data-toggle="tooltip"
                  data-original-title="Hapus user"
                  @click="deleteUser"
                >Hapus</a>
              </td>
              <ul v-if="errors && errors.length">
            <li v-for="error of errors">
              {{error.message}}
            </li>
            </ul>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: "authors-table",
  data() {
    return {
      posts: [],
      errors: []
    }
  },

  // Fetches posts when the component is created.
  created() {
    axios.get(`https://reqres.in/api/users?page=2`)
    .then(response => {
      // JSON responses are automatically parsed.
      this.posts = response.data.data
    })
    .catch(e => {
      this.errors.push(e)
    })
  },

  methods: {
        async deleteUser() {
            let x = window.confirm("You want to delete the user?");

            if (x) {
                const user = await axios.delete(
                    "https://reqres.in/api/users/2"
                );

                console.log(user);
                alert("User deleted!");
            }
        },
    },
}
</script>