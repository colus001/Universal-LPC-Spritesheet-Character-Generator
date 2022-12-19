<script lang="ts">
	import { afterUpdate } from 'svelte';
	import Container from '../components/Container.svelte';
	import _body from '../sheet_definitions/body.json';
	import _head from '../sheet_definitions/heads_human_male.json';

	let bodyType: string = 'male';
	let bodyColor: string = 'light';
	let canvas: HTMLCanvasElement;

	const bodyTypes = ['male', 'female', 'teen', 'child', 'pregnant', 'muscular'];

	afterUpdate(async () => {
		const context = canvas.getContext('2d');
		if (!context) {
			return;
		}

		context.clearRect(0, 0, canvas.width, canvas.height);

		const body = ['/spritesheets/', (_body.layer_1 as any)[bodyType], bodyColor, '.png'].join('');
		const head = ['/spritesheets/', (_head.layer_1 as any)[bodyType], bodyColor, '.png'].join('');

		[body, head].forEach((url) => {
			loadImage(url).then((img) => {
				context.drawImage(img, 0, 0);
			});
		});
	});

	function loadImage(url: string) {
		return new Promise<HTMLImageElement>((resolve, reject) => {
			const img = new Image();
			img.onload = () => resolve(img);
			img.onerror = () => reject(new Error(`load ${url} fail`));
			img.src = url;
		});
	}
</script>

<Container class="mt-8">
	<section class="flex">
		<ul class="space-y-4">
			<li>
				<h3>Body</h3>
				<ul>
					{#each bodyTypes as type}
						<li>
							<label class="capitalize">
								<input type="radio" name="type" value={type} bind:group={bodyType} />
								{type}
							</label>
						</li>
					{/each}
				</ul>
			</li>
			<li>
				<h3>Body Color</h3>
				<ul>
					{#each _body.variants as variant}
						<li>
							<label class="capitalize">
								<input type="radio" name="sex" value={variant} bind:group={bodyColor} />
								{variant}
							</label>
						</li>
					{/each}
				</ul>
			</li>
		</ul>
		<div>
			<canvas bind:this={canvas} width={832} height={1344}>HTML5 Browser required.</canvas>
		</div>
	</section>
</Container>
