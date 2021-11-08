<template>
  <div class="min-h-full">
 {{users}}
    <main>
      <div class="max-w-7xl mx-auto py-6 sm:px-6 lg:px-8">
        <!-- Replace with your content -->
        <div class="px-4 py-6 sm:px-0">
          <!-- This example requires Tailwind CSS v2.0+ -->
          <div class="flex flex-col">
            <div class="-my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
              <div class="py-2 align-middle inline-block min-w-full sm:px-6 lg:px-8">
                <div class="shadow overflow-hidden border-b border-gray-200 sm:rounded-lg">
                  <table class="min-w-full divide-y divide-gray-200">
                    <thead class="bg-gray-50">
                      <tr>
                        <th
                          scope="col"
                          class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
                        >T/r</th>
                        <th
                          scope="col"
                          class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
                        >Name</th>
                        <th
                          scope="col"
                          class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
                        >UserName</th>
                        <th
                          scope="col"
                          class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
                        >Email</th>
                        <th
                          scope="col"
                          class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
                        >street</th>
                         <th
                          scope="col"
                          class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
                        >suite</th>
                         <th
                          scope="col"
                          class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
                        >city</th>

                      </tr>
                    </thead>
                    <tbody class="bg-white divide-y divide-gray-200">
                      <tr v-for="(user,idx) in users" :key="idx" @click="UserProfile">
                        <td class="px-6 py-4 whitespace-nowrap">
                         {{user.id}}
                        </td>
                        <td class="px-6 py-4 whitespace-nowrap">
                         {{user.name}}
                        </td>
                        <td class="px-6 py-4 whitespace-nowrap">
                          {{user.username}}
                        </td>
                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
                          {{user.email}}</td>
                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
                          {{ user.address.street}}</td>
                      <td class="px-6 py-4 whitespace-nowrap">
                        {{ user.address.suite }}
                      </td>
                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
                          {{user.address.city}}</td>
                      </tr>
                    </tbody>
                  </table>
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

  methods:{
    UserProfile(){
      this.$router.push('/userProfile')
    }
  },

   async asyncData({ $axios }) {
      const users = await $axios.$get(`https://jsonplaceholder.typicode.com/users`)
      return { users }
    },
}
</script>
