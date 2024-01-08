<template>
  <span class="text-center text-black text-2xl">
    Add Items
  </span>
  <form action="#" class="w-full m-4 ">
    <div class="flex flex-wrap  mb-6 fade-left">
      <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
        <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2 ml-3" for="grid-first-name">
          First Name
        </label>
        <input id="grid-first-name" class="appearance-none block w-full text-black border-gray-200 rounded-full  focus:border-indigo-600 focus:ring focus:ring-opacity-40 focus:ring-indigo-500" type="text" placeholder="Jane">
      </div>
      <div class="w-full md:w-1/2 px-3">
        <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2 ml-3" for="grid-last-name">
          Last Name
        </label>
        <input id="grid-last-name" class="appearance-none block w-full text-black border-gray-200 rounded-full  focus:border-indigo-600 focus:ring focus:ring-opacity-40 focus:ring-indigo-500" type="text" placeholder="Doe">
      </div>
    </div>
    <div class="flex flex-wrap  mb-6">
      <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
        <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2 ml-3" for="grid-password">
          Password
        </label>
        <input id="grid-password" class="appearance-none block w-full text-black border-gray-200 rounded-full  focus:border-indigo-600 focus:ring focus:ring-opacity-40 focus:ring-indigo-500" type="password" placeholder="******************">
        <p class="text-gray-600 text-xs italic ml-3">
          Make it as long and as crazy as you'd like
        </p>
      </div>
      <div class="w-full md:w-1/2 px-3">
        <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2 ml-3" for="grid-password">
          Re-Password
        </label>
        <input id="grid-password" class="appearance-none block w-full text-black border-gray-200 rounded-full  focus:border-indigo-600 focus:ring focus:ring-opacity-40 focus:ring-indigo-500" type="password" placeholder="******************">
        <p class="text-gray-600 text-xs italic ml-3">
          Make it as long and as crazy as you'd like
        </p>
      </div>
    </div>
  </form>
</template>
