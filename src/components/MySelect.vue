<template>
  <select name="" id="" class="fw-bolder h-50 me-3" v-bind:value="value"
    v-on:input="$emit('input', $event.target.value)">
    <option v-if="showEmpty === true" value="__empty" selected>{{labelEmpty}}</option>
    <option v-for="opt in options" :key="opt.key" :value="opt.value">{{opt.desc}}</option>
  </select>
</template>

<script>
export default {
  name: 'MySelect',
  props: ['value', 'options', 'showEmpty', 'labelEmpty']
}

</script>

<style></style>
