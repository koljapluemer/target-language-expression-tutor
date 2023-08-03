<script>
  import NativeExpression from '../components/nativeExpression.svelte';
  import WriteTranslation from '../components/writeTranslation.svelte';

  let currentStep = 1;

  function goToNextStep() {
    // ...
  }

  function goToPreviousStep() {
    // ...
  }
</script>

<main>
  {#if currentStep === 1}
    <NativeExpression />
  {:else if currentStep === 2}
    <WriteTranslation />
  {/if}

  <!-- <button on:click={goToPreviousStep} disabled={currentStep === 1}>
    Previous
  </button>
  <button on:click={goToNextStep} disabled={currentStep === totalSteps}>
    Next
  </button> -->
</main>
