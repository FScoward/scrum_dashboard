<script>
  import Chyart from "chart.js"
	export let name;

	let json = `
	[
		{"day": "one", "point": 100},
		{"day": "two", "point": 90},
		{"day": "three", "point": 40},
		{"day": "four", "point": 20},
		{"day": "five", "point": 0}
	]
	`;

	let burndown_data = JSON.parse(json);

	let labels = new Array(burndown_data.length);
	let data = new Array(burndown_data.length);

	for(var i=0; i<burndown_data.length; i++){
		labels[i] = burndown_data[i].day;
		data[i] = burndown_data[i].point;
	};


	function renderChart() {
    var ctx = document.getElementById("myChart").getContext("2d");
    var chart = new Chart(ctx, {
      type: "line",
      data: {
        labels: labels,
        datasets: [
          {
            label: "Burndown chart",
            borderColor: "rgb(255, 99, 132)",
            data: data
          }
        ]
      },
      options: {
				elements: {
            line: {
                tension: 0, // ベジェ曲線を無効にする
            }
        }
			}
    });
  }
</script>

<main>
	<button on:click={renderChart}>Load</button>
	<canvas id="myChart"></canvas>

	<h1>Hello {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>