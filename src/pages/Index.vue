<template>
  <q-page class="flex flex-center">
   <div id="app" v-cloak>
			<div class="page-content">
				<img
					class="logo-pokemon"
					src="../assets/logo-pokemon.svg"
					alt=""
				/>
        <h2 class="game-options__title"> Number of cards</h2>
				<form class="game-options">
					<label for="gameOption1" class="game-options__label">
						<input
							id="gameOption1"
							class="game-options__input"
							type="radio"
							value="4"
							v-model="gameData.changed.selectedDeck"
						/>
						<svg width="20px" height="20px" viewBox="0 0 20 20">
							<circle cx="10" cy="10" r="9"></circle>
							<path
								d="M10,7 C8.34314575,7 7,8.34314575 7,10 C7,11.6568542 8.34314575,13 10,13 C11.6568542,13 13,11.6568542 13,10 C13,8.34314575 11.6568542,7 10,7 Z"
								class="inner"
							></path>
							<path
								d="M10,1 L10,1 L10,1 C14.9705627,1 19,5.02943725 19,10 L19,10 L19,10 C19,14.9705627 14.9705627,19 10,19 L10,19 L10,19 C5.02943725,19 1,14.9705627 1,10 L1,10 L1,10 C1,5.02943725 5.02943725,1 10,1 L10,1 Z"
								class="outer"
							></path>
						</svg>
						<span class="game-options__text">
							4
						</span>
					</label>
					<label for="gameOption2" class="game-options__label">
						<input
							id="gameOption2"
							class="game-options__input"
							type="radio"
							value="6"
							v-model="gameData.changed.selectedDeck"
						/>
						<svg width="20px" height="20px" viewBox="0 0 20 20">
							<circle cx="10" cy="10" r="9"></circle>
							<path
								d="M10,7 C8.34314575,7 7,8.34314575 7,10 C7,11.6568542 8.34314575,13 10,13 C11.6568542,13 13,11.6568542 13,10 C13,8.34314575 11.6568542,7 10,7 Z"
								class="inner"
							></path>
							<path
								d="M10,1 L10,1 L10,1 C14.9705627,1 19,5.02943725 19,10 L19,10 L19,10 C19,14.9705627 14.9705627,19 10,19 L10,19 L10,19 C5.02943725,19 1,14.9705627 1,10 L1,10 L1,10 C1,5.02943725 5.02943725,1 10,1 L10,1 Z"
								class="outer"
							></path>
						</svg>
						<span class="game-options__text">
							6
						</span>
					</label>
					<label for="gameOption3" class="game-options__label">
						<input
							id="gameOption3"
							class="game-options__input"
							type="radio"
							value="8"
							v-model="gameData.changed.selectedDeck"
						/>
						<svg width="20px" height="20px" viewBox="0 0 20 20">
							<circle cx="10" cy="10" r="9"></circle>
							<path
								d="M10,7 C8.34314575,7 7,8.34314575 7,10 C7,11.6568542 8.34314575,13 10,13 C11.6568542,13 13,11.6568542 13,10 C13,8.34314575 11.6568542,7 10,7 Z"
								class="inner"
							></path>
							<path
								d="M10,1 L10,1 L10,1 C14.9705627,1 19,5.02943725 19,10 L19,10 L19,10 C19,14.9705627 14.9705627,19 10,19 L10,19 L10,19 C5.02943725,19 1,14.9705627 1,10 L1,10 L1,10 C1,5.02943725 5.02943725,1 10,1 L10,1 Z"
								class="outer"
							></path>
						</svg>
						<span class="game-options__text">
							8
						</span>
					</label>
					<label for="gameOption4" class="game-options__label">
						<input
							id="gameOption4"
							class="game-options__input"
							type="radio"
							value="10"
							v-model="gameData.changed.selectedDeck"
						/>
						<svg width="20px" height="20px" viewBox="0 0 20 20">
							<circle cx="10" cy="10" r="9"></circle>
							<path
								d="M10,7 C8.34314575,7 7,8.34314575 7,10 C7,11.6568542 8.34314575,13 10,13 C11.6568542,13 13,11.6568542 13,10 C13,8.34314575 11.6568542,7 10,7 Z"
								class="inner"
							></path>
							<path
								d="M10,1 L10,1 L10,1 C14.9705627,1 19,5.02943725 19,10 L19,10 L19,10 C19,14.9705627 14.9705627,19 10,19 L10,19 L10,19 C5.02943725,19 1,14.9705627 1,10 L1,10 L1,10 C1,5.02943725 5.02943725,1 10,1 L10,1 Z"
								class="outer"
							></path>
						</svg>
						<span class="game-options__text">
							10
						</span>
					</label>
				</form>

				<div class="game-data">
					<p class="game-data__item game-data__attempts">
						Trials: {{ gameData.changed.attempts }}
					</p>
					<p class="game-data__item game-data__fails">
						Fails: {{ gameData.changed.fails }}
					</p>
					<p
						v-if="gameData.changed.difficult"
						class="game-data__item game-data__opportunities"
						:class="{'game-data__opportunities--error': gameData.changed.opportunities.last}"
					>
						Opportunities: {{ gameData.changed.opportunities.number }}
					</p>
					<button
						v-if="gameData.changed.selectedDeck > 8"
						class="button button--color"
						:disabled="counter.disabled"
						@click="setCounter"
					>
						<span
							v-if="counter.init"
							class="game-data__item game-data__counter"
						>
							{{ counter.changed }}
						</span>
						<span v-else>
							Start counter
						</span>
					</button>
				</div>
        <p v-if="offline" class="offline-mode">
          You are offline !
        </p>
				<ul
          v-if="!offline"
					class="game-list-cards"
					:class="{'game-list-cards--8': (gameData.changed.selectedDeck == 8), 'game-list-cards--10': (gameData.changed.selectedDeck > 8)}"
				>
					<li
						v-for="card in cards"
						:key="card.image"
						@click="selectCard(card)"
						:class="{'is-covered': coveredCards.includes(card), 'is-uncovered': uncoveredCards.includes(card)}"
						class="game-card"
					>
						<div class="game-card__face game-card-front">
							<h3 class="game-card-front__name">
								{{ card.name }}
							</h3>
							<img
								:src="card.image"
								class="game-card-front__image"
							/>
						</div>
						<div class="game-card__face game-card-back">
							<div class="game-card-back__inner">?</div>
						</div>
					</li>
				</ul>

				<button
					@click="resetGame"
					v-if="gameResult.finish"
					class="button button--game"
				>
					Play again
				</button>

				<transition name="slide-down-up">
					<div
						v-if="gameResult.win"
						class="game-result game-result--win"
					>
						Good game
					</div>
				</transition>
				<transition name="slide-down-up">
					<div
						v-if="gameResult.lose"
						class="game-result game-result--lose"
					>
						Game over
					</div>
				</transition>
			</div>

			<div v-if="showLoader" class="loader"></div>
		</div>
  </q-page>
</template>

<script>

export default {
  name: 'PageIndex',
  el: "#app",
	data() {
		return {
      offline: false,
			maxCards: 150,
			cards: [],
			pairedCards: [],
			selectedCards: [],
			gameData: {
				default: {
					selectedDeck: 4,
					attempts: 0,
					fails: 0,
					opportunities: {
						number: 2,
						last: false
					},
					difficult: false,
				},
				changed: {
					selectedDeck: 4,
					attempts: 0,
					fails: 0,
					opportunities: {
						number: 2,
						last: false
					},
					difficult: false,
				},
			},
			gameResult: {
				finish: false,
				win: false,
				lose: false,
			},
			gameReset: false,
			currentDateTime: {
				time: "00:00:00",
				date: "DD/MM/YYYY",
			},
			counter: {
				init: false,
				disabled: false,
				default: "00:00",
				changed: "00:00",
			},
			showLoader: false,
		};
	},
	computed: {
		uncoveredCards() {
			let uncoveredCards = [...this.pairedCards, ...this.selectedCards];
			return uncoveredCards;
		},
		coveredCards() {
			let coveredCards = this.cards.filter(
				(card) => !this.uncoveredCards.includes(card)
			);

			this.initGame(coveredCards);
			this.checkResultGame(coveredCards);
			this.checkDifficulty();

			return coveredCards;
		},
	},
	watch: {
		cards: {
			immediate: true,
			handler(newValue) {
				if (
					newValue.length == parseInt(this.gameData.changed.selectedDeck) * 2
				) {
					this.removeLoader();
				} else {
					this.createLoader();
				}
			},
		},
		"gameData.changed.selectedDeck": {
			immediate: true,
			handler(newValue) {
				this.gameData.changed.selectedDeck = parseInt(newValue);
				this.resetGame();
			},
		},
		"currentDateTime.date": {
			immediate: true,
			handler() {
				this.createCurrentDateFormat();
			},
		},
		"currentDateTime.time": {
			immediate: true,
			handler() {
				this.createCurrentTimeFormat();
			},
		},
		"counter.init": {
			immediate: true,
			handler() {
				if (this.counter.init) {
					this.createCounterdown();
				} else {
					this.counter.changed = this.counter.default;
				}
			},
		},
	},
	methods: {
		getRandomInteger(min, max) {
			const numberRandom = Math.floor(Math.random() * (max - min)) + min;
			// console.log("Number integer random:", numberRandom);

			return numberRandom;
		},
		async getTotalPokemon(){
			return this.maxCards;
		},
		async getPokemon(id) {
			try {
				const res = await fetch(`https://pokeapi.co/api/v2/pokemon/${id}`);
				const data = await res.json();
				// console.log(data);

				return data;
			} catch (error) {
				this.removeLoader();
				this.offline = true;
			}
		},
		createPokemon(data) {
			const pokemon = {
				id: data.id,
				name: data.name,
				images: {
					game: {
						front: data.sprites.front_default,
						back: data.sprites.back_default,
					},
					png: {
						front: `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/${data.id}.png`,
					},
					svg: {
						front: data.sprites.other.dream_world.front_default,
					},
				},
			};
			// console.log(pokemon);

			return pokemon;
		},
		createPairs(pokemons) {
			let pokemonPairs = [];
			for (let index = 0; index < pokemons.length; index++) {
				const pokemon = pokemons[index];

				const pokemonFront = {
					id: pokemon.id,
					name: pokemon.name,
					image: pokemon.images.game.front,
				};
				const pokemonBack = {
					id: pokemon.id,
					name: pokemon.name,
					image: pokemon.images.game.back,
				};

				pokemonPairs.push(pokemonFront);
				pokemonPairs.push(pokemonBack);
			}
			// console.log("Pokemon pairs", pokemonPairs);

			return pokemonPairs;
		},
		async getPokemons(numberMax) {
			let pokemonId = [];
			let pokemonList = [];

			const totalPokemon = await this.getTotalPokemon();
			
			for (let index = 0; index < numberMax; index++) {
				const pokemonRandom = await this.getRandomInteger(1, totalPokemon + 1);
				if (!pokemonId.some((item) => item == pokemonRandom)) {
					pokemonId.push(pokemonRandom);
					const pokemonData = await this.getPokemon(pokemonRandom);
					const pokemonDataFormatted = await this.createPokemon(pokemonData);
					pokemonList.push(pokemonDataFormatted);
				}
			}

			// console.log(`Get ${numberMax} pokemons`, pokemonList);

			return pokemonList;
		},
		async randomCards() {
			const pokemonsList = await this.getPokemons(this.gameData.changed.selectedDeck);
			const pokemonsPairs = this.createPairs(pokemonsList);
			this.cards = pokemonsPairs;
			this.cards.sort(() => Math.random() - 0.5);
		},
		selectCard(card) {
			if (!this.gameResult.finish) {
				this.selectedCards.push(card);

				if (this.selectedCards.length === 1) {
					if (!this.counter.init) {
						this.counter.disabled = true;
					}
				} else if (this.selectedCards.length === 2) {
					this.gameData.changed.attempts++;
					const [card1, card2] = this.selectedCards;

					if (card1 !== card2) {
						if (card1.id === card2.id) {
							this.pairedCards = this.pairedCards.concat(
								this.selectedCards
							);
						} else {
							this.gameData.changed.fails++;
							if (this.gameData.changed.difficult) {
								this.gameData.changed.opportunities.number--;
							}
						}
					}

					this.checkLastOpportunity();

					setTimeout(() => {
						this.selectedCards = [];
					}, 500);
				}
			}
		},
		resetData() {
			this.gameData.changed.attempts = this.gameData.default.attempts;
			this.gameData.changed.fails = this.gameData.default.fails;
			this.gameData.changed.opportunities.number = this.gameData.default.opportunities.number;
			this.gameData.changed.opportunities.last = this.gameData.default.opportunities.last;
			this.gameData.changed.difficult = this.gameData.default.difficult;
		},
		resetResult() {
			this.gameResult.finish = false;
			this.gameResult.win = false;
			this.gameResult.lose = false;
		},
		initGame(coveredCards) {
			if (this.gameReset) {
				this.cards = coveredCards;
				this.gameReset = false;
				this.gameResult.finish = false;
			}
		},
		resetGame() {
			this.randomCards();
			this.pairedCards = [];
			this.selectedCards = [];
			this.resetData();
			this.resetResult();
			this.gameReset = true;
			this.updatedOpportunities();
			this.lastOpportunity = false;
			this.counter.init = false;
			this.counter.disabled = false;
		},
		checkResultGame(coveredCards) {
			if (coveredCards.length == 0) {
				this.gameResult.finish = true;
				this.gameResult.win = true;
			}
		},
		checkDifficulty() {
			if (this.gameData.changed.selectedDeck >= 8) {
				this.gameData.changed.difficult = true;
				this.checkOpportunities();
			} else {
				this.gameData.changed.difficult = false;
			}
		},
		checkOpportunities() {
			if (this.gameData.changed.opportunities.number == 0) {
				this.gameResult.finish = true;
				this.gameResult.lose = true;
			}
		},
		checkLastOpportunity() {
			this.gameData.changed.difficult &&
			this.gameData.changed.opportunities.number <= 1
				? (this.gameData.changed.opportunities.last = true)
				: false;
		},
		updatedOpportunities() {
			this.gameData.changed.opportunities.number = (this.gameData.changed.selectedDeck * 2) - 6;
		},
		getCurrentDate() {
			return new Date();
		},
		getCurrentYear() {
			return this.getCurrentDate().getFullYear();
		},
		getCurrentMonth() {
			return this.getCurrentDate().getMonth() + 1;
		},
		getCurrentDay() {
			return this.getCurrentDate().getDate();
		},
		getCurrentHours() {
			return this.getCurrentDate().getHours();
		},
		getCurrentMinutes() {
			return this.getCurrentDate().getMinutes();
		},
		getCurrentSeconds() {
			return this.getCurrentDate().getSeconds();
		},
		checkDigits(number) {
			return number.toString().length < 2
				? 0 + number.toString()
				: number.toString();
		},
		createCurrentDateFormat() {
			setInterval(() => {
				const day = this.checkDigits(this.getCurrentDay());
				const month = this.checkDigits(this.getCurrentMonth());
				const year = this.checkDigits(this.getCurrentYear());

				this.currentDateTime.date = `${day}/${month}/${year}`;
			}, 1000);
		},
		createCurrentTimeFormat() {
			setInterval(() => {
				const hours = this.checkDigits(this.getCurrentHours());
				const minutes = this.checkDigits(this.getCurrentMinutes());
				const seconds = this.checkDigits(this.getCurrentSeconds());

				this.currentDateTime.time = `${hours}:${minutes}:${seconds}`;
			}, 1000);
		},
		setCounter() {
			this.counter.init = !this.counter.init;
		},
		createCounterdown() {
			const seconds = 60;
			const end = this.getCurrentDate().getTime() + seconds * 1000;

			let timeout = setInterval(() => {
				let counter = Math.floor((end - this.getCurrentDate().getTime()) / 1000);
				if (counter < 0) {
					counter = 0;
				}

				this.counter.changed = `${Math.floor(counter / 60)}:${("00" + Math.floor(counter % 60)).slice(-2)}`;

				if (counter === 0 && !this.gameResult.finish) {
					this.gameResult.finish = true;
					this.gameResult.lose = true;
				}

				if (this.gameResult.finish) {
					clearTimeout(timeout);
				}

				if (counter === 0 || !this.counter.init) {
					this.counter.changed = this.counter.default;
					clearTimeout(timeout);
				}
			}, 300);
		},
		createLoader() {
			this.showLoader = true;
		},
		removeLoader() {
			setTimeout(()=>{
				this.showLoader = false;
			}, 1500);
		},
	},
}
</script>
<style>
/*** IMPORTS ***/
/**************************/

@import url("https://fonts.googleapis.com/css?family=Roboto:400,700");





/*** COLOR ***/
/**************************/



</style>