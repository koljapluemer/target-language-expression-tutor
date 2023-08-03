<script>
	import '../tailwind.css';

	import NativeExpression from '../components/nativeExpression.svelte';
	import WriteTranslation from '../components/writeTranslation.svelte';
</script>

<main class="text-center container p">
	<div class="card w-96 bg-base-100 shadow-xl">
		<div class="card-body">
			<h2 class="card-title">Initial Settings</h2>
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
			<div class="card-actions justify-end">
				<button class="btn btn-primary">Next Step</button>
			</div>
		</div>
	</div>

	<div class="card w-96 bg-base-100 shadow-xl">
		<div class="card-body">
			<h2 class="card-title">Image Prompt</h2>
			<p>Write something that comes to mind when seeing this image</p>
			<div class="card-actions justify-end">
				<button class="btn btn-primary">Next Step</button>
			</div>
		</div>
	</div>

    <div class="card w-96 bg-base-100 shadow-xl">
		<div class="card-body">
			<h2 class="card-title">Translation Attempt</h2>
			<p>Try to translate the sentence by yourself. Give it your best shot!</p>
            <textarea name="" id="" cols="100" rows="10"></textarea>
            <small>You don't have to put your translation here, you can also write it by hand</small>
			<div class="card-actions justify-end">
				<button class="btn btn-primary">Next Step</button>
			</div>
		</div>
	</div>

    <div class="card w-96 bg-base-100 shadow-xl">
		<div class="card-body">
			<h2 class="card-title">Automatic Translation</h2>
			<p>Check out the automatic translation of the sentence. I recommend the following steps:</p>
            <ul>
                <li>Compare with your own attempt.</li>
                <li>Listen.</li>
            </ul>
            <p>
                Afterwards, please copy the translated sentence here:
            </p>
			<div class="card-actions justify-end">
				<button class="btn btn-primary">Next Step</button>
			</div>
		</div>
	</div>

    <div class="card w-96 bg-base-100 shadow-xl">
		<div class="card-body">
			<h2 class="card-title">Write it</h2>
			<p>Copy the translated sentence (either per hand or in the input box below)</p>
			<div class="card-actions justify-end">
				<button class="btn btn-primary">Next Step</button>
			</div>
		</div>
	</div>

    <div class="card w-96 bg-base-100 shadow-xl">
		<div class="card-body">
			<h2 class="card-title">Pronounciation</h2>
			<p>Dive deeper into the pronounciation of each word by checking out the links below</p>
			<div class="card-actions justify-end">
				<button class="btn btn-primary">Next Step</button>
			</div>
		</div>
	</div>

    <div class="card w-96 bg-base-100 shadow-xl">
		<div class="card-body">
			<h2 class="card-title">Explanation</h2>
			<p>Copy the following prompt into ChatGPT. Take a minute to read it</p>
			<div class="card-actions justify-end">
				<button class="btn btn-primary">Next Step</button>
			</div>
		</div>
	</div>

    <div class="card w-96 bg-base-100 shadow-xl">
		<div class="card-body">
			<h2 class="card-title">Vocabulary</h2>
			<p>Do you still remember the words? You may write the answer in the input field (or not).</p>
			<div class="card-actions justify-end">
				<button class="btn btn-primary">Next Step</button>
			</div>
		</div>
	</div>

    <div class="card w-96 bg-base-100 shadow-xl">
		<div class="card-body">
			<h2 class="card-title">optional: Flashcards</h2>
			<p>Copy the following prompt into ChatGPT to generate learning cards. These will be used to solidy the learned material for the rest of the session, and you can download the flashcards at the end.</p>
			<div class="card-actions justify-end">
				<button class="btn btn-primary">Next Step</button>
			</div>
		</div>
	</div>

    <div class="card w-96 bg-base-100 shadow-xl">
		<div class="card-body">
			<h2 class="card-title">Reflect</h2>
			<p>Take a minute to reflect on what you learned in this run. Maybe there is something you want to note down?</p>
			<div class="card-actions justify-end">
				<button class="btn btn-primary">New Prompt</button>
			</div>
		</div>
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
