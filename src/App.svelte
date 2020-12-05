<script>
	import "https://cdn.jsdelivr.net/npm/@tensorflow/tfjs";
   	import "https://cdn.jsdelivr.net/npm/@tensorflow-models/mobilenet";
	import  "https://cdn.jsdelivr.net/npm/@tensorflow/tf.min.js.map";
	let predictions;
	let buttonname = "開始";
	async function test(){
		buttonname = "読み込み中";
		const version = 2;
		const alpha = 0.5;
		const img = document.getElementById('img');
		
		// Load the model.
		const model = await mobilenet.load();
		
		// Classify the image.
		predictions = await model.classify(img,5);
		
		console.log('Predictions: ');
		console.log("test");
		console.log(predictions[0].className);
		buttonname = "終了";
	}
</script>
<img id="img" src="img2.jpeg" height="300hw">
<button on:click={test}>{buttonname}</button>
{#if predictions}
	{#each predictions as p,i}
		<p>結果{i+1}  = {p.className}</p>
	{/each}
{/if}
