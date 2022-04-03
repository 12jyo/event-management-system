<script>
	export let name;
	import {
		AspectRatio,
		Tile,
		Form,
		FormGroup,
		Checkbox,
		RadioButtonGroup,
		RadioButton,
		Select,
		SelectItem,
		Button,
		TextInput,
	} from "carbon-components-svelte";
	import FullCalendar from "svelte-fullcalendar";
	import daygridPlugin from "@fullcalendar/daygrid";

	let options = {
		initialView: "dayGridMonth",
		plugins: [daygridPlugin],
		dateClick: (event) => alert("date click! " + event.dateStr),
		events: [
			{ title: "event 1", date: "2022-04-01" },
			{ title: "event 2", date: "2022-04-02" },
		],
	};
</script>

<main>
	<!-- <h1>Hello {name}!</h1> -->
	<div class="container">
		<AspectRatio ratio="2x1">
			<Tile style="height: 12px">
				<p>EVENT PLANNER</p>
			</Tile>
			<div class="content">
				<Tile style="height: 100%; width: 20%; margin: 12px;">
					<Form on:submit>
						<FormGroup legend="Event Name">
							<TextInput
								labelText="Event Name"
								placeholder="Enter event name"
							/>
						</FormGroup>
						<FormGroup legendText="Event Deliverables">
							<Checkbox
								id="checkbox-0"
								labelText="Catering"
								checked
							/>
							<Checkbox id="checkbox-1" labelText="Hospitality" />
						</FormGroup>
						<FormGroup legendText="Event Type">
							<RadioButtonGroup
								name="radio-button-group"
								selected="default-selected"
							>
								<RadioButton
									id="radio-1"
									value="default-selected"
									labelText="Type 1"
								/>
								<RadioButton
									id="radio-2"
									value="standard"
									labelText="Type 2"
								/>
							</RadioButtonGroup>
						</FormGroup>
						<FormGroup>
							<Select
								id="select-1"
								labelText="Delegate to"
								value="placeholder-item"
							>
								<SelectItem
									disabled
									hidden
									value="placeholder-item"
									text="Choose an option"
								/>
								<SelectItem value="option-1" text="User 1" />
								<SelectItem value="option-2" text="User 2" />
								<SelectItem value="option-3" text="User 3" />
							</Select>
						</FormGroup>
						<Button type="submit">Submit</Button>
					</Form>
				</Tile>
				<Tile
					style="height: 75vh; width: 80%; margin: 12px; margin-left: -3px;"
				>
					<!-- <p>test</p> -->
					<div class="hight-low content">
						<FullCalendar {options} style="width: 600%"/>
					</div>
				</Tile>
			</div>
			<Tile>Copyright</Tile>
		</AspectRatio>
	</div>
</main>

<style>
	.container {
		height: 80vh;
	}

	.content {
		display: flex;
		flex-direction: row;
		justify-content: center;
	}

	.hight-low {
		height: 100%;
	}
</style>
