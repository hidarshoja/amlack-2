<template>
    <div
    class="w-[90%]  min-h-[1000px] mx-auto bg-bg1 shadow-lg py-10 px-3 lg:px-28 rounded-xl"
    >
      <h3 class="flex gap-1 items-center">
        <span class="text-gold1 font-semibold"> متقاضیان</span>
        <span class="text-gold1 font-semibold">⟵</span>
      </h3>
      <div class="w-full relative mt-3">
        <input
          type="text"
          class="w-full py-2 px-3 rounded-lg text-sm border border-1 border-gray-400"
          placeholder="جستجو براساس نام  ، نام محدوده "
        />
        <img
          src="/icons/search.svg"
          class="w-6 absolute left-2 cursor-pointer top-2"
          alt=""
        />
      </div>
      <div class="flex mt-5 items-center justify-between">
        <div>
          <span
            @click="openModal = true"
            class="bg-gold1 text-sm py-1.5 px-4 rounded-lg border-green-700 border-1 border cursor-pointer text-gray-800 flex gap-2 items-center"
          >
            <span><img src="/img/filter.svg" class="w-4" alt="" /></span
            ><span>فیلترها</span>
          </span>
        </div>
        <div class="flex gap-2 text-sm text-gold1">
          <span>نمایش</span>
          <span>20</span>
          <span>مورد از</span>
          <span>33620</span>
        </div>
      </div>
      <div class="flex items-center mt-5 gap-3 flex-wrap justify-center">
        <div
        v-if="products.length > 0"
        v-for="item in products"
        :key="item"
        class="mt-10"
      >
        <a href="#">
          <div
            class="shadow-lg rounded-xl bg-gold1 font-yekan overflow-hidden border-t border-t-[#eaeaea]"
          >
            <div class="p-6 bg-gold1">
              <div class="w-full bg-gray-200 relative  rounded-t-lg overflow-hidden">
                <span class="absolute text-green-100 right-1 top-1 text-sm bg-green-700 rounded-md px-1">{{ item.title }}</span>
               <img :src="item.src" width="280px" height="80px" alt="">
              </div>
              <div
                class="text-white flex justify-around items-center py-2 pb-2 text-sm px-2 border-b border-dashed border-gray-300 bg-gray-700"
              >
                <div class="text-primary-10">
                  <span class="font-bold text-pink"> {{ item.type }} </span>
                </div>
                <div>{{ item.dic }}</div>
                <div></div>
              </div>
              <div
                class="bg-gray-200 inline-flex w-full justify-between items-center pb-2 border-b border-dashed border-gray-300 py-2 px-1"
              >
                <div class="text-sm">{{ item.meter }}</div>
                <div  class="ml-1 min-w-[20px] flex gap-2">
                  <img src="/img/location.svg" alt="location" class="w-5 h-5" />
                  <div class="min-w-0">
                    <p class="text-[#333] truncate font-semibold text-sm">
                      {{ item.city }}
                    </p>
                  </div>
                </div>
              </div>
              <div
                class="flex justify-between w-full items-center py-2 px-1 bg-gray-600 rounded-b-lg"
              >
                <div class="flex items-center">
                  <div class="m-1">
                    <img
                      src="/img/number.svg"
                      alt="number"
                      class="w-4 h-4 bg-white rounded-md"
                    />
                  </div>
                  <div class="font-yekanNum text-sm text-white">
                    {{ item.code }}
                  </div>
                </div>
                <div class="flex items-center ng-star-inserted">
                  <div class="m-1">
                    <img src="/img/date2.svg" alt="date" class="w-5 h-5 bg-white rounded-lg" />
                  </div>
                  <div class="font-yekanNum text-sm text-white">
                    {{ item.time }} ساعت پیش
                  </div>
                </div>
                <div class="flex justify-between items-center"></div>
              </div>
            </div>
            <div
              class="flex justify-center items-center pink px-0 py-2 text-white bg-[#f800ce] ng-star-inserted"
              v-if="item.type === 'رهن و اجاره'"
            >
              <div class="flex justify-start items-center mx-2">
                <div class="mx-1 font-yekan text-sm ng-star-inserted">رهن:</div>
                <div class="font-yekan text-sm ng-star-inserted">
                  {{ item.price }} میلیون تومان
                </div>
              </div>
              <div class="flex justify-start items-center mx-2">
                <div class="mx-1 font-yekan text-sm ng-star-inserted">
                  اجاره:
                </div>
                <div class="font-yekan text-sm ng-star-inserted">
                  {{ item.price2 }} میلیون تومان
                </div>
              </div>
            </div>
            <div
              class="flex justify-center items-center pink px-0 py-2 text-white bg-[#46e940] ng-star-inserted"
              v-if="item.type === 'خرید و فروش'"
            >
              <div class="flex justify-start items-center mx-2">
                <div class="mx-1 font-yekan text-sm ng-star-inserted">
                  قیمت متر:
                </div>
                <div class="font-yekan text-sm ng-star-inserted">
                  {{ item.price }} تومان
                </div>
              </div>
              <div class="flex justify-start items-center mx-2">
                <div class="mx-1 font-yekan text-sm ng-star-inserted">
                  قیمت کل:
                </div>
                <div class="font-yekan text-sm ng-star-inserted">
                  {{ item.price2 }} میلیون تومان
                </div>
              </div>
            </div>
          </div>
        </a>
      </div>
      <div
        v-else-if="products.length == 0"
        class="flex flex-col items-center justify-center gap-5"
      >
        <img src="/img/file.svg" class="w-72" alt="" />
        <span class="text-[#333] font-semibold">هیچ فایلی ثبت نشده است !</span>
      </div>
      </div>
      <nav
      class="flex items-center justify-between border-t border-gray-200 px-4 sm:px-0 mt-10"
    >
      <div class="-mt-px flex w-0 flex-1">
        <a
          href="#"
          class="inline-flex items-center border-t-2 border-transparent pr-1 pt-4 text-sm font-medium text-gold1 hover:border-gray-300 hover:text-gold6"
        >
          قبلی
        </a>
      </div>
      <div class="hidden md:-mt-px md:flex">
        <a
          href="#"
          class="inline-flex items-center border-t-4 border-transparent px-4 pt-4 text-sm font-medium text-gray-100 hover:border-gold1 hover:text-gold1"
          >1</a>
        <a
          href="#"
          class="inline-flex items-center border-t-4 border-gold1 px-4 pt-4 text-sm font-medium text-gold1"
          aria-current="page"
          >2</a
        >
        <a
          href="#"
          class="inline-flex items-center border-t-4 border-transparent px-4 pt-4 text-sm font-medium text-gray-100 hover:border-gold1 hover:text-gold1"
          >3</a>
          <a
          href="#"
          class="inline-flex items-center border-t-4 border-transparent px-4 pt-4 text-sm font-medium text-gray-100 hover:border-gold1 hover:text-gold1"
          >4</a>
          <a
          href="#"
          class="inline-flex items-center border-t-4 border-transparent px-4 pt-4 text-sm font-medium text-gray-100 hover:border-gold1 hover:text-gold1"
          >5</a>
          <a
          href="#"
          class="inline-flex items-center border-t-4 border-transparent px-4 pt-4 text-sm font-medium text-gray-100 hover:border-gold1 hover:text-gold1"
          >6</a>
      </div>
      <div class="-mt-px flex w-0 flex-1 justify-end">
        <a
          href="#"
          class="inline-flex items-center border-t-2 border-transparent pl-1 pt-4 text-sm font-medium text-gold1 hover:border-gray-300 hover:text-gold6"
        >
          بعدی
        </a>
      </div>
    </nav>
      <div
        v-if="openModal"
        class="fixed inset-0 flex items-center justify-center bg-black bg-opacity-50 z-50"
      >
        <div class="bg-white px-8 py-2 rounded-lg w-[90%] max-h-[90vh] overflow-y-auto">
          <div class="flex items-center justify-between py-3">
            <div class="text-gray-600 text-sm">فیلترها</div>
            <button
              @click="openModal = false"
              class="bg-red-500 hover:bg-red-600 text-white w-6 h-6 rounded-full"
            >
              x
            </button>
          </div>
          <div class="text-gray-600 text-sm py-2 mt-5">نوع واگذاری</div>
          <div class="flex gap-3 flex-wrap">
            <button
              v-for="button in buttonsTransfer"
              :key="button.id"
              @click="handleClick(button.id)"
              class="w-24 border border-1 border-green-400 rounded-lg py-1 text-sm"
              :style="{
                backgroundColor: button.id === selectedButtonId ? 'green' : '',
                color: button.id === selectedButtonId ? 'white' : '',
              }"
            >
              {{ button.name }}
            </button>
          </div>
          <div class="text-gray-600 text-sm py-2 mt-5">نوع ملک</div>
          <div class="flex gap-3 flex-wrap">
            <button
              v-for="button in PropertyType"
              :key="button.id"
              @click="handleClick2(button.id)"
              class="w-24 border border-1 border-green-400 rounded-lg py-1 text-sm"
              :style="{
                backgroundColor: button.id === selectedButtonId2 ? 'green' : '',
                color: button.id === selectedButtonId2 ? 'white' : '',
              }"
            >
              {{ button.name }}
            </button>
          </div>
          <div class="text-gray-600 text-sm py-2 mt-5">تعداد اتاق</div>
          <div class="flex gap-3 flex-wrap">
            <button
              v-for="button in numberRooms"
              :key="button.id"
              @click="handleClick3(button.id)"
              class="w-24 border border-1 border-green-400 rounded-lg py-1 text-sm"
              :style="{
                backgroundColor: button.id === selectedButtonId3 ? 'green' : '',
                color: button.id === selectedButtonId3 ? 'white' : '',
              }"
            >
              {{ button.name }}
            </button>
          </div>
  
          <div class="text-gray-600 text-sm py-2 mt-5">متراژ</div>
          <div class="flex gap-3 flex-wrap">
            <div class="relative">
              <label
                for="min-meter"
                class="absolute -top-2 right-2 inline-block bg-white px-1 text-xs font-medium text-gray-900"
                >حداقل متراژ</label
              >
              <input
                type="text"
                name="min-meter"
                id="min-meter"
                class="block pl-2 w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                placeholder=""
                dir="ltr"
              />
            </div>
            <div class="relative">
              <label
                for="max-meter"
                class="absolute -top-2 right-2 inline-block bg-white px-1 text-xs font-medium text-gray-900"
                >حداکثر متراژ</label
              >
              <input
                type="text"
                name="max-meter"
                id="max-meter"
                class="block pl-2 w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                placeholder=""
                dir="ltr"
              />
            </div>
          </div>
          <div class="flex items-center gap-3 mt-5">
            <div class="text-gray-600 text-sm py-2">قیمت توافقی</div>
            <Switch
              v-model="enabled"
              class="group relative inline-flex h-5 w-10 flex-shrink-0 cursor-pointer items-center justify-center rounded-full focus:outline-none focus:ring-2 focus:ring-indigo-600 focus:ring-offset-2"
            >
              <span class="sr-only">Use setting</span>
              <span
                aria-hidden="true"
                class="pointer-events-none absolute h-full w-full rounded-md bg-white"
              />
              <span
                aria-hidden="true"
                :class="[
                  enabled ? 'bg-indigo-600' : 'bg-gray-200',
                  'pointer-events-none absolute mx-auto h-4 w-9 rounded-full transition-colors duration-200 ease-in-out',
                ]"
              />
              <span
                aria-hidden="true"
                :class="[
                  enabled ? 'translate-x-5' : 'translate-x-0',
                  'pointer-events-none absolute left-0 inline-block h-5 w-5 transform rounded-full border border-gray-200 bg-white shadow ring-0 transition-transform duration-200 ease-in-out',
                ]"
              />
            </Switch>
          </div>
          <div v-if="!enabled">
            <div class="text-gray-600 text-sm py-2 mt-5">بازه قیمت</div>
            <div class="flex gap-3 flex-wrap">
              <div class="relative">
                <label
                  for="min-meter"
                  class="absolute -top-2 right-2 inline-block bg-white px-1 text-xs font-medium text-gray-900"
                  >حداقل قیمت</label
                >
                <input
                  type="text"
                  name="min-meter"
                  id="min-meter"
                  class="block pl-2 w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                  placeholder=""
                  dir="ltr"
                />
              </div>
              <div class="relative">
                <label
                  for="max-meter"
                  class="absolute -top-2 right-2 inline-block bg-white px-1 text-xs font-medium text-gray-900"
                  >حداکثر قیمت</label
                >
                <input
                  type="text"
                  name="max-meter"
                  id="max-meter"
                  class="block pl-2 w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                  placeholder=""
                  dir="ltr"
                />
              </div>
            </div>
          </div>
          <div class="flex items-center justify-between py-5">
            <button
              class="bg-red-500 hover:bg-red-600 text-white py-1.5 px-4 rounded-lg"
            >
              پاکسازی
            </button>
            <button
              class="bg-green-500 hover:bg-green-600 text-white py-1.5 px-4 rounded-lg"
            >
              اعمال فیلتر
            </button>
          </div>
        </div>
      </div>
      <div class="w-full h-60"></div>
    </div>
  </template>
  <script>
  import { ref } from "vue";
  import { Switch } from "@headlessui/vue";
  
  const enabled = ref(false);
  
  export default {
    components: {
      Switch,
    },
    setup() {
      const enabled = ref(false);
  
      return {
        enabled,
      };
    },
    data() {
      return {
        openModal: false,
        selectedButtonId: null,
        selectedButtonId2: null,
        selectedButtonId3: null,
        buttonsTransfer: [
          { id: 1, name: "فروش" },
          { id: 2, name: "رهن و اجاره" },
          { id: 3, name: "پیش فروش" },
          { id: 4, name: "مشارکت" },
          { id: 5, name: "تهاتر" },
        ],
        PropertyType: [
          { id: 1, name: "آپارتمان" },
          { id: 2, name: "خانه ویلایی" },
          { id: 3, name: "زمین" },
          { id: 4, name: "کلنگی" },
          { id: 5, name: "مغازه و تجاری" },
          { id: 6, name: "سوییت" },
          { id: 7, name: "سالن" },
          { id: 8, name: "ویلا" },
          { id: 9, name: "دفتر اداری" },
          { id: 10, name: "باغ" },
          { id: 11, name: "انبار" },
          { id: 12, name: "کارگاه" },
          { id: 13, name: "مستغلات" },
          { id: 14, name: "سوله" },
          { id: 15, name: "دامداری" },
          { id: 16, name: "مرغداری" },
          { id: 17, name: "هتل" },
          { id: 18, name: "صنعتی " },
        ],
        numberRooms: [
          { id: 1, name: "بدون اتاق" },
          { id: 2, name: " یک خواب " },
          { id: 3, name: " دو خواب" },
          { id: 4, name: "سه خواب" },
          { id: 5, name: "چهار خواب" },
          { id: 6, name: " 5 خواب به بالا" },
        ],
        products: [
        {
          id: 1,
          title: "اجاره سوله",
          type: "رهن و اجاره",
          dic: "صنعتی ، کشاورزی و تجاری",
          meter: "متراژ 170 متری",
          city: "بجنورد ",
          code: "23456",
          time: "5",
          price: "100",
          price2: "1",
          src: "/img/07.jpg",
        },
        {
          id: 2,
          title: "فروش واحد مسکونی",
          type: "خرید و فروش",
          dic: "فروش واحد مسکونی",
          meter: "متراژ 110 متری",
          city: " بجنورد",
          code: "34567",
          time: "7",
          price: "170",
          price2: "2,300",
          src: "/img/08.jpg",
        },
        {
          id: 3,
          title: "اجاره مسکونی",
          type: "رهن و اجاره",
          dic: "رهن واحد مسکونی",
          meter: "متراژ 115 متری",
          city: "بجنورد",
          code: "987543",
          time: "11",
          price: "1",
          price2: "200",
          src: "/img/09.jpg",
        },
        {
          id: 4,
          title: "اجاره سوله",
          type: "رهن و اجاره",
          dic: "صنعتی ، کشاورزی و تجاری",
          meter: "متراژ 170 متری",
          city: "بجنورد ",
          code: "23456",
          time: "5",
          price: "100",
          price2: "1",
          src: "/img/10.jpg",
        },
        {
          id: 6,
          title: "اجاره مسکونی",
          type: "رهن و اجاره",
          dic: "رهن واحد مسکونی",
          meter: "متراژ 115 متری",
          city: "بجنورد",
          code: "987543",
          time: "11",
          price: "1",
          price2: "200",
          src: "/img/11.jpg",
        },
        {
          id: 5,
          title: "فروش واحد مسکونی",
          type: "خرید و فروش",
          dic: "فروش واحد مسکونی",
          meter: "متراژ 110 متری",
          city: " بجنورد",
          code: "34567",
          time: "7",
          price: "170",
          price2: "2,300",
          src: "/img/12.jpg",
        },
      ],
      };
    },
    methods: {
      handleClick(id) {
        this.selectedButtonId = id;
      
      },
      handleClick2(id) {
        this.selectedButtonId2 = id;
  
      },
      handleClick3(id) {
        this.selectedButtonId3 = id;
      
      },
    },
  };
  </script>
  