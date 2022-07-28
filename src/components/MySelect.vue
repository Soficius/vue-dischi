<template>
  <select :name="name" :id="id" class="fw-bolder h-50 me-3" :value="value" @input="$emit('input', $event.target.value)">
    <option value="" selected>{{ placeholder || 'Scegli un opzione' }}</option>
    <option v-for="opt in options" :key="opt.key" :value="opt.value">{{opt.desc}}</option>
  </select>
</template>

<script>
export default {
  name: 'MySelect',
  props: ['name', 'id', 'value', 'options', 'placeholder']
}

</script>

<style></style>
