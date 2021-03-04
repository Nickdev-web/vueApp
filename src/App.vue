<template>
<div>
<div class="h-screen flex overflow-hidden bg-gray-100">
<sideBar /> 
<div class="flex flex-col w-0 flex-1 overflow-hidden">
<navigationBar />  
<usersInTable />
</div>
</div>
</div>
</template>

<script>
import usersInTable from './components/usersInTable.vue'
import sideBar from './components/sideBar.vue'
import navigationBar from './components/navigationBar.vue'
import './assets/tailwind.css'





export default {
      name: 'App',
      components: {
            usersInTable,
            sideBar,
            navigationBar
      },
      
}
</script>

<style>
 
</style>
