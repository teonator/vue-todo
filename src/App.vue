<script>
export default {
  data() {
    return {
      tasks: [
          {
            label: 'Feed the cat',
            done: 0
          },      
          {
            label: 'Pick up the milk',
            done: 1
          }        
      ]
    }
  }
}
</script>

<template>
<div>
  <div class="row mb-3">
      <div class="col col-xl-8 offset-xl-2">

          <h1>Todo</h1>

      </div>
  </div>

  <div class="row d-flex justify-content-center">
      <div class="col col-xl-8">

          <div class="card">
              <div class="card-body p-5">

                <div class="d-flex align-items-center mt-4">
                  <h4 class="flex-fill m-0">Tasks</h4>
                </div>                  

                <div class="list-group mt-3">
                  <div v-for="task in tasks" class="list-group-item list-group-item-action d-flex align-items-center">
                    <a class="btn btn-sm me-2 btn-outline-secondary">
                      <i class="fas fa-check text-white"></i>
                    </a>
                    <p class="flex-grow-1 mb-0 text-secondary">{{ task.label }}</p>  
                  </div>
                </div>

              </div>
          </div>
      </div>
  </div>

  <div class="row mt-3">
      <div class="col col-xl-8 offset-xl-2 text-end">

          <span>Made with <a href="https://vuejs.org" target="_blank">Vue.js</a></span>

      </div>
  </div>
</div>
</template>
