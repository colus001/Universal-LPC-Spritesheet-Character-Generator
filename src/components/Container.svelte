<script lang="ts">
	import classNames from 'classnames';

	let className = '';
	export { className as class };
</script>

<div class={classNames('mx-auto max-w-8xl px-4 md:px-8', className)}>
	<slot />
</div>
