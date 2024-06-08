<template>
    <div
    class="w-[90%] min-h-[1000px] mx-auto  shadow-lg py-10 px-3 lg:px-28 rounded-xl"
  >
    <div class="flex items-center justify-between">
      <h3 class="flex gap-1 items-center">
        <span class="text-gold1 font-semibold"> ویرایش  فایل </span>
        <span class="text-gold1 font-semibold">⟵</span>
      </h3>
    </div>
    <div class="  py-2 rounded-lg  w-[90%] max-h-[90vh] overflow-y-auto text-gold1">
        
        <div class="mt-6">
          <div class="w-full flex flex-col lg:flex-row gap-3">
            <div class="w-full lg:w-1/3">
              <p class="text-gold1 text-sm py-2">نوع واگذاری</p>
              <select
              v-model="formData.typeOfTransfer"
                class="w-full border border-1 border-gray-500 rounded-lg px-4 py-1"
              >
                <option value="1">فروش</option>
                <option value="2">رهن</option>
                <option value="3">پیش‌فروش</option>
                <option value="4">مشارکت</option>
              </select>
            </div>
            <div class="w-full lg:w-1/3">
              <p class="text-gold1 text-sm py-2">نوع ملک</p>
              <select
                v-model="formData.typeOfHouse"
                class="w-full border border-1 border-gray-500 rounded-lg px-4 py-1"
              >
                <option value="1">خانه ویلایی</option>
                <option value="2">آپارتمان</option>
                <option value="3">زمین</option>
                <option value="4">کلنگی</option>
              </select>
            </div>
            <div class="w-full lg:w-1/3">
              <p class=" text-sm py-2">نوع کاربری</p>
              <select
                v-model="formData.practical"
                class="w-full border border-1 border-gray-500 rounded-lg px-4 py-1"
              >
                <option value="sales">مسکونی</option>
                <option value="mortgage">اداری</option>
                <option value="pre-sale">تجاری</option>
                <option value="partnership">اقامتی</option>
              </select>
            </div>
          </div>
          <div class="w-full flex flex-col lg:flex-row gap-3 mt-3">
            <div class="w-full lg:w-1/3">
              <p class=" text-sm py-2">متراژ</p>
              <input
                type="text"
                v-model="formData.metrage"
                class="w-full border border-1 border-gray-500 rounded-lg px-4 py-1"
                placeholder=""
                dir="ltr"
              />
            </div>
            <div class="w-full lg:w-1/3">
              <p class=" text-sm py-2">قیمت متر مربع (تومان)</p>
              <input
                type="text"
                v-model="formData.priceOfMetrage"
                class="w-full border border-1 border-gray-500 rounded-lg px-4 py-1"
                placeholder=""
                dir="ltr"
              />
            </div>
            <div class="w-full lg:w-1/3">
              <p class=" text-sm py-2">قیمت کل (تومان)</p>
              <input
                type="text"
                v-model="formData.priceOfWhole"
                class="w-full border border-1 border-gray-500 rounded-lg px-4 py-1"
                placeholder=""
                dir="ltr"
              />
            </div>
          </div>
          <div class="w-full flex flex-col lg:flex-row gap-3 mt-3">
            <div class="w-full lg:w-1/3">
              <p class=" text-sm py-2">معاوضه</p>
              <select
              v-model="formData.exchange"
                class="w-full border border-1 border-gray-500 rounded-lg px-4 py-1"
              >
                <option value="1">دارد</option>
                <option value="2">ندارد</option>
              </select>
            </div>
            <div class="w-full lg:w-1/3">
              <p class=" text-sm py-2">وام</p>
              <select
              v-model="formData.loan"
                class="w-full border border-1 border-gray-500 rounded-lg px-4 py-1"
              >
                <option value="1">دارد</option>
                <option value="2">ندارد</option>
              </select>
            </div>
            <div class="w-full lg:w-1/3">
              <p class=" text-sm py-2">مبلغ وام (اگر وام دارد)</p>
              <input
                type="text"
                v-model="formData.priceOfLoan"
                class="w-full border border-1 border-gray-500 rounded-lg px-4 py-1.5"
                placeholder=""
                dir="ltr"
              />
            </div>
          </div>
          <div class="w-full flex flex-col lg:flex-row gap-3 mt-3">
            <div class="w-full lg:w-1/3">
              <p class=" text-sm py-2">استان</p>
              <select
              v-model="formData.state"
                class="w-full border border-1 border-gray-500 rounded-lg px-4 py-1"
              >
                <option value="1">تهران</option>
                <option value="2">مشهد</option>
                <option value="3">خراسان شمالی</option>
                <option value="4">خراسان رضوی</option>
              </select>
            </div>
            <div class="w-full lg:w-1/3">
              <p class=" text-sm py-2">شهر</p>
              <select
              v-model="formData.city"
                class="w-full border border-1 border-gray-500 rounded-lg px-4 py-1"
              >
                <option value="1">بجنورد</option>
                <option value="2">شیروان</option>
                <option value="3">فاروج</option>
                <option value="4">اسفراین</option>
              </select>
            </div>
            <div class="w-full lg:w-1/3">
              <p class=" text-sm py-2">کوچه</p>
              <input
                type="text"
                v-model="formData.address"
                class="w-full border border-1 border-gray-500 rounded-lg px-4 py-1.5"
                placeholder="ادرس ملک"
              />
            </div>
          </div>
          <div class="w-full mt-3">
            <p class=" text-sm py-2">انتخاب تصاویر</p>
            <div class="relative">
              <input
                type="file"
                accept="image/*"
                class="hidden"
                id="imageInput"
                @input="previewImages"
                multiple
              />
              <label for="imageInput" class="w-full h-full cursor-pointer">
                <div
                  class="w-full border border-1 border-gray-500 rounded-lg px-4 py-1 flex items-center justify-between"
                >
                  <span class=" placeholder-[#999]">
                    تصاویر را انتخاب کنید...
                  </span>
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    class="h-5 w-5 text-gray-400"
                    viewBox="0 0 20 20"
                    fill="currentColor"
                  >
                    <path
                      fill-rule="evenodd"
                      d="M12 5l-8 8 1.5 1.5 8-8L18 9l1.5-1.5L12 2z"
                      clip-rule="evenodd"
                    />
                  </svg>
                </div>
              </label>
              <div
                class="mt-2 flex gap-3 items-center border border-1 border-gray-500 rounded-lg p-2"
              >
                <div v-if="images.length > 0" class="flex gap-3 items-center">
                  <img
                    v-for="(image, index) in images"
                    :key="index"
                    :src="image"
                    class="w-[100px] h-16 mr-2"
                  />
                </div>
                <div
                  class="flex items-center justify-center w-full text-sm text-gold1"
                  v-else
                >
                  <p>تصویری انتخاب نشده است.</p>
                </div>
              </div>
            </div>
          </div>
          <div class="w-full mt-3">
            <p class="text-gold1 text-sm py-2">امکانات</p>
            <div class="flex gap-3 flex-wrap">
              <div
                v-for="i in Possibilities"
                :key="i"
                class="flex items-center"
              >
                <label :for="'checkbox-' + i">{{ i }}</label>
                <input type="checkbox" :id="'checkbox-' + i" class="mr-1"  v-model="formData.additionalFeatures" />
              </div>
            </div>
          </div>
          <div class="w-full flex flex-col lg:flex-row gap-3 mt-3">
            <div class="w-full lg:w-1/3">
              <p class="text-gold1 text-sm py-2">نام و نام خانوادگی</p>
              <input
                type="text"
                class="w-full border border-1 border-gray-500 rounded-lg px-4 py-1"
                placeholder=""
                v-model="formData.username"
                dir="ltr"
              />
            </div>
            <div class="w-full lg:w-1/3">
              <p class="text-gold1 text-sm py-2">شماره تماس 1</p>
              <input
                type="text"
                class="w-full border border-1 border-gray-500 rounded-lg px-4 py-1"
                placeholder=""
                dir="ltr"
                v-model="formData.phone1"
              />
            </div>
            <div class="w-full lg:w-1/3">
              <p class="text-gold1 text-sm py-2">شماره تماس 2</p>
              <input
                type="text"
                class="w-full border border-1 border-gray-500 rounded-lg px-4 py-1"
                placeholder=""
                dir="ltr"
                v-model="formData.phone2"
              />
            </div>
          </div>
          <div class="flex items-center justify-end w-full mt-3">
            <button
            @click="submitForm" 
              class="border border-1 border-gold1 rounded-lg px-5 py-2 text-gold1 hover:bg-gold1 hover:text-white text-sm"
            >
              ویرایش فایل
            </button>
          </div>
        </div>
      </div>
    </div>
</template>
<script>


export default {
 
  data() {
    return {
        formData: {
        typeOfTransfer: '',
        typeOfHouse: '',
        practical: '',
        metrage: '',
        priceOfMetrage: '',
        priceOfWhole: '',
        exchange: '',
        loan: '',
        priceOfLoan: '',
        state: '',
        city: '',
        address: '',
        username: '',
          phone1: '',
          phone2: '',
        additionalFeatures: [],
      },
      selectedButtonId: null,
      selectedButtonId2: null,
      selectedButtonId3: null,
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
      additionalFeatures: [
        { value: '1', label: 'پارکینگ' },
        { value: '2', label: 'انباری' },
        { value: '3', label: 'بالکن' },
      ],
      images: [],
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
      Possibilities: [
        "استخر",
        "پارکینگ",
        "انباری",
        "تراس",
        "کابینت",
        "نگهبانی",
        "جکوزی",
        "سونا",
        "دزدگیر",
        "اتاق بازی",
      ],
    };
  },
  methods: {
    previewImages(event) {
      this.images = [];
      const files = event.target.files;
      for (let i = 0; i < files.length; i++) {
        const reader = new FileReader();
        reader.onload = (e) => {
          this.images.push(e.target.result);
        };
        reader.readAsDataURL(files[i]);
      }
    },
    async submitForm() {
  try {
    const formData = new FormData();
    console.log("Initial formData:", this.formData);


    Object.keys(this.formData).forEach(key => {
      if (Array.isArray(this.formData[key])) {
        this.formData[key].forEach(value => {
          console.log(`Appending array item: ${key}[] = ${value}`);
          formData.append(`${key}[]`, value);
        });
      } else {
        
        formData.append(key, this.formData[key]);
      }
    });

    const imageInput = document.getElementById('imageInput');
    if (imageInput && imageInput.files) {
      Array.from(imageInput.files).forEach(file => {
        console.log(`Appending image: ${file.name}`);
        formData.append('images', file);
      });
    }


    const response = await fetch('https://jsonplaceholder.typicode.com/posts', {
      method: 'POST',
      body: formData
    });

    if (!response.ok) {
      throw new Error('Network response was not ok');
    }

    const responseData = await response.json();
    console.log("Response data:", responseData);
    alert('Form submitted successfully!');
  } catch (error) {
    console.error('Error submitting form:', error);
    alert('Error submitting form. Please try again.');
  }
}

  }
};
</script>