<template>
  <div class="w-full h-28 text-center fixed bottom-20 lg:bottom-2 z-10">
    <div
      class="flex flex-col lg:flex-row items-center justify-center lg:justify-between relative w-[90%]  mx-auto bg-gold3 shadow-lg py-2 px-3 rounded-xl"
    >

      <div
        class="absolute top-[-25px] left-1/2 transform -translate-x-1/2 bg-gold6 w-12 h-12 p-1 rounded-full cursor-pointer"
      >
         <router-link to="/">
          <span class="inline-block p-1 rounded-full">
            <img src="/icons/home.png" class="w-7" alt="" />
          </span>
        </router-link>
       
      </div>
      <div class=" flex items-center justify-between w-full lg:w-2/6 gap-5 mt-5 lg:mt-0">
        <router-link to="/filing">
        
          <div class="flex flex-col items-center  gap-1 cursor-pointer">
            <span class="inline-block p-1 rounded-full">
              <img src="/icons/page.png" class="w-7" alt="" />
            </span>
            <span class="text-sm"> فایلینگ </span>
          </div>
      </router-link>
     
       
       <router-link to="/ApplicantsView">
         
            <div class="flex flex-col items-center gap-1 cursor-pointer">
              <span class="inline-block p-1 rounded-full">
                <img src="/icons/Applicant.png" class="w-[27px]" alt="" />
              </span>
              <span class="text-sm"> متقاضیان </span>
            </div>

       </router-link>
      
       <router-link to="/VideoView">
         
         <div class="flex flex-col items-center gap-1 cursor-pointer">
           <span class="inline-block p-1 rounded-full">
             <img src="/icons/video2.png" class="w-7" alt="" />
           </span>
           <span class="text-sm"> آموزش </span>
         </div>

    </router-link>
      </div>
      <div></div>
      <div class=" flex items-center justify-between w-full lg:w-2/6 gap-5">
        <div class="flex flex-col items-center gap-1 cursor-pointer">
          <router-link to="/FilesPageView" class="flex flex-col items-center justify-center gap-1 mr-[-5px] lg:mr-0">
          <span class="inline-block p-1 rounded-full">
            <img src="/icons/fileSvg.svg" class="w-7" alt="" />
          </span>
          <span class="text-sm"> دفاتر فایل </span>
          </router-link>
        </div>
        <div class="flex flex-col items-center gap-1 cursor-pointer">
          <router-link to="/CustomersView" class="flex flex-col items-center gap-1">
            <span class="inline-block p-1 rounded-full">
              <img src="/icons/subscription.png" class="w-8" alt="" />
            </span>
            <span class="text-sm"> اشتراک </span>
          </router-link>
        </div>
       
        <div class="flex flex-col items-center gap-1 cursor-pointer">
          <router-link to="/expert/loginExpert" class="flex flex-col items-center gap-1 ml-[-5px] lg:mr-0">
            <span class="inline-block p-1 rounded-full">
              <img src="/icons/user.png" class="w-7" alt="" />
            </span>
            <span class="text-sm"> متخصصان </span>
          </router-link>
        </div>
      </div>
    </div>
  </div>
</template>
<script></script>
