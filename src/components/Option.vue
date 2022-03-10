<template>
  <div>
    <p> {{ answer }} {{ title }}</p>
  </div>
</template>

<script>

  export default {
    name: 'Option',
    props: {
      title: '',
      answer: 0,
    }
  }

</script>