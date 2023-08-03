<script>
	import '../tailwind.css';

	import NativeExpression from '../components/nativeExpression.svelte';
	import WriteTranslation from '../components/writeTranslation.svelte';
</script>

<main class="text-center container card p">
    <div class="card w-96 bg-base-100 shadow-xl">
        <figure><img src="/images/stock/photo-1606107557195-0e29a4b5b4aa.jpg" alt="Shoes" /></figure>
        <div class="card-body">
          <h2 class="card-title">Shoes!</h2>
          <p>If a dog chews shoes whose shoes does he choose?</p>
          <div class="card-actions justify-end">
            <button class="btn btn-primary">Buy Now</button>
          </div>
        </div>
      </div>

	<ul data-role="tabs" data-expand="true" id="tabs">
		<li><a href="#_target_1">Initial Settings</a></li>
		<li><a href="#_target_2">Image Prompt</a></li>
		<li><a href="#_target_3">Translation Attempt</a></li>
		<li><a href="#_target_4">Automatic Translation</a></li>
		<li><a href="#_target_5">Write it</a></li>
		<li><a href="#_target_6">Explanation</a></li>
		<li><a href="#_target_7">Pronounciation</a></li>
		<li><a href="#_target_8">Vocabulary</a></li>
		<li><a href="#_target_9">Check</a></li>
	</ul>
	<div class="border bd-default no-border-top p-2">
		<div id="_target_1">
			<div class="">
				<label for="native-language">Native Language</label>
				<select name="native-language" id="native-language">
					<option value="English">English</option>
				</select>
			</div>
			<div class="">
				<label for="target-language">Target Language</label>
				<select name="target-language" id="target-language">
					<option value="Japanese">Arabic</option>
				</select>
			</div>
		</div>
		<div id="_target_2">The shield is a post-apocalyptic nanomachine.</div>
		<div id="_target_3">Cream soup is just not the same without basil</div>
	</div>
	<!-- {#if currentStep === 1}
		<NativeExpression />
	{:else if currentStep === 2}
		<WriteTranslation />
	{/if} -->

	<!-- <button on:click={goToPreviousStep} disabled={currentStep === 1}>
    Previous
  </button>
  <button on:click={goToNextStep} disabled={currentStep === totalSteps}>
    Next
  </button> -->
</main>
