<script setup lang="ts">
import { ref } from 'vue'
import { useSidebar } from '../composables/useSidebar'

const { isOpen } = useSidebar()
const activeClass = ref(
  // 'bg-gray-600 bg-opacity-25 text-gray-100 border-gray-100',
)
const inactiveClass = ref(
  // 'border-gray-900 text-gray-500 hover:bg-gray-600 hover:bg-opacity-25 hover:text-gray-100',
)
</script>

<script lang="ts">
export default {
  data() {
    return {
      items: [
        {
          title: 'Item 1',
          open: false,
          subItems: ['Subitem 1.1', 'Subitem 1.2'],
        },
        {
          title: 'Item 2',
          open: false,
          subItems: ['Subitem 2.1', 'Subitem 2.2'],
        },
        {
          title: 'Item 3',
          open: false,
          subItems: ['Subitem 2.1', 'Subitem 2.2'],
        },
        {
          title: 'Item 4',
          open: false,
          subItems: ['Subitem 2.1', 'Subitem 2.2'],
        },
        // Add more items as needed
      ],
    }
  },
  methods: {
    toggleItem(index) {
      this.items[index].open = !this.items[index].open
    },
  },
}
</script>

<template>
  <div class="flex">
    <!-- Backdrop -->
    <div
      :class="isOpen ? 'block' : 'hidden'"
      class="fixed inset-0 z-20 transition-opacity bg-black opacity-50 lg:hidden"
      @click="isOpen = false"
    />
    <!-- End Backdrop -->

    <div
      :class="isOpen ? 'translate-x-0 ease-out' : '-translate-x-full ease-in'"
      class="fixed inset-y-0 left-0 z-30 w-64 overflow-y-auto transition duration-300 transform bg-white lg:translate-x-0 lg:static lg:inset-0"
    >
      <div class="flex items-center justify-center mt-8">
        <div class=" items-center">
          <span class="block border-4 text-center rounded-full"><i class="fa-solid fa-user text-5xl border-lg p-4" />
          </span>
          <p class="block mt-4 text-center">
            User
          </p>
          <p class="block text-xl font-bold text-red-900 text-center ">
            Admin
          </p>
        </div>
      </div>

      <nav class="mt-10">
        <div>
          <ul class="animate-right">
            <li>
              <router-link
                class="flex  items-center px-6 py-2 mt-4 duration-200 border-l-4 justify-between"
                :class="[$route.name === 'Dashboard' ? activeClass : inactiveClass]"
                to="/dashboard"
              >
                <span class="flex items-center">
                  <span class=" text-black text-lg">Dashboard</span>

                </span>
                <img
                  src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABQAAAAUCAYAAACNiR0NAAAACXBIWXMAAAsTAAALEwEAmpwYAAABIUlEQVR4nKXUu0oDURCA4Y8gFiLexSaaNKJgIQhiIVhoJWKnpVpZ2wRfwcJKsFEIKIplCm+F4AVRQfQJBN9FFiYhhLAmmx8OLGdm/92d2TOkU8QpfmKdoCADMyjjDWvIxUqu3yOW5KQyjRIecY3llNwkdhO5JUw1Jtyhgh0Ma52RuKcSjhqv6JOdAbzUb9wj34GwECWokXRyoQPhEo7rN/ax1YFwF3uNXTvqQHjV+IW9+Mooy+EX3Y2BW0xmEM7jsllgE4cZhGfRlKav/onRNmTjeEhL2MZBG8IyVtISuvAcdfmPVVy08tRidDztKOZj6vRrkfWYJD1NYkMhm9MmSdefYqJUmcAHFtuVVUlO0HcM1o0oxWxWWZUxnMf/Nvhf9h+TiSxFg+9hrAAAAABJRU5ErkJggg=="
                  class="ml-auto"
                >
              </router-link>
            </li>

            <li>
              <div class="cursor-pointer flex items-center" @click="toggleItem(0)">
                <span class="flex-grow px-6 py-2 mt-4 duration-200 border-l-4 text-black text-lg">
                  Admissions
                  <span
                    :class="{ 'rotate-180': items[0].open }"
                    class="transition-transform duration-300 inline-block "
                  ><i class="fa-solid fa-chevron-down fa-xs" />
                  </span>
                </span>

                <span class="ml-auto flex-grow-0 px-6 py-2 mt-4">
                  <i class="fa-regular fa-user" />
                </span>
              </div>

              <ul v-if="items[0].open" class="px-6 py-2 bg-gray-300 rounded-lg mx-5 fadeInDown">
                <li class="text-black text-base mt-2 p-2 ">
                  Admission List
                </li>
                <li class="text-black text-base mt-2 p-2 ">
                  Admission Email
                </li>
                <li class="text-black text-base mt-2 p-2 ">
                  Admission Sms
                </li>
              </ul>
            </li>
            <li>
              <div class="cursor-pointer flex justify-between items-center" @click="toggleItem(1)">
                <span class="flex-grow items-center px-6 py-2 mt-4 duration-200 border-l-4 text-black text-lg">
                  Registration
                  <span
                    :class="{ 'rotate-180': items[1].open }"
                    class="transition-transform duration-300 inline-block  flex-grow-0"
                  ><i class="fa-solid fa-chevron-down fa-xs" />
                  </span>
                </span>

                <span class="ml-auto px-6 py-2 mt-4 flex-grow-0">
                  <i class="fa-solid fa-users" />
                </span>
              </div>
              <ul v-if="items[1].open" class="px-6 py-2 bg-gray-300 rounded-lg mx-5 fadeInDown">
                <li class="text-black text-base mt-2 p-2 animate-right">
                  Registration List
                </li>
                <li class="text-black text-base mt-2 p-2 fade-left">
                  Registration Email
                </li>
                <li class="text-black text-base mt-2 p-2 animate-right">
                  Registration Sms
                </li>
              </ul>
            </li>
            <li>
              <div class="cursor-pointer flex justify-between items-center" @click="toggleItem(2)">
                <span class="flex-grow flex items-center px-6 py-2 mt-4 duration-200 border-l-4 text-black text-lg ">
                  Accounting
                  <span
                    :class="{ 'rotate-180': items[2].open }"
                    class="transition-transform duration-300 inline-block  flex-grow-0 mx-1"
                  ><i class="fa-solid fa-chevron-down fa-xs" />
                  </span>
                </span>

                <span class="ml-auto px-6 py-2 mt-4 flex-grow-0">
                  <i class="fa-solid fa-clock" />
                </span>
              </div>
              <ul v-if="items[2].open" class="px-6 py-2 bg-gray-300 rounded-lg mx-5 fadeInDown">
                <li class="text-black text-base mt-2 p-2">
                  Inovice
                </li>
                <li class="text-black text-base mt-2 p-2">
                  Payments
                </li>
                <li class="text-black text-base mt-2 p-2">
                  Items
                </li>
              </ul>
            </li>
            <li>
              <router-link
                class="flex items-center px-6 py-2 mt-4 duration-200 border-l-4 justify-between"
                :class="[$route.name === 'Modal' ? activeClass : inactiveClass]"
                to="/modal"
              >
                <span class="flex items-center">
                  <span class=" text-black text-lg">Courses</span>

                </span>

                <i class="fa-solid fa-book" />
              </router-link>
            </li>
            <li>
              <router-link
                class="flex items-center px-6 mt-4 duration-200 border-l-4 justify-between"
                :class="[$route.name === 'Modal' ? activeClass : inactiveClass]"
                to="/modal"
              >
                <span class="flex items-center">
                  <span class="text-black text-lg">Sujects</span>

                </span>

                <i class="fa-solid fa-book" />
              </router-link>
            </li>

            <li>
              <div class="cursor-pointer flex justify-between items-center mt-4" @click="toggleItem(3)">
                <span class="flex items-center px-6  duration-200 border-l-4 text-black text-lg">
                  Messages
                  <span
                    :class="{ 'rotate-180': items[3].open }"
                    class="transition-transform duration-300 inline-block ml-4 flex-grow-0"
                  ><i class="fa-solid fa-chevron-down fa-xs" />
                  </span>
                </span>

                <span class="ml-auto px-6 py-2 mt-4 flex-grow-0">
                  <i class="fa-solid fa-message" />
                </span>
              </div>
              <ul v-if="items[3].open" class="px-6 py-2 bg-gray-300 rounded-lg mx-5 fadeInDown">
                <li class="text-black text-base mt-2 p-2">
                  Messages
                </li>
                <li class="text-black text-base mt-2 p-2">
                  Bulk Email
                </li>
                <li class="text-black text-base mt-2 p-2">
                  Bulk Sms
                </li>
                <li class="text-black text-base mt-2 p-2">
                  Logs
                </li>
              </ul>
            </li>
            <li>
              <router-link
                class="flex items-center px-6 py-2 duration-200 border-l-4 justify-between mt-4"
                :class="[$route.name === 'Modal' ? activeClass : inactiveClass]"
                to="/modal"
              >
                <span class="flex items-center">
                  <span class="text-black text-lg">Settings</span>

                </span>

                <i class="fa-solid fa-gear" />
              </router-link>
            </li>
            <li>
              <router-link
                class="flex items-center px-6 py-2  duration-200 border-l-4 justify-between mt-4"
                :class="[$route.name === 'Modal' ? activeClass : inactiveClass]"
                to="/modal"
              >
                <span class="flex items-center">
                  <span class=" text-black text-lg">Users</span>

                </span>

                <i class="fa-solid fa-user" />
              </router-link>
            </li>
            <li>
              <router-link
                class="flex items-center px-6  duration-200 border-l-4 justify-between mt-4"
                :class="[$route.name === 'Modal' ? activeClass : inactiveClass]"
                to="/modal"
              >
                <span class="flex items-center">
                  <span class="text-black text-lg">Profile</span>

                </span>

                <i class="fa-solid fa-user" />
              </router-link>
            </li>
          </ul>
        </div>
      </nav>
    </div>
  </div>
</template>
