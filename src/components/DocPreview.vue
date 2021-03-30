<template>
	<div class="wrapper" v-if="isOpenPopUp">
		<div class="window">
			<p>Document type is {{ docType }}</p>

			<iframe
				v-if="docType === 'pdf'"
				:src="docDetails"
				width="400"
				height="300"
				allowfullscreen
				webkitallowfullscreen
			></iframe>

			<div v-if="docType !== 'pdf'" class="download">
				<p>
					Click <span style="color: blue">Download</span> button below
					to get the document.
				</p>
				<a
					class="button button__download"
					:href="docDetails"
					target="_blank"
					>Download</a
				>
			</div>

			<button class="button button__close" @click="handleCloseWindow">
				Close
			</button>
		</div>
	</div>
	<div class="radio-group">
		<p>Choose document type:</p>
		<div class="form-group">
			<input
				type="radio"
				name="doc-type"
				id="docx"
				value="docx"
				v-model="docType"
			/>
			<label for="docx">docx</label>
		</div>
		<div class="form-group">
			<input
				type="radio"
				name="doc-type"
				id="xlsx"
				value="xlsx"
				v-model="docType"
			/>
			<label for="xlsx">xlsx</label>
		</div>
		<div class="form-group">
			<input
				type="radio"
				name="doc-type"
				id="pptx"
				value="pptx"
				v-model="docType"
			/>
			<label for="pptx">pptx</label>
		</div>
		<div class="form-group">
			<input
				type="radio"
				name="doc-type"
				id="pdf"
				value="pdf"
				v-model="docType"
			/>
			<label for="pdf">pdf</label>
		</div>
	</div>

	<button
		:class="[!docType ? 'button__disabled' : '', 'button button__submit']"
		@click="handleOpenWindow"
		:disabled="!docType"
	>
		Submit
	</button>
</template>

<script>
	// import VueDocPreview from 'vue-doc-preview'

	export default {
		// components: {
		//   VueDocPreview
		// },
		data: function () {
			return {
				isOpenPopUp: false,
				docType: null,
			};
		},
		methods: {
			handleOpenWindow() {
				this.isOpenPopUp = true;
			},
			handleCloseWindow() {
				this.isOpenPopUp = false;
			},
		},
		computed: {
			docDetails() {
				return this.docType === 'pdf'
					? `/ViewerJS/#/doc/Doc.${this.docType}`
					: `/doc/Doc.${this.docType}`;
			},
		},
	};
</script>

<style scoped>
	.wrapper {
		position: absolute;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
		background-color: rgba(0, 0, 0, 0.5);
		display: flex;
		justify-content: center;
		align-items: center;
		min-height: 100vh;
	}

	.window {
		display: grid;
		gap: 1rem;
		padding: 1rem;
		background-color: white;
		width: 30rem;
	}

	.download {
		display: grid;
		gap: 0.5rem;
	}

	.radio-group {
		margin-top: 2rem;
		display: grid;
		gap: 0.5rem;
	}

	input[type='radio'],
	label {
		cursor: pointer;
	}

	label {
		margin-left: 0.5rem;
	}

	.button {
		padding: 0.5rem 1rem;
		border: none;
		border-radius: 0.25rem;
		cursor: pointer;
		color: white;
	}

	.button__disabled {
		cursor: not-allowed;
		opacity: 0.5;
	}

	.button__submit {
		margin-top: 1rem;
		background-color: green;
	}

	.button__close {
		background-color: red;
	}

	.button__download {
		text-decoration: none;
		background-color: blue;
		text-align: center;
	}
</style>
