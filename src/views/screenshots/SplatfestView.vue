<template>
  <ScreenshotLayout header="Splatfest">
    <div class="grow flex items-center justify-center" v-if="festival">
      <div class="flex space-x-32 items-center mx-6">
        <SplatfestBox
          :festival="festival"
          class="flex-1 max-w-md md:-rotate-1 scale-[1.2]"
          />

        <SplatfestResultsBox v-if="festival.hasResults" :festival="festival"
          class="max-w-md md:rotate-1 scale-[1.2]" />
      </div>
    </div>
  </ScreenshotLayout>
</template>

<script setup>
import ScreenshotLayout from '../../layouts/ScreenshotLayout.vue';

import { useUSSplatfestsStore } from '@/stores/splatfests';
import SplatfestBox from '@/components/SplatfestBox.vue';
import SplatfestResultsBox from '@/components/SplatfestResultsBox.vue';
import { computed } from 'vue';
const usSplatfests = useUSSplatfestsStore();

const festival = computed(() => usSplatfests.activeFestival ?? usSplatfests.recentFestival);
</script>
