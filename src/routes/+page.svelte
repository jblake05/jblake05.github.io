<script>
	import { goto } from '$app/navigation';

	$: outerWidth = 0
	$: innerWidth = 0
	$: outerHeight = 0
	$: innerHeight = 0

	$: musicPoints = `0,0 0,${innerHeight} ${innerWidth/2},${innerHeight}`
	$: musicStyle = "fill:#b544dd;"
	const musicRoute = () => {
		goto('/music');
	}

    $: aboutPoints = `${innerWidth},0 ${innerWidth},${innerHeight} ${innerWidth/2},${innerHeight}`
    $: aboutStyle = "fill:yellow;"
    const aboutRoute = () => {
        goto('/about');
    }
	// export let musicPoints = `0,0 0,${innerHeight} ${innerWidth/3},${innerHeight}`
	// ^ undefined currently........ and not bound to changes later in the code.....
	// export let musicPoints = `0,0 0,100 100,100`

</script>

<svelte:window bind:innerWidth bind:outerWidth bind:innerHeight bind:outerHeight/>
<!-- <div bind:this={musicPoints}/> -->

<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<svg width={innerWidth} height={innerHeight}>
	<polygon points={musicPoints} 
	on:click={musicRoute} 
	on:mouseenter={() => {
		musicStyle = "fill:#9d08d3;"
	}} 
	on:mouseleave={() => {
		musicStyle="fill:#b544dd;"
	}}
	style={musicStyle}
	/>

	<a href="/music">
		<text x="12.5%" y="50%" dominant-baseline="middle" text-anchor="middle" fill="black">
			music
		</text>
	</a>

    <polygon points={aboutPoints}
    on:click={aboutRoute}
    on:mouseenter={() => {
        aboutStyle = "fill:orange;"
    }}
    on:mouseleave={() => {
        aboutStyle="fill:yellow;"
    }}
    style={aboutStyle}
    />

    <a href="/about">
		<text x="87.5%" y="50%" dominant-baseline="middle" text-anchor="middle" fill="black">
			about
		</text>
	</a>

    <a href="/programming">
        <text x="50%" y="50%" dominant-baseline="middle" text-anchor="middle" fill="black">
			programming
		</text>
    </a>

</svg>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<!-- <svg x="50%" width={innerWidth} height={innerHeight} style="z-index:-95">


</svg> -->

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