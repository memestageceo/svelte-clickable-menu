<script lang="ts">
	type ToggleProps = {
		checked: boolean;
		id: string;
		label: string;
		onchange?: () => void;
	};

	let { checked = $bindable(), id = '', label = '', onchange }: ToggleProps = $props();
</script>

<div class="flex items-center">
	<label
		for={id}
		class="relative inline-block h-8 w-14 cursor-pointer rounded-full bg-gray-300 transition [-webkit-tap-highlight-color:_transparent] has-[:checked]:bg-green-500"
	>
		<input
			type="checkbox"
			{id}
			class="peer absolute inset-0 cursor-pointer rounded-full opacity-0 focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-blue-500 focus-visible:ring-offset-2 [&:checked_+_span_svg[data-checked-icon]]:block [&:checked_+_span_svg[data-unchecked-icon]]:hidden"
			bind:checked
			{onchange}
			role="switch"
			aria-checked={checked}
			aria-labelledby={`${id}-label`}
		/>

		<span
			class="absolute inset-y-0 start-0 z-10 m-1 inline-flex size-6 items-center justify-center rounded-full bg-white text-gray-400 transition-all peer-checked:start-6 peer-checked:text-green-600"
		>
			<svg
				data-unchecked-icon
				xmlns="http://www.w3.org/2000/svg"
				class="h-4 w-4"
				viewBox="0 0 20 20"
				fill="currentColor"
				aria-hidden="true"
			>
				<path
					fill-rule="evenodd"
					d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z"
					clip-rule="evenodd"
				/>
			</svg>

			<svg
				data-checked-icon
				xmlns="http://www.w3.org/2000/svg"
				class="hidden h-4 w-4"
				viewBox="0 0 20 20"
				fill="currentColor"
				aria-hidden="true"
			>
				<path
					fill-rule="evenodd"
					d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z"
					clip-rule="evenodd"
				/>
			</svg>
		</span>
		<span class="sr-only">{checked ? 'On' : 'Off'}</span>
	</label>
</div>
