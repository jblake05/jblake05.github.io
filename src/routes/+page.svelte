<script>
	import { goto } from '$app/navigation';

	$: outerWidth = 0
	$: innerWidth = 0
	$: outerHeight = 0
	$: innerHeight = 0

	$: musicPoints = `0,0 0,${innerHeight} ${innerWidth/2},${innerHeight}`
	$: musicStyle = "fill:purple;"
	const musicRoute = () => {
		goto('/music');
	}
	// export let musicPoints = `0,0 0,${innerHeight} ${innerWidth/3},${innerHeight}`
	// ^ undefined currently........ and not bound to changes later in the code.....
	// export let musicPoints = `0,0 0,100 100,100`

</script>

<svelte:window bind:innerWidth bind:outerWidth bind:innerHeight bind:outerHeight/>
<!-- <div bind:this={musicPoints}/> -->

<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<svg width={innerWidth/2} height={innerHeight}>
	<!-- <nav> -->

		<!-- <a href="/">home</a> -->
		<!-- <a href="/music">music</a> -->
		<!-- <a href="/programming">programming</a> -->
		<!-- <a href="/about">about</a> -->
	<!-- </nav> -->

	<polygon points={musicPoints} 
	on:click={musicRoute} 
	on:mouseenter={() => {
		musicStyle = "fill:blue;"
	}} 
	on:mouseleave={() => {
		musicStyle="fill:purple;"
	}}
	style={musicStyle}
	/>

	<a href="/music">
		<text x="12.5%" y="50%" dominant-baseline="middle" text-anchor="middle" fill="black">
			music
		</text>
	</a>
</svg>

<slot></slot>

<style>
	svg {
		z-index:-100;
	}

	text {
		font-size: 25px;
	}

	a {
		color:black;
		width:200px;
		height:200px;
		position:absolute;
		top:250px;
		left:100px;
	}
	/* nav {
		border-width:1px 0;
		list-style:none;
		margin:0;
		padding:0;
		position:relative;
		/* height:100px;
	}
	 */
</style>