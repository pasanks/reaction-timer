<template>
  <div class="results">
      <p>Your reaction time is {{ score }} ms.</p>
      <p>Click <b>Start</b> button to calculate again.</p>
  </div>
</template>

<script>
export default {
    props: ['score']
}
</script>
