<script setup lang="ts">
import { LLMOS } from '@/config/schemas';

const mgmt = useManagementStore();
const localCluster = await mgmt.find(LLMOS.MANAGEMENT.CLUSTER, "local")
console.log(localCluster)
const clusterInfo = localCluster.status?.version
console.log(localCluster.id)
</script>

<template>
  <div class="p-3">
    <h1 class="font-semibold text-2xl text-gray-900 dark:text-white leading-tight py-2">
      LLMOS Dashboard
    </h1>
    <UDivider class="my-2" />

    <div class="flex gap-3">
      <span>Name:</span>{{ localCluster.metadata.name }}
      <span>Architecture:</span>{{ clusterInfo.platform }}
      <span>Created:</span>{{ localCluster.metadata.creationTimestamp }}
    </div>

    <UDivider class="my-2" />
  </div>
</template>
