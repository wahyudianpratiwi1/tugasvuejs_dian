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
              <p class="text-uppercase text-sm">User Information</p>
              <div class="row">
                <div class="col-md-12">
                  <label for="example-text-input" class="form-control-label"
                    >Email</label
                  >
                  <input class="form-control" type="email"/>
                </div>
                <div class="col-md-12">
                  <label for="example-text-input" class="form-control-label"
                    >First name</label
                  >
                  <input class="form-control" type="text" />
                </div>
                <div class="col-md-12">
                  <label for="example-text-input" class="form-control-label"
                    >Last name</label
                  >
                  <input class="form-control" type="text" />
                </div>
                
              </div>
            </div>
            <button class="btn mb-0 btn-outline-success btn-sm null null" >Tambah</button>
            </div>
          </div>
        </div>
        <div class="col-md-4">
          <profile-card />
        </div>
      </div>

  </main>
</template>
