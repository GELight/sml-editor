<svelte:options tag="sml-editor" />

<script>
	import { get_current_component } from 'svelte/internal';
	let host = get_current_component();
	
	export let value = "";

	let editor;

	const keyup = (e) => {
		const elm = e.target;
		if (e.keyCode === 9 || e.key === 'Tab') {
			e.preventDefault();
			
			let start = elm.selectionStart;
			let end = elm.selectionEnd;
			
			elm.value = elm.value.substring(0, start) + "\t" + elm.value.substring(end);
			
			let cursorPos = start + 1
			elm.selectionStart = cursorPos
			elm.selectionEnd = cursorPos
		} else if (e.keyCode === 13 || e.key === 'Enter') {
			e.preventDefault();
			
			let lineIndentation = getLineIndentation(elm)
			let start = elm.selectionStart
			let end = elm.selectionEnd
			
			elm.value = elm.value.substring(0, start) +
				"\n" + lineIndentation + elm.value.substring(end)

			let cursorPos = start + 1 + lineIndentation.length
			elm.selectionStart = cursorPos
			elm.selectionEnd = cursorPos
		}
		
		if ('auto-resize' in $$props) {
			setTimeout(() => {
				editor.style.height = "auto";
				editor.style.height = (editor.scrollHeight)+"px";
			}, 0)
		}

		isAutoResize();
		scrollToBottom(e)
		
		host.dispatchEvent(new CustomEvent("change", { detail: { value }, composed: true }));
	}

	const isAutoResize = () => {
		if ('auto-resize' in $$props) {
			setTimeout(() => {
				editor.style.height = "auto";
				editor.style.height = (editor.scrollHeight)+"px";
			}, 0)
		}
	}

	const scrollToBottom = (e) => {
		if (e.ctrlKey && e.keyCode === 86) {
			editor.scrollTop = editor.scrollHeight;
		}
	}
	
	const getLineIndentation = (textarea) => {
		let cursorPos = textarea.selectionEnd;
		let text = textarea.value;
		let lineStart = 0;
		for (let i=cursorPos-1; i>=0; i--) {
			if (text[i] == "\n") {
				lineStart = i+1;
				break;
			}
		}
		let count = 0;
		for (let i=lineStart; i<text.length; i++) {
			if (!(text[i] == " " || text[i] == "\t" || text[i] == "\u3000")) {
				break;
			}
			count++;
		}
		let indentation = text.substring(lineStart,lineStart+count);
		return indentation;
	}
</script>

<textarea on:keyup="{keyup}" bind:this="{editor}" bind:value="{value}"></textarea>

<style>
	:host {
		display: flex;
		justify-content: stretch;
		align-items: stretch;
	}
	textarea {
		box-sizing: border-box;
		white-space: pre-wrap;
		outline: none;
		tab-size: var(--sml-editor-tab-size);
		width: 100%;
		max-height: var(--sml-editor-max-height);
		height: var(--sml-editor-height);
		overflow: auto;

		color: var(--sml-editor-color);
		background: var(--sml-editor-bg);
		border: var(--sml-editor-border);
		padding: var(--sml-editor-padding);

		box-shadow: var(--sml-editor-box-shadow);
		text-shadow: var(--sml-editor-text-shadow);

		font-family: var(--sml-editor-font-family);
		font-size: var(--sml-editor-font-size);
		line-height: var(--sml-editor-line-height);
		font-weight: var(--sml-editor-font-weight);
		font-style: var(--sml-editor-font-style);
		font-stretch: var(--sml-editor-font-stretch);
		letter-spacing: var(--sml-editor-letter-spacing);
		text-transform: var(--sml-editor-text-transform);
	}
</style>
