<script>
	let html = '<h1>hi</h1>';
	let markdown = '';
	const rules = [
        { regex: /(\*\*|__)(.*?)\1/g, replace: '<strong>$2</strong>' }, // Bold
        { regex: /(\*|_)(.*?)\1/g, replace: '<em>$2</em>' }, // Italics
        { regex: /# (.*?)(?:\r?\n|$)/g, replace: '<h1>$1</h1>' }, // Heading 1
        { regex: /## (.*?)(?:\r?\n|$)/g, replace: '<h2>$1</h2>' }, // Heading 2
		{ regex: /([^\n]+)(\*)([^\n]+)/g, replace: "<ul><li>$3</li></ul>" } // Numbered list
	];
	function renderMarkdown() {
		html = markdown;
		rules.forEach((rule) => {
			html = html.replace(rule.regex, rule.replace);
		});
	}
</script>

<html lang="en">
	<body>
		<div id="row">
			<div class="rowItem">
				<textarea bind:value={markdown} />
			</div>
			<div id="divider" />
			<div class="rowItem">
				{@html html}
			</div>
		</div>
		<br />
		<button on:click={renderMarkdown}>Render</button>
		<br />
	</body>
	<style>
		body {
			margin: 0;
			padding: 0;
		}
		textarea {
			resize: none;
			width: 100%;
			padding: 1em;
			margin: 0;
			height: 100vh;
			box-sizing: border-box;
		}
		#divider {
			border-left: 2px solid black;
			position: absolute;
			left: 50%;
			margin-left: -3px;
			top: 0;
		}
		#row {
			display: flex;
			flex-direction: row;
		}
		.rowItem {
			flex: 1;
		}
	</style>
</html>
