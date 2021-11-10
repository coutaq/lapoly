<template>
  <div class="frac">
    {{ num }}
    <hr />
    {{ denom }}
  </div>
</template>

<script>
export default {
  props: ["num", "denom"],
};
</script>

<style>
.frac {
  width: fit-content;
}
</style>