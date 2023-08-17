<script>
	let html = '<h1>hi</h1>';
	let markdown = '';
	let rules = [
		{ regex: /(\*\*|__)(.*?)\1/g, replace: '<strong>$2</strong>' }, // Bold
		{ regex: /(\*|_)(.*?)\1/g, replace: '<em>$2</em>' }, // Italics
		{ regex: /# (.*?)(?:\r?\n|$)/g, replace: '<h1>$1</h1>' }, // Heading 1
		{ regex: /## (.*?)(?:\r?\n|$)/g, replace: '<h2>$1</h2>' } // Heading 2
		// Add more rules for other Markdown syntax
	];
	function renderMarkdown() {
		html = markdown;
		rules.forEach((rule) => {
			html = html.replace(rule.regex, rule.replace);
		});
	}
</script>
<div id="row">
<textarea bind:value={markdown} />
{@html html}
</div>
<br />
<button on:click={renderMarkdown}>Render</button>
<br />
<style>
	textarea {
		resize: none;
        padding: 0;
        margin: 0;
        width: 50%;
        height: 100%; 
	}
    #row{
        display: flex;
        flex-direction: row;
    }
    h1{
        margin: 0
    }
</style>
