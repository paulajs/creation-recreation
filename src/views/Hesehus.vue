<template>
  <div class="case-hesehus">
    <CasesAboveTheFold />
    <CasesResult/>
    <CasesProcess/>
  </div>
</template>
</style>
<script>
import CasesAboveTheFold from "@/components/CasesAboveTheFold.vue";
import CasesResult from "@/components/CasesResult.vue";
import CasesProcess from "@/components/CasesProcess.vue";
export default {
  name: "Hesehus",
  components: {
    CasesAboveTheFold,
    CasesResult,
    CasesProcess
  }
};
</script>
