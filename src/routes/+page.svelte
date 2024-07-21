<script>
	import { goto } from '$app/navigation';

	$: outerWidth = 0
	$: innerWidth = 0
	$: outerHeight = 0
	$: innerHeight = 0

	$: musicPoints = `0,0 0,${innerHeight} ${innerWidth/2},${innerHeight}`
	$: musicStyle = "fill:#f2596d;"
	const musicRoute = () => {
		goto('/music');
	}

    $: aboutPoints = `${innerWidth},0 ${innerWidth},${innerHeight} ${innerWidth/2},${innerHeight}`
    $: aboutStyle = "fill:#fcee58;"
    const aboutRoute = () => {
        goto('/about');
    }

	$: progPoints = `0,0 ${innerWidth/2},${innerHeight} ${innerWidth},0`
	$: progStyle = "fill:#fc7efa;"
	const progRoute = () => {
		goto('/programming');
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

	<!-- MUSIC -->
	<polygon points={musicPoints} 
	on:click={musicRoute} 
	on:mouseenter={() => {
		// musicStyle = "fill:#9d08d3;"
		musicStyle="fill:#9875f9;"

	}} 
	on:mouseleave={() => {
		musicStyle="fill:#f2596d;"
	}}
	style={musicStyle}
	/>

	<a href="/music"
	on:mouseenter={() => {
		musicStyle = "fill:#9875f9;"
	}}>
		<text x="12.5%" y="50%" dominant-baseline="middle" text-anchor="middle" fill="black">
			music
		</text>
	</a>

	<!-- ABOUT -->
    <polygon points={aboutPoints}
    on:click={aboutRoute}
    on:mouseenter={() => {
        aboutStyle = "fill:#fc9c58;"
    }}
    on:mouseleave={() => {
        aboutStyle="fill:#fcee58;"
    }}
    style={aboutStyle}
    />

    <a href="/about"
	on:mouseenter={() => {
		 aboutStyle = "fill:#fc9c58;"
	}}>
		<text x="87.5%" y="50%" dominant-baseline="middle" text-anchor="middle" fill="black">
			about
		</text>
	</a>


	<!-- PROGRAMMING -->
	<polygon points={progPoints}
	on:click={progRoute}
	on:mouseenter={() => {
		progStyle = "fill:#79e080;"
	}}
	on:mouseleave={() => {
		progStyle = "fill:#fc7efa;"
	}}
	style={progStyle}
	/>

    <a href="/programming"
	on:mouseenter={() => {
		progStyle = "fill:#79e080;"
	}}>
        <text x="50%" y="50%" dominant-baseline="middle" text-anchor="middle" fill="black">
			programming
		</text>
    </a>

</svg>

<style>
	polygon {
		stroke: black;
		stroke-width: 3px;
		stroke-opacity: 20%;
	}	

	text {
		/* font-family: 'Courier New', Courier, monospace; */
		font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
		font-weight: 350;
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