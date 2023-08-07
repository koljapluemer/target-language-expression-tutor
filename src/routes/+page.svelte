<script>
	import '../tailwind.css';

	import NativeExpression from '../components/nativeExpression.svelte';
	import WriteTranslation from '../components/writeTranslation.svelte';
	// import { t } from 'vitest/dist/types-198fd1d9';

	// handle the logic behind going from one step to the next:
	let page = 0;
	let nativeExpression = '';
	let translatedExpression = '';
</script>

<main class="text-center p flex flex-col items-center">
	<ul class="steps">
		<li class={page >= 0 ? 'step step-primary' : 'step'}>Initial Settings</li>
		<li class={page >= 1 ? 'step step-primary' : 'step'}>Image Prompt</li>
		<li class={page >= 2 ? 'step step-primary' : 'step'}>Translation Attempt</li>
		<li class={page >= 3 ? 'step step-primary' : 'step'}>Automatic Translation</li>
		<li class={page >= 4 ? 'step step-primary' : 'step'}>Write it</li>
		<li class={page >= 5 ? 'step step-primary' : 'step'}>Pronounciation</li>
		<li class={page >= 6 ? 'step step-primary' : 'step'}>Explanation</li>
		<li class={page >= 7 ? 'step step-primary' : 'step'}>Vocabulary</li>
		<li class={page >= 8 ? 'step step-primary' : 'step'}>Grammar</li>
	</ul>

	{#if page === 0}
		<div class="card w-2/3 p4 mt-5 bg-base-100 shadow-xl">
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
					<button
						on:click={() => {
							page += 1;
						}}
						class="btn">Next Step</button
					>
				</div>
			</div>
		</div>
	{/if}
	{#if page === 1}
		<div class="card w-2/3 p4 mt-5 bg-base-100 shadow-xl">
			<div class="card-body">
				<h2 class="card-title">Image Prompt</h2>
				<p>
					Write down something that comes to mind when seeing this image. Please use your <em
						>native language</em
					>. There is no right or wrong.
				</p>
				<img src="https://picsum.photos/300" alt="Random Stockphoto" width="300" height="300" />
				<textarea name="" id="" cols="30" rows="10" bind:value={nativeExpression} />
				<div class="card-actions justify-end">
					<button
						on:click={() => {
							page += 1;
						}}
						class="btn">Next Step</button
					>
				</div>
			</div>
		</div>
	{/if}
	{#if page === 2}
		<div class="card w-2/3 p4 mt-5 bg-base-100 shadow-xl">
			<div class="card-body">
				<h2 class="card-title">Translation Attempt</h2>
				<p>Try to translate the sentence by yourself. Give it your best shot!</p>
				<em>{nativeExpression}</em>
				<textarea name="" id="" cols="100" rows="10" />
				<small>You don't have to put your translation here, you can also write it by hand</small>
				<div class="card-actions justify-end">
					<button
						on:click={() => {
							page += 1;
						}}
						class="btn">Next Step</button
					>
				</div>
			</div>
		</div>
	{/if}
	{#if page === 3}
		<div class="card w-2/3 p4 mt-5 bg-base-100 shadow-xl">
			<div class="card-body">
				<h2 class="card-title">Automatic Translation</h2>
				<p>Check out the automatic translation of the sentence. I recommend the following steps:</p>
				<h3>
					<a
						class="btn btn-primary"
						href="https://translate.google.com/?sl=en&tl=ar&text={encodeURIComponent(
							nativeExpression
						)}%20&op=translate"
						target="_blank">Google Translate Attempt</a
					>
				</h3>
				<ul>
					<li>Compare with your own attempt.</li>
					<li>Listen.</li>
				</ul>
				<p>Afterwards, please copy the translated sentence here:</p>
				<input type="text" bind:value={translatedExpression} />
				<div class="card-actions justify-end">
					<button
						on:click={() => {
							page += 1;
						}}
						class="btn">Next Step</button
					>
				</div>
			</div>
		</div>
	{/if}
	{#if page === 4}
		<div class="card w-2/3 p4 mt-5 bg-base-100 shadow-xl">
			<div class="card-body">
				<h2 class="card-title">Write it</h2>
				<p>Copy the translated sentence (either per hand or in the input box below)</p>
				<div class="card-actions justify-end">
					<button
						on:click={() => {
							page += 1;
						}}
						class="btn">Next Step</button
					>
				</div>
			</div>
		</div>
	{/if}
	{#if page === 5}
		<div class="card w-2/3 p4 mt-5 bg-base-100 shadow-xl">
			<div class="card-body">
				<h2 class="card-title">Pronounciation</h2>
				<p>Dive deeper into the pronounciation of each word by checking out the links below</p>
				<div class="card-actions justify-end">
					<button
						on:click={() => {
							page += 1;
						}}
						class="btn">Next Step</button
					>
				</div>
			</div>
		</div>
	{/if}
	{#if page === 6}
		<div class="card w-2/3 p4 mt-5 bg-base-100 shadow-xl">
			<div class="card-body">
				<h2 class="card-title">Explanation</h2>
				<p>Copy the following prompt into ChatGPT. Take a minute to read it</p>
				<code>
					You are an Arabic teacher, I am your pupil. I translated "{nativeExpression}" to "{translatedExpression}".
					Explain me the sentence, the words in it and grammatical structures. If there are special
					constructions, snares, common confusion or other interesting things, please point them
					out. Please adjust the depth of your explanations to the complexity of the
					sentence.
				</code>
				<div class="card-actions justify-end">
					<button
						on:click={() => {
							page += 1;
						}}
						class="btn">Next Step</button
					>
				</div>
			</div>
		</div>
	{/if}
	{#if page === 7}
		<div class="card w-2/3 p4 mt-5 bg-base-100 shadow-xl">
			<div class="card-body">
				<h2 class="card-title">Vocabulary</h2>
				<p>
					Do you still remember the words? You may write the answer in the input field (or not).
				</p>
				<div class="card-actions justify-end">
					<button
						on:click={() => {
							page += 1;
						}}
						class="btn">Next Step</button
					>
				</div>
			</div>
		</div>
	{/if}
	{#if page === 8}
		<div class="card w-2/3 p4 mt-5 bg-base-100 shadow-xl">
			<div class="card-body">
				<h2 class="card-title">optional: Flashcards</h2>
				<p>
					Copy the following prompt into ChatGPT to generate learning cards. These will be used to
					solidy the learned material for the rest of the session, and you can download the
					flashcards at the end.
				</p>
				<div class="card-actions justify-end">
					<button
						on:click={() => {
							page += 1;
						}}
						class="btn">Next Step</button
					>
				</div>
			</div>
		</div>
	{/if}
	{#if page === 9}
		<div class="card w-2/3 p4 mt-5 bg-base-100 shadow-xl">
			<div class="card-body">
				<h2 class="card-title">Reflect</h2>
				<p>
					Take a minute to reflect on what you learned in this run. Maybe there is something you
					want to note down?
				</p>
				<div class="card-actions justify-end">
					<button
						on:click={() => {
							page = 1;
						}}
						class="btn">New Prompt</button
					>
				</div>
			</div>
		</div>
	{/if}
</main>
