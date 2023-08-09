<script>
	import '../tailwind.css';

	import NativeExpression from '../components/nativeExpression.svelte';
	import WriteTranslation from '../components/writeTranslation.svelte';
	// import { t } from 'vitest/dist/types-198fd1d9';

	// handle the logic behind going from one step to the next:
	let page = 0;
	let nativeExpression = '';
	let translatedExpression = '';

	const possibleLanguages = [
		{ language: 'Afrikaans', shortcode: 'af' },
		{ language: 'Albanian', shortcode: 'sq' },
		{ language: 'Arabic', shortcode: 'ar' },
		{ language: 'Armenian', shortcode: 'hy' },
		{ language: 'Azerbaijani', shortcode: 'az' },
		{ language: 'Basque', shortcode: 'eu' },
		{ language: 'Bengali', shortcode: 'bn' },
		{ language: 'Bosnian', shortcode: 'bs' },
		{ language: 'Bulgarian', shortcode: 'bg' },
		{ language: 'Catalan', shortcode: 'ca' },
		{ language: 'Chinese (Simplified)', shortcode: 'zh-CN' },
		{ language: 'Chinese (Traditional)', shortcode: 'zh-TW' },
		{ language: 'Croatian', shortcode: 'hr' },
		{ language: 'Czech', shortcode: 'cs' },
		{ language: 'Danish', shortcode: 'da' },
		{ language: 'Dutch', shortcode: 'nl' },
		{ language: 'English', shortcode: 'en' },
		{ language: 'Esperanto', shortcode: 'eo' },
		{ language: 'Estonian', shortcode: 'et' },
		{ language: 'Filipino (Tagalog)', shortcode: 'fil' },
		{ language: 'Finnish', shortcode: 'fi' },
		{ language: 'French', shortcode: 'fr' },
		{ language: 'Galician', shortcode: 'gl' },
		{ language: 'German', shortcode: 'de' },
		{ language: 'Greek', shortcode: 'el' },
		{ language: 'Gujarati', shortcode: 'gu' },
		{ language: 'Hebrew', shortcode: 'he' },
		{ language: 'Hindi', shortcode: 'hi' },
		{ language: 'Hungarian', shortcode: 'hu' },
		{ language: 'Icelandic', shortcode: 'is' },
		{ language: 'Indonesian', shortcode: 'id' },
		{ language: 'Italian', shortcode: 'it' },
		{ language: 'Japanese', shortcode: 'ja' },
		{ language: 'Javanese', shortcode: 'jv' },
		{ language: 'Kannada', shortcode: 'kn' },
		{ language: 'Khmer', shortcode: 'km' },
		{ language: 'Korean', shortcode: 'ko' },
		{ language: 'Latvian', shortcode: 'lv' },
		{ language: 'Lithuanian', shortcode: 'lt' },
		{ language: 'Macedonian', shortcode: 'mk' },
		{ language: 'Malay', shortcode: 'ms' },
		{ language: 'Malayalam', shortcode: 'ml' },
		{ language: 'Maltese', shortcode: 'mt' },
		{ language: 'Maori', shortcode: 'mi' },
		{ language: 'Marathi', shortcode: 'mr' },
		{ language: 'Mongolian', shortcode: 'mn' },
		{ language: 'Nepali', shortcode: 'ne' },
		{ language: 'Norwegian', shortcode: 'no' },
		{ language: 'Odia (Oriya)', shortcode: 'or' },
		{ language: 'Pashto', shortcode: 'ps' },
		{ language: 'Persian', shortcode: 'fa' },
		{ language: 'Polish', shortcode: 'pl' },
		{ language: 'Portuguese', shortcode: 'pt' },
		{ language: 'Punjabi', shortcode: 'pa' },
		{ language: 'Romanian', shortcode: 'ro' },
		{ language: 'Russian', shortcode: 'ru' },
		{ language: 'Sanskrit', shortcode: 'sa' },
		{ language: 'Serbian', shortcode: 'sr' },
		{ language: 'Sinhala', shortcode: 'si' },
		{ language: 'Slovak', shortcode: 'sk' },
		{ language: 'Slovenian', shortcode: 'sl' },
		{ language: 'Spanish', shortcode: 'es' },
		{ language: 'Swahili', shortcode: 'sw' },
		{ language: 'Swedish', shortcode: 'sv' },
		{ language: 'Tamil', shortcode: 'ta' },
		{ language: 'Telugu', shortcode: 'te' },
		{ language: 'Thai', shortcode: 'th' },
		{ language: 'Turkish', shortcode: 'tr' },
		{ language: 'Ukrainian', shortcode: 'uk' },
		{ language: 'Urdu', shortcode: 'ur' },
		{ language: 'Uzbek', shortcode: 'uz' },
		{ language: 'Vietnamese', shortcode: 'vi' }
	];

	let nativeLanguage = 'en';
	let targetLanguage = 'es';
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
					<div class="flex gap flex-col items-start">
						<div class="my-2">
							<label for="native-language">Native Language: </label>
							<select
								bind:value="{nativeLanguage}"
								name="native-language"
								id="native-language"
								class="select select-bordered max-w-xs"
							>
								{#each possibleLanguages as lang}
									<option value={lang.shortcode}>
										{lang.language}
									</option>
								{/each}
							</select>
						</div>
						<div class="my-2">
							<label for="target-language">Target Language: </label>
							<select
								bind:value="{targetLanguage}"
								name="target-language"
								id="target-language"
								class="select select-bordered max-w-xs"
							>
								{#each possibleLanguages as lang}
									<option value={lang.shortcode}>
										{lang.language}
									</option>
								{/each}
							</select>
						</div>
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
						href="https://translate.google.com/?sl={nativeLanguage}&tl={targetLanguage}&text={encodeURIComponent(
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

				<ul>
					{#each translatedExpression.split(' ') as word}
						<li class="flex gap">
							<a href="https://forvo.com/search/{word}/">{word}</a>
						</li>
					{/each}
				</ul>

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
					out. Please adjust the depth of your explanations to the complexity of the sentence.
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
				{#each translatedExpression.split(' ') as word}
					<div class="flex gap">
						{word} <input type="text" />
					</div>
				{/each}
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
