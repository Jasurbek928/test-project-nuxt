<template>
  <div>
     <header class="bg-white shadow">
      <div class="max-w-7xl mx-auto py-6 px-4 sm:px-6 lg:px-8">
        <h1 class="text-3xl  text-gray-900">User : {{$route.params.id}}</h1>
      </div>
    </header>
     <main>
      <div class="max-w-7xl mx-auto py-6 sm:px-6 lg:px-8">
        <!-- Replace with your content -->
        <div class="px-4 py-6 sm:px-0">
          <!-- This example requires Tailwind CSS v2.0+ -->
          <div class="flex flex-col">
            <div class="-my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
              <div class="py-2 align-middle inline-block min-w-full sm:px-6 lg:px-8">
                <div class=" shadow overflow-hidden border-b border-gray-200 sm:rounded-lg">
                   Name:
                  <input type="text" class="mt-1 focus:ring-indigo-500 focus:border-indigo-500 block w-full shadow-sm sm:text-sm border-gray-300 rounded-md" v-model="user.name">
                 <br>
                  Username:
                  <input type="text" class="mt-1 focus:ring-indigo-500 focus:border-indigo-500 block w-full shadow-sm sm:text-sm border-gray-300 rounded-md" v-model="user.username">
                  <br>
                  Email:
                  <input type="email" class="mt-1 focus:ring-indigo-500 focus:border-indigo-500 block w-full shadow-sm sm:text-sm border-gray-300 rounded-md" v-model="user.email">
                  
                  <br/>
                 Website:
                  <input type="text" class="mt-1 focus:ring-indigo-500 focus:border-indigo-500 block w-full shadow-sm sm:text-sm border-gray-300 rounded-md" v-model="user.website">

               
               
               
               
               
               
               
               
               
               
               
               
               
               
               
                </div>
              </div>
            </div>
          </div>
        </div>
        <!-- /End replace -->
      </div>
    </main>
  </div>

</template>

<script>
export default {
  data(){
    return{
      user:{}
    }
  },
 async mounted(){
       await this.$axios.get("https://jsonplaceholder.typicode.com/users/" +  this.$route.params.id)
        .then((res)=> {
          this.user=res.data
          console.log(res)
      })
    },
   methods:{
    userUpdateData(){
        this.$axios.put("https://jsonplaceholder.typicode.com/users/" +  this.$route.params.id,{...this.user} )
          .then((res)=>{
            this.$router.push('/')
        })
    }
  }
}
</script>

<style>

</style>
