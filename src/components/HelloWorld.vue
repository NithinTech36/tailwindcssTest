<script setup>
const weekDays = ['MON', 'TUE', 'WED', 'THU', 'FRI', 'SAT', 'SUN'];
const dateRange = '13 January, 2025 - 19 January, 2025';
const events = [
  { day: 0, time: '8:00 AM - 10:00 AM', name: 'Thomas Smith', color: 'bg-blue-200', type: 'tech' },
  { day: 0, time: '8:00 AM - 10:00 AM', name: 'Thomas Smith', color: 'bg-yellow-100', type: 'tech' },
  { day: 2, time: '8:00 AM - 10:00 AM', name: 'Thomas Smith', color: 'bg-purple-200', type: 'tech' },
  { day: 2, time: '8:00 AM - 10:00 AM', name: 'Thomas Smith', color: 'bg-green-200', type: 'tech' },
  // Add more events as needed
];
</script>

<template>
  <div class=" min-h-screen bg-gray-800 shadow-lg text-white">
    <!-- Header -->
<div class="flex items-center justify-between  px-6 py-4 bg-gradient-to-r from-blue-900 to-black  shadow">
  <div class="flex items-center gap-2">
    <!-- set black background with blue border -->
    <button class=" border border-blue-700  px-8  rounded-full text-blue-400 font-bold mr-3">Today</button>
    <button class="text-2xl  border border-white-700  text-white  rounded-full w-8 h-8 flex items-center justify-center hover:bg-gray-700 transition">&#60;</button>
    <button class="text-2xl  border border-white-700  text-white rounded-full w-8 h-8 flex items-center justify-center hover:bg-gray-700 transition">&#62;</button>
    <span class="text-2xl font-semibold ml-6">{{ dateRange }}</span>
    <button class="ml-2 text-white text-xl">&#9660;</button>
  </div>
  <div class="flex items-center gap-4">
    <span class="bg-black bg-opacity-60 px-5 py-2 rounded-xl flex items-center gap-2 border border-blue-900">
      <span class="text-gray-300 font-semibold">Grand Total</span>
      <span class="text-white font-bold text-xl">$3,000</span>
    </span>
    <button class="bg-blue-600 px-5 py-2 rounded-lg text-white font-bold text-lg shadow hover:bg-blue-700 transition flex items-center gap-2">
      <span class="text-2xl">+</span> Add
    </button>
  </div>
</div>


<!-- Tabs -->
<div class="flex  py-2 mb-4 px-2 bg-gradient-to-r from-blue-900 to-black  shadow">
  <div class="flex  mb-1 flex-1 px-6 py-2 ">
  <button class="bg-gray-800 px-4 py-2  text-white ">Daily</button>
  <button class="bg-blue-600 px-4 py-2 font-bold text-white shadow">Weekly</button>
  <button class="bg-gray-800 px-4 py-2 text-white">Monthly</button>
  <button class="bg-gray-800 px-4 py-2 text-white">List</button>
  </div>
  <div class="flex gap-4 mb-4 px-6 py-2 flex-1 justify-end">
  <button class="bg-gray-800 px-4 py-2 rounded-lg text-white flex items-center gap-2">
    All Services
    <span class="text-lg">&#9660;</span>
  </button>
  <button class="bg-gray-800 px-4 py-2 rounded-lg text-white flex items-center gap-2">
    All Tech
    <span class="text-lg">&#9660;</span>
  </button>
</div>
</div>

<!-- Filters -->


    <!-- Calendar Grid -->
    <div class="grid grid-cols-7">
      <div v-for="(day, i) in weekDays" :key="day" class="border-r border-gray-500 bg-opacity-40 p-2 h-full">
        <div class="text-center font-bold mb-2">{{ day }}</div>
        <div v-for="event in events.filter(e => e.day === i)" :key="event.time + event.name" :class="['rounded-lg w-full p-2 mb-2 text-black', event.color]">
          <div class="font-semibold flex items-center gap-2">
            <span class="bg-blue-500 rounded-full w-6 h-6 flex items-center justify-center text-white text-xs">👤</span>
            {{ event.name }}
          </div>
          <div class="text-xs text-gray-700">{{ event.time }}</div>
        </div>
      </div>
    </div>
  </div>
</template>