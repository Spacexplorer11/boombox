<script>
	import questions from "$lib/questions";
	import { onMount } from "svelte";

	let randomQuestion = $state(Math.floor(Math.random() * questions.length));
	let doneQuestions = [];
	let questionJSON = $derived(questions[randomQuestion]);

	let score = $state(0);

	let questionsElement = "";
	let optionsElement = "";
	let finishedElement = "";
	let option1Element = "";
	let option2Element = "";
	let option3Element = "";
	let option4Element = "";

	function questionSelected(optionIndex) {
		return () => {
			if (questionJSON.answer === optionIndex) {
				score += 1;
				if (optionIndex === 0) {
					option1Element.style.backgroundColor = "green";
				}
				if (optionIndex === 1) {
					option2Element.style.backgroundColor = "green";
				}
				if (optionIndex === 2) {
					option3Element.style.backgroundColor = "green";
				}
				if (optionIndex === 3) {
					option4Element.style.backgroundColor = "green";
				}
			} else {
				alert(`Incorrect! You can do the quiz again after finishing all questions.`);
			}
			doneQuestions.push(randomQuestion);

			if (doneQuestions.length === questions.length) {
				setTimeout(() => {
					questionsElement.hidden = "hidden";
					optionsElement.hidden = "hidden";
					finishedElement.hidden = "";
					option1Element.style.backgroundColor = "#9810fa";
					option2Element.style.backgroundColor = "#9810fa";
					option3Element.style.backgroundColor = "#9810fa";
					option4Element.style.backgroundColor = "#9810fa";
				}, 500);
				return;
			}

			setTimeout(() => {
				do {
					randomQuestion = Math.floor(Math.random() * questions.length);
				} while (doneQuestions.includes(randomQuestion));
				option1Element.style.backgroundColor = "#9810fa";
				option2Element.style.backgroundColor = "#9810fa";
				option3Element.style.backgroundColor = "#9810fa";
				option4Element.style.backgroundColor = "#9810fa";
			}, 500);
		};
	}

	onMount(() => {
		questionsElement = document.getElementById("question");
		optionsElement = document.getElementById("options");
		finishedElement = document.getElementById("finished");
		option1Element = document.getElementById("option1");
		option2Element = document.getElementById("option2");
		option3Element = document.getElementById("option3");
		option4Element = document.getElementById("option4");
	});
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
		<h2 id="question" class="my-10 text-3xl text-red-950 md:text-4xl">{questionJSON.question}</h2>
		<div hidden="hidden" id="finished">
			<h2 class="my-10 text-3xl text-red-950 md:text-4xl">You finished all the questions!</h2>
			<h3 class="my-10 text-2xl text-red-950 md:text-4xl">
				You got {score}/{questions.length} correct!
			</h3>
			<h3 class="my-10 text-2xl text-red-950 md:text-4xl">Wanna go again?</h3>
			<button
				class="mx-auto my-2 max-w-fit rounded-2xl bg-purple-600
				p-4 text-2xl text-red-950 md:text-3xl"
				onclick={() => {
					questionsElement.hidden = "";
					optionsElement.hidden = "";
					finishedElement.hidden = "hidden";
					doneQuestions = [];
					score = 0;
					do {
						randomQuestion = Math.floor(Math.random() * questions.length);
					} while (doneQuestions.includes(randomQuestion));
				}}
			>
				Restart Quiz
			</button>
		</div>
		<div id="options" class="@container/options my-auto flex flex-col">
			<button
				class="mx-auto my-2 max-w-fit rounded-2xl p-4 text-2xl text-red-950 md:text-3xl"
				onclick={questionSelected(0)}
				id="option1"
				style="background-color: #9810fa"
			>
				{questionJSON.options[0]}
			</button>
			<button
				class="mx-auto my-2 max-w-fit rounded-2xl p-4 text-2xl text-red-950 md:text-3xl"
				onclick={questionSelected(1)}
				id="option2"
				style="background-color: #9810fa"
			>
				{questionJSON.options[1]}
			</button>
			<button
				class="mx-auto my-2 max-w-fit rounded-2xl p-4 text-2xl text-red-950 md:text-3xl"
				onclick={questionSelected(2)}
				id="option3"
				style="background-color: #9810fa"
			>
				{questionJSON.options[2]}
			</button>
			<button
				class="mx-auto my-2 max-w-fit rounded-2xl p-4 text-2xl text-red-950 md:text-3xl"
				onclick={questionSelected(3)}
				id="option4"
				style="background-color: #9810fa"
			>
				{questionJSON.options[3]}
			</button>
		</div>
	</main>
</div>
