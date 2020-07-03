<script>
	import ProfilePic from "./components/ProfilePic.svelte";
	import FooterMenu from "./components/FooterMenu.svelte";
	let scrolVal = 0
	let nextSection = 1
	let footerMenus = [
			[FooterMenu, "abc"],
			[FooterMenu, "123"],
			[FooterMenu, "r34"],
			[FooterMenu, "4543"]
	]
	let Component = footerMenus[0]
	let onScroll = e=>{
		let st = window.pageYOffset || document.documentElement.scrollTop; // Credits: "https://github.com/qeremy/so/blob/master/so.dom.js#L426"
		if (st > 1){
			// downscroll code
			scrolVal--
			if(scrolVal%30 === 0){
				nextSection--;
				let p = nextSection%footerMenus.length
				console.log(p)
			}
		} else {
			// upscroll code
			scrolVal++
			if(scrolVal%30 === 0){
				nextSection++;
			}
		}
		e.preventDefault();
		Component = footerMenus[Math.abs(nextSection%footerMenus.length)] || footerMenus[0];
		window.scrollTo(0,1);
		// scrolVal = window.scrollY
		// debugger
		// scrolVal++
	};
</script>
<svelte:window  on:scroll={onScroll}/>

<main>
	<div class="intro">
		<h1>Hello! I am Gourav</h1>
		<ProfilePic/>
		{nextSection}
	</div>
	<div class="text"></div>
	<div class="footer">
		<svelte:component this={Component[0]}>{Component[1]}</svelte:component>
	</div>
</main>

<style>
	body{
		overscroll-behavior: none;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 2.5rem;
		font-weight: 100;
	}

	main{
		display: flex;
		justify-content: center;
		flex-direction: column;
	}
	.intro{
		position: fixed;
		display: flex;
		flex-direction: column-reverse;
		top:0vh;
		left: 0vh;
		background-color:#ffffff;
		height:32vh;
		width:100vw;
		transition: 0.3s;
		justify-content: center;
		align-items: center;
	}

	.text{
		margin-top: 33vh;
	}

</style>
