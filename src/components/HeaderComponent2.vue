<template>
     <div class="w-full flex items-center justify-between py-3">
        <div class="flex items-center gap-4">
          <div>
            <img src="/img/sorena.png" class="w-[30px]" alt="" />
          </div>
          <div>
            <span class="text-gradient text-xl font-semibold"
              >املاک سورنا</span
            >
          </div>
        </div>
        <div class="flex items-center gap-4">
          <div
            class="w-10 h-10 p-2 border border-1 border-gray-400 custom-gradient-bg4 rounded-full relative"
          >
            <span
              class="absolute bg-red-400 text-[12px] text-white w-5 h-5 rounded-full flex items-center justify-center top-[-5px] left-6"
              >3</span
            >
            <router-link to="/notification">
              <img
                src="/icons/alert.png"
                class="w-[30px] cursor-pointer"
                alt=""
              />
            </router-link>
          </div>
         
          <div class="relative">
            <div
              class="w-10 h-10 p-2 border border-1 border-gray-400 custom-gradient-bg4 rounded-full"
              @click="toggleSubMenu"
            >
              <img
                src="/icons/user.png"
                class="w-[30px] cursor-pointer"
                alt=""
              />
            </div>
            <div
              v-if="isSubMenuOpen"
              class="absolute top-[42px] left-1 w-[150px] bg-white border-2 border-gold1  rounded-lg shadow-xl z-30 text-sm"
            >
              <ul>
                <li>
                  <router-link to="/profile" class="profileBtn">حساب کاربری</router-link>
                </li>
                <li>
                  <router-link class="profileBtn" to="/password">تغییر رمز عبور</router-link>
                </li>
                <li>
                  <router-link class="profileBtn" to="/transactionsView">سوابق پرداختی</router-link>
                </li>
                <li>
                  <router-link class="profileBtn" to="/BuySubscriptionView">خرید اشتراک</router-link>
                </li>
                <li>
                  <router-link to="#" class="profileBtn">خروج</router-link>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
</template>
<script>


export default {
 
  data() {
    return {
    
      isSubMenuOpen: false,
    };
  },
  methods: {
    toggleSubMenu() {
      this.isSubMenuOpen = !this.isSubMenuOpen;
    },

  },
};
</script>
<style scoped>
ul {
  list-style: none;
  padding: 0;
}

li {
  padding:5px 0.5rem;
}

a.profileBtn {
  background-color: transparent;
  border: none;
  display: block;
  cursor: pointer;
  outline: none;
  width: 100%;
  text-align: right;
  padding: 5px 3px;
}

a.profileBtn:hover {
  background-color: #f3f4f6;
}
</style>
