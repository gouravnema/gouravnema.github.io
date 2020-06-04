<script>
	import ProfilePic from "./components/ProfilePic.svelte";
</script>

<main>
	<div class="intro">
		<h1>Hello {name}! I am Gourav</h1>
		<ProfilePic/>
	</div>

</main>

<style>

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	main{
		display: flex;
		justify-content: center;
	}
	.intro{
		display: flex;
		flex-direction: column-reverse;
		align-items: center;
	}

</style>
