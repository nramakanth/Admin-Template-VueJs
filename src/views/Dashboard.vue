<script setup lang="ts">
import { computed, ref } from 'vue'

interface User {
  name: string
  email: string
  title: string
  title2: string
  status: string
  role: string
}

const testUser: User = {
  name: 'John Doe',
  email: 'john@example.com',
  title: 'Software Engineer',
  title2: 'Web dev',
  status: 'Active',
  role: 'Owner',
}

const users = ref<User[]>([...Array(6).keys()].map(() => testUser))

const itemsPerPage = 5
const currentPage = ref(1)

const paginatedUsers = computed(() => {
  const start = (currentPage.value - 1) * itemsPerPage
  const end = start + itemsPerPage
  return users.value.slice(start, end)
})

const totalPages = computed(() => Math.ceil(users.value.length / itemsPerPage))

function toggleAddItem() {
  showAddItem.value = !showAddItem.value
}
</script>

<script lang="ts">
export default {
  data() {
    return {
      showAddItem: false,
    }
  },
  methods: {
    toggleAddItem() {
      this.showAddItem = !this.showAddItem
    },
  },

}
</script>

<template>
  <div>
    <!-- <h3 class="text-3xl font-medium text-gray-700">
      Dashboard
    </h3> -->
    <div>
      <!-- <h3 class="text-3xl font-medium text-gray-700">
      Dashboard
    </h3> -->
      <div id="app">
        <div class="flex ">
          <span class="text-3xl font-medium text-gray-700 animate-right">Dashboard</span>

          <!-- <button class="intro-y text-xl font-medium text-white px-5 bg-blue-500 rounded-2xl" @click="addItem">
            Add Item
          </button> -->
        </div>
        <div class="flex mt-2 justify-between">
          <!-- <button class="intro-y text-xl font-medium text-white px-5 bg-blue-500 rounded-lg py-1" @click="addItem">
            Add Item
          </button> -->
          <router-link
            class=" text-xl font-medium text-white px-5 bg-blue-500 rounded-lg py-1"
            :class="[$route.name === 'Additem' ? activeClass : inactiveClass]"
            to="additem"
          >
            Add Item <span>
              <i class="fa-solid fa-plus" />
            </span>
          </router-link>
          <div class="relative mx-4 lg:mx-0">
            <span class="absolute inset-y-0 left-0 flex items-center pl-3">
              <svg class="w-5 h-5 text-gray-500" viewBox="0 0 24 24" fill="none">
                <path
                  d="M21 21L15 15M17 10C17 13.866 13.866 17 10 17C6.13401 17 3 13.866 3 10C3 6.13401 6.13401 3 10 3C13.866 3 17 6.13401 17 10Z"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                />
              </svg>
            </span>

            <input
              class="w-32 pl-10 pr-4 text-indigo-600 border-gray-200 rounded-full sm:w-64 focus:border-indigo-600 focus:ring focus:ring-opacity-40 focus:ring-indigo-500"
              type="text"
              placeholder="Search..."
            >
          </div>
        </div>
      </div>

      <div
        class="flex flex-col mt-8 "
      >
        <div class="py-2 -my-2 overflow-x-auto sm:-mx-6 sm:px-6 lg:-mx-8 lg:px-8 ">
          <div
            class="inline-block min-w-full overflow-hidden align-middle border-b border-gray-200 shadow sm:rounded-lg "
          >
            <table class="min-w-full ">
              <thead>
                <tr>
                  <th
                    class="px-6 py-3 text-xs font-medium leading-4 tracking-wider text-left text-gray-500 uppercase border-b border-gray-200 bg-gray-50"
                  >
                    Name
                  </th>
                  <th
                    class="px-6 py-3 text-xs font-medium leading-4 tracking-wider text-left text-gray-500 uppercase border-b border-gray-200 bg-gray-50"
                  >
                    Title
                  </th>
                  <th
                    class="px-6 py-3 text-xs font-medium leading-4 tracking-wider text-left text-gray-500 uppercase border-b border-gray-200 bg-gray-50"
                  >
                    Status
                  </th>
                  <th
                    class="px-6 py-3 text-xs font-medium leading-4 tracking-wider text-left text-gray-500 uppercase border-b border-gray-200 bg-gray-50"
                  >
                    Role
                  </th>
                  <th class="px-6 py-3 text-xs font-medium leading-4 tracking-wider text-left text-gray-500 uppercase border-b border-gray-200 bg-gray-50 ml-5">
                    Action
                  </th>
                </tr>
              </thead>

              <tbody class="bg-white  ">
                <tr v-for="(u, index) in users" :key="index" class="hover:bg-gray-200 fade-left">
                  <td
                    class="px-6 py-4 border-b border-gray-200 whitespace-nowrap "
                  >
                    <div class="flex items-center">
                      <div class="flex-shrink-0 w-10 h-10">
                        <img
                          class="w-10 h-10 rounded-full"
                          src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
                          alt=""
                        >
                      </div>

                      <div class="ml-4">
                        <div class="text-sm font-medium leading-5 text-gray-900 slideOutRight">
                          {{ u.name }}
                        </div>
                        <div class="text-sm leading-5 text-gray-500">
                          {{ u.email }}
                        </div>
                      </div>
                    </div>
                  </td>

                  <td
                    class="px-6 py-4 border-b border-gray-200 whitespace-nowrap"
                  >
                    <div class="text-sm leading-5 text-gray-900">
                      {{ u.title }}
                    </div>
                    <div class="text-sm leading-5 text-gray-500">
                      {{ u.title2 }}
                    </div>
                  </td>

                  <td
                    class="px-6 py-4 border-b border-gray-200 whitespace-nowrap"
                  >
                    <span
                      class="inline-flex px-2 text-xs font-semibold leading-5 text-green-800 bg-green-100 rounded-full"
                    >{{ u.status }}</span>
                  </td>

                  <td
                    class="px-6 py-4 text-sm leading-5 text-gray-500 border-b border-gray-200 whitespace-nowrap"
                  >
                    Role
                  </td>

                  <td class="px-6 py-4 text-sm leading-5 text-gray-500 border-b border-gray-200 whitespace-nowrap">
                    <div class="flex">
                      <router-link
                        class="flex  items-center px-6 py-2 mt-4 duration-200 border-l-4 justify-between"
                        :class="[$route.name === 'Dashboard' ? activeClass : inactiveClass]"
                        to="/edit"
                      >
                        <i class="fa-solid fa-edit" />
                      </router-link>
                      <router-link
                        class=" items-center px-6 py-2 mt-4 duration-200 border-l-4 justify-between text-red-600"
                        :class="[$route.name === 'Dashboard' ? activeClass : inactiveClass]"
                        to="/dashboard"
                      >
                        <i class="fa-solid fa-trash" />
                      </router-link>
                    </div>
                  </td>
                </tr>
              </tbody>
            </table>
          </div>
          <div class="flex justify-center mt-4">
            <button
              class="px-4 py-2 mr-2 text-sm text-gray-700 bg-blue-700 text-white border rounded-full hover:bg-blue-500 hover:text-white"
              :disabled="currentPage === 1"
              @click="currentPage -= 1"
            >
              Previous
            </button>

            <span class="text-sm text-gray-700 px-4 py-2">
              Page {{ currentPage }} of {{ totalPages }}
            </span>

            <button
              class="px-4 py-2 mr-2 text-sm text-gray-700 bg-blue-700 text-white border rounded-full hover:bg-blue-500 hover:text-white"
              :disabled="currentPage === totalPages"
              @click="currentPage += 1"
            >
              Next
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
