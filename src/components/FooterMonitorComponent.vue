<template>
  <div class="w-full h-28 text-center fixed bottom-1 z-10">
    <div
      class="flex flex-row items-center justify-center custom-gradient-bg lg:justify-around relative w-[90%]  mx-auto  border border-[#696cff] shadow-lg py-2 px-3 rounded-xl"
    >

      <div
        class="absolute top-[-25px] left-1/2 transform -translate-x-1/2 custom-gradient-bg4 border border-[#696cff]  w-12 h-12 p-1 rounded-full cursor-pointer"
      >
         <router-link to="/expertMonitor/PropertyMonitor">
          <span class="inline-block p-1 rounded-full">
            <img src="/icons/home.png" class="w-7 opacity-85" alt="" />
          </span>
        </router-link>
       
      </div>
      <div class="flex items-center justify-between w-full lg:w-1/6 gap-5  lg:mt-0">
        <router-link to="/expertMonitor/ProfileMonitor">
        
          <div class="flex flex-col items-center gap-1 cursor-pointer">
            <span class="inline-block p-1 rounded-full">
              <img src="/icons/user.png" class="w-7 opacity-85" alt="" />
            </span>
            <span class="text-sm"> پرفایل </span>
          </div>
      </router-link>
     
       
    
      </div>
      <div></div>
      <div class="flex items-center justify-end w-full lg:w-1/6 gap-5">
        <div class="flex flex-col items-center gap-1 cursor-pointer">
          <router-link to="/expertMonitor/NotificationMonitor" class="flex flex-col items-center gap-1">
          <span class="inline-block p-1 rounded-full">
            <img src="/icons/alert8.png" class="w-7 opacity-85" alt="" />
          </span>
          <span class="text-sm">  پیام ها  </span>
          </router-link>
        </div>
      
      </div>
    </div>
  </div>
</template>
<script></script>
