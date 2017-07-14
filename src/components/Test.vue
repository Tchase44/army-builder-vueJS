<template>
	<main class="test">
		<h1>Army Builder</h1>

		<input type="text" id="raceForm" v-model='newRace' v-on:keypress.enter='methods.addRace(newRace,races)'/>
		<button v-on:click="methods.addRace(newRace,races)">add race</button>

		<div>
			<ul>
				<div v-for="race,index in races" >
					<h4>{{ race.name }}
						<span class="x" v-on:click="methods.removeRace(index,races)">[X]</span>
					</h4>
					<p>{{race.alignment}} </p>
					<p>Army Size: {{race.armySize}} 
						<button class="b" v-on:click="methods.addUnits(race)" > [+] </button>
						<button class="b" v-on:click="methods.removeUnits(race)"> [-] </button>
					</p>
					<p>Total Heros: {{race.totalHeroes}} 
						<button class="b" v-on:click="methods.addHero(race)" > [+] </button>
						<button class="b" v-on:click="methods.removeHero(race)"> [-] </button>
					</p>
				</div>
			</ul>
		</div>

	</main>
</template>

<script>
	export default {
		// el: '.test',
		name: 'test',
		data() {
			return {
				newRace: '',
				races: [
				{
				name: "Lizardmen",
				alignment: "Neutral/Good",
				armySize: 1200,
				totalHeroes: 3
				},{
				name: "High Elves",
				alignment: "Good",
				armySize: 1000,
				totalHeroes: 2
				},{
				name: "Chaos",
				alignment: "Evil",
				armySize: 900,
				totalHeroes: 3
				}],
				methods: {
					addRace: function(newRace,races){
						// console.log(`${newRace}`)
						if(newRace !== ''){
							races.push({
								name: newRace,
								alignment: '',
								armySize: 0,
								totalHeroes: 0
							})
						}
						document.getElementById('raceForm')
					},
					removeRace(index,races){
						// console.log(this)
						races.splice(index,1)
					},
					addHero(race){
						race.totalHeroes += 1
					},
					removeHero(race){
						race.totalHeroes <= 0 ? race.totalHeroes = 0 : race.totalHeroes -= 1
					},
					addUnits(race){
						race.armySize += 100
					},
					removeUnits(race){
						race.armySize <= 0 ? race.armySize = 0 : race.armySize -= 100
					},
				}
			}
		}
	}


</script>

<style >
	span.x{
		cursor: pointer;
	}
	button.b{
		cursor: pointer;
	}
<style>