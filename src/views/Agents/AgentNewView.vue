<script setup lang="ts">
import { Icon } from "@iconify/vue";
import AgentForm from "@/components/agent/AgentForm.vue";
import type { CreateAgent } from "@/types/Agents";
import { useRouter } from "vue-router";

const router = useRouter();

// TODO save to backend
const createNewAgent = (data: CreateAgent) => {
  console.log(data);
  router.push({ name: "agent-list" });
};
</script>

<template>
  <div class="shadow-common bg-white rounded-[15px] min-h-full p-4">
    <!-- heading -->
    <div class="flex items-center justify-between mb-4">
      <div
        class="flex items-center gap-2 cursor-pointer hover:text-primary"
        @click="$router.push({ name: 'agent-list' })"
      >
        <Icon icon="mdi:arrow-left" class="text-[2rem]" />
        <span class="text-xl font-medium">New Agent</span>
      </div>
    </div>
    <div class="max-w-xl pl-2">
      <!-- can assert -->
      <AgentForm
        @submit="(data) => createNewAgent(data as CreateAgent)"
        @cancel="router.push({ name: 'agent-list' })"
      />
    </div>
  </div>
</template>
