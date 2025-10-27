<script>
	import questions from "$lib/questions";

	let randomQuestion = $state(Math.floor(Math.random() * questions.length));
	let doneQuestions = [];
	let questionJSON = $derived(questions[randomQuestion]);

	function questionSelected(optionIndex) {
		return () => {
			if (questionJSON.answer === optionIndex) {
				alert("Correct!");
			} else {
				alert(`Incorrect! You can do the quiz again after finishing all questions.`);
			}
			doneQuestions.push(randomQuestion);
			if (doneQuestions.length === questions.length) {
				alert("You've completed all the questions!");
				doneQuestions = [];
			}
			do {
				randomQuestion = Math.floor(Math.random() * questions.length);
			} while (doneQuestions.includes(randomQuestion));
			questionJSON = questions[randomQuestion];
		};
	}
</script>

<sveltekit:head>
	<title>BoomBox - Record</title>
	<meta name="description" content="BoomBox - Recorder, but not a recorder" />
</sveltekit:head>
<div class="@container flex flex-col">
	<header class="@container/header text-center text-red-950">
		<h1 class="text-4xl md:text-5xl">BoomBox - Record</h1>
		<h3 class="text-2xl md:text-3xl">This ain't a recorder</h3>
		<h3 class="text-2xl md:text-3xl">Yeahhhh, good luck mate 🇬🇧</h3>
	</header>
	<main class="text-center">
		<h2 class="my-10 text-3xl text-red-950 md:text-4xl">{questionJSON.question}</h2>
		<div class="@container/options my-auto flex flex-col">
			<button
				class="mx-auto my-2 max-w-fit rounded-2xl bg-purple-600 p-4 text-2xl text-red-950 md:text-3xl"
				onclick={questionSelected(0)}
			>
				{questionJSON.options[0]}
			</button>
			<button
				class="mx-auto my-2 max-w-fit rounded-2xl bg-purple-600 p-4 text-2xl text-red-950 md:text-3xl"
				onclick={questionSelected(1)}
			>
				{questionJSON.options[1]}
			</button>
			<button
				class="mx-auto my-2 max-w-fit rounded-2xl bg-purple-600 p-4 text-2xl text-red-950 md:text-3xl"
				onclick={questionSelected(2)}
			>
				{questionJSON.options[2]}
			</button>
			<button
				class="mx-auto my-2 max-w-fit rounded-2xl bg-purple-600 p-4 text-2xl text-red-950 md:text-3xl"
				onclick={questionSelected(3)}
			>
				{questionJSON.options[3]}
			</button>
		</div>
	</main>
</div>
