<script>
	import '../app.css';
	import Container from '../components/Container.svelte';
</script>

<form id="customizeChar">
	<Container>
		<div id="controls">
			<h1>Universal LPC Spritesheet Generator</h1>
			<p>
				Free/Libre pixel art sprites from the <a href="lpc.opengameart.org">Liberated Pixel Cup</a>
				and <a href="https://opengameart.org/content/lpc-collection">OpenGameArt.org</a>. License:
				<a href="https://creativecommons.org/licenses/by-sa/3.0/">CC-BY-SA 3.0</a>. You must
				<a id="scroll-to-credits" href="#">credit the authors of this artwork.</a>
			</p>
			<div>
				<label class="control-label">Download:</label>
				<a id="saveAsPNG"><input type="button" value="Image (PNG)" /></a>
				<button type="button" class="generateSheetCreditsTxt">Credits (text)</button>
				<button type="button" class="generateSheetCreditsCsv">Credits (CSV)</button>
			</div>
			<div>
				<label class="control-label">Edit:</label>
				<button type="button" id="resetAll">Reset all</button>
				<button type="button" class="replacePinkMask">Replace Mask (pink)</button>
			</div>
			<div>
				<label class="control-label">View:</label>
				<button type="button" id="collapse">Collapse All</button>
				<button type="button" id="expand">Expand Selected</button>
				<label for="displayMode-compact"
					><input type="checkbox" name="displayMode" value="compact" id="displayMode-compact" /> Compact
					Display</label
				>
			</div>
			<div>
				<label class="control-label" for="searchbox">Search: </label><input
					type="search"
					id="searchbox"
					name=""
					placeholder="Search"
				/>
			</div>
		</div>
	</Container>

	<slot />
</form>
