<script setup lang="ts">
import { ref } from "vue";
import Tabs from "@/components/organisms/commons/CommonTabs.vue";
import Button from "@/components/atoms/commons/CommonButton.vue";
import Header from "@/components/organisms/commons/CommonHeader.vue";
import SelectBox from "@/components/atoms/commons/CommonSelectBox.vue";
import Footer from "@/components/organisms/commons/CommonFooter.vue";
import RoundedInput from "@/components/atoms/commons/CommonRoundedInput.vue";
import { useRouter } from "vue-router";

const router = useRouter();
const SittingDownGirl = "/icons/SittingDownGirl.svg";
const GirlHavingCookie = "/icons/GirlHavingCookie.svg";

/** status true means you clicked WORKOUT tab */
const isFirstTabClicked = ref(true);

const onClickFirstMenu = (status: any) => {
  isFirstTabClicked.value = status;
};
</script>

<template>
  <Header title="Register your activity" />
  <Tabs
    class="mt-16"
    first-item="WORKOUT"
    second-item="FOODS"
    @isFirstMenuClicked="onClickFirstMenu"
  />
  <div v-if="isFirstTabClicked === true">
    <div class="mt-5 flex items-center mx-8">
      <p>Let’s see how hard you had workout today</p>
      <img :src="SittingDownGirl" alt="" />
    </div>

    <!-- When Workout tab is selected -->
    <main class="px-6 font-sans mt-3 pb-32">
      <div class="text-center">
        <RoundedInput placeholder="Enter the machine" class="my-2" />
        <span class="block font-bold my-3">OR</span>
        <SelectBox
          placeholder="Choose your machine"
          :options="['Push up bar', 'Tread mill', 'Aero bike']"
          class="h-5/6 mb-3"
        />
        <RoundedInput placeholder="Enter the weight" class="my-2" />
        <RoundedInput placeholder="Enter the reps" class="my-2" />
        <RoundedInput placeholder="Enter how long it takes" class="my-2" />
        <Button
          class="bg-primary w-52 text-white mt-5 hover:bg-primary rounded-full"
          label="Done"
          @click="router.push('/login')"
        />
      </div>
    </main>
  </div>

  <div v-if="isFirstTabClicked === false">
    <div class="mt-5 flex items-center mx-8">
      <p>Let’s see the things giving you fat :(</p>
      <img :src="GirlHavingCookie" alt="" />
    </div>

    <!-- When Foods tab is selected -->
    <main class="px-6 font-sans mt-3 pb-32">
      <div class="text-center">
        <SelectBox
          placeholder="Select from templates"
          :options="['Push up bar', 'Tread mill', 'Aero bike']"
          class="h-5/6 my-3"
        />
        <RoundedInput placeholder="Enter the menu" class="my-2" />
        <RoundedInput placeholder="Enter the amount of protein" class="my-2" />
        <RoundedInput placeholder="Enter the amount of fat" class="my-2" />
        <RoundedInput
          placeholder="Enter the amount of carbohydrate"
          class="my-2"
        />
        <RoundedInput placeholder="Enter the cost" class="my-2" type="number" />
        <Button
          class="bg-primary w-52 text-white mt-5 hover:bg-primary rounded-full"
          label="Done"
          @click="router.push('/login')"
        />
      </div>
    </main>
  </div>
  <Footer />
</template>
