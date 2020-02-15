<template>
	<section class="ba-section-cards">
	<div class="row align-center">
		<div class="column large-10 small-12">
			<div class="ba-search-filters">
				<button class="button ba-fillters-button" type="button" data-toggle="form-dropdown">
					<svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
						<path d="M19.75 18.0625L13.9338 12.2453C14.8711 10.9572 15.3753 9.40488 15.3738 7.81188C15.3738 3.64234 11.9814 0.25 7.81188 0.25C3.64234 0.25 0.25 3.64234 0.25 7.81188C0.25 11.9814 3.64234 15.3738 7.81188 15.3738C9.40488 15.3753 10.9572 14.8711 12.2453 13.9338L18.0625 19.75L19.75 18.0625ZM7.81188 12.9855C6.7885 12.9856 5.78809 12.6822 4.93714 12.1137C4.0862 11.5452 3.42296 10.7371 3.03129 9.79165C2.63961 8.8462 2.53711 7.80583 2.73674 6.80211C2.93637 5.7984 3.42916 4.87643 4.15279 4.15279C4.87643 3.42916 5.7984 2.93637 6.80211 2.73674C7.80583 2.53711 8.8462 2.63961 9.79165 3.03129C10.7371 3.42296 11.5452 4.0862 12.1137 4.93714C12.6822 5.78809 12.9856 6.7885 12.9855 7.81188C12.9839 9.1835 12.4383 10.4985 11.4684 11.4684C10.4985 12.4383 9.1835 12.9839 7.81188 12.9855Z" fill="#190078"/>
					</svg>
					Уточнить детали поиска
				</button>
    			<div class="dropdown-pane" id="form-dropdown" data-dropdown data-auto-focus="true">
      			<form action="#" method="POST">
						<label for="city">Город</label>
						<select id="city" v-on:change="changeCity">
							<option value="Киев">Киев</option>
							<option value="Полтава">Полтава</option>
							<option value="Харьков">Харьков</option>
							<option value="Львов">Львов</option>
							<option value="Где" selected hidden>Где</option>
						</select>

						<label for="date">Дата</label>
						<input type="date" id="date" name="start" value="Когда" v-on:change="changeDate">

						<label for="drink">Что пить</label>
						<select id="drink" v-on:change="changeDrink">
							<option value="Водка">Водка</option>
							<option value="Ром">Ром</option>
							<option value="Виски">Виски</option>
							<option value="Вино">Вино</option>
							<option value="Текила">Текила</option>
							<option value="Пиво">Пиво</option>
							<option value="Настойки">Настойки</option>
							<option value="Коктейли">Коктейли</option>
							<option value="Другое">Другое</option>
							<option value="Вид алкоголя" selected hidden>Вид алкоголя</option> 
						</select>

						<label for="amount">Количество людей</label>
						<select id="amount" v-on:change="changeCompany">
							<option value="1">1</option>
							<option value="2">2</option>
							<option value="3">3</option>
							<option value="4">4</option>
							<option value="5">5</option>
							<option value="6">Больше 5</option>
							<option value="Сколько людей хочу найти" selected hidden>Сколько людей хочу найти</option>
						</select>

						<button class="ba-button ba-button--lighter ba-button-reset" v-on:click="resetFilter"> 
							Сбросить фильтр	
						</button>	
					</form>
    			</div>

				<a href="#" class="hide-for-small-only">	
					<svg width="21" height="27" viewBox="0 0 21 27" fill="none" xmlns="http://www.w3.org/2000/svg">
						<path d="M6.12508 0.375L0.291748 6.20833H4.66675V16.4167H7.58342V6.20833H11.9584L6.12508 0.375ZM16.3334 20.7917V10.5833H13.4167V20.7917H9.04175L14.8751 26.625L20.7084 20.7917H16.3334Z" fill="#F2E7FE"/>
					</svg>
				</a>	
			</div>
			<!-- /.ba-search-filters -->
			<div class="ba-card">
				<div class="person-card" v-for="(card, index) in cardsDisplayed">
					<a :href="card.url" id="search" v-on:click="showSinglePage(card.id)">
						<div class="row">
							<div class="column large-4 small-4">
								<img class="ba-person-card-img" :src="card.img" :alt="card.name">

							</div>						
							<div class="column large-8 small-8">
								<div class="ba-person-name">
									{{card.name}}

									<svg v-if="card.challenge" width="20" height="16" viewBox="0 0 20 16" fill="none" xmlns="http://www.w3.org/2000/svg">
										<path d="M20 6V2C20 0.9 19.1 0 18 0H2C0.9 0 0.00999999 0.9 0.00999999 2V6C1.11 6 2 6.9 2 8C2 9.1 1.11 10 0 10V14C0 15.1 0.9 16 2 16H18C19.1 16 20 15.1 20 14V10C18.9 10 18 9.1 18 8C18 6.9 18.9 6 20 6ZM18 4.54C16.81 5.23 16 6.53 16 8C16 9.47 16.81 10.77 18 11.46V14H2V11.46C3.19 10.77 4 9.47 4 8C4 6.52 3.2 5.23 2.01 4.54L2 2H18V4.54ZM7.07 12L10 10.12L12.93 12L12.04 8.64L14.73 6.44L11.26 6.23L10 3L8.73 6.22L5.26 6.43L7.95 8.63L7.07 12Z" fill="#02BEB2"/>
									</svg>

								</div>
								<div class="ba-card-info">
									<div class="ba-rating" v-if="card.rating">
										<span v-for="star in card.rating" v-if="card.rating >= 1">&#9733</span>
										<!-- {n = 4 - card.rating} -->
										<span v-for="star in n" v-if="card.rating < 4">&#9734</span>
									</div>
									<div class="ba-data">{{card.date}}</div>
								</div>
								<div class="row">
									<div class="column">
										<div class="ba-person-list-info">
											<ul class="ba-list--2col">
												<li>
													<span class="ba-value">Город:</span>
													<span class="ba-answer">{{card.city}}</span>
												</li>
												<li>
													<span class="ba-value">Повод:</span>
													<span class="ba-answer">{{card.reason}}</span>
												</li>
												<li>
													<span class="ba-value">Компания:</span>
													<span class="ba-answer">{{card.company}}</span>
												</li>
												<li>
													<span class="ba-value">Заведение:</span>
													<span class="ba-answer">{{card.place}}</span>
												</li>
												<li>
													<span class="ba-value">Напиток:</span>
													<span class="ba-answer">{{card.drink}}</span>
												</li>
												<li v-if="card.challenge">
													<span class="ba-value ba-value--challenge">Челендж:</span>
													<span class="ba-answer">{{card.challenge}}</span>
												</li>
											</ul>
										</div>
										<!-- /.ba-person-list-info -->
									</div>
								</div>
							</div>
							<!-- /.column -->
						</div>
					</a>
					<div class="ba-like" v-on:click="toggleFollowToP (isActive = !isActive)" >
						<svg width="21" height="20" viewBox="0 0 21 20" fill="none" xmlns="http://www.w3.org/2000/svg">
							<path v-bind:class="{isActive: isActive}"  d="M10.4999 19.2396L8.9895 17.8646C3.62492 13 0.083252 9.79167 0.083252 5.85417C0.083252 2.64583 2.60409 0.125 5.81242 0.125C7.62492 0.125 9.3645 0.96875 10.4999 2.30208C11.6353 0.96875 13.3749 0.125 15.1874 0.125C18.3958 0.125 20.9166 2.64583 20.9166 5.85417C20.9166 9.79167 17.3749 13 12.0103 17.875L10.4999 19.2396Z" fill="#D7B7FD"/>
						</svg>
					</div>
					<div class="ba-button--more">
						<button class="waves-effect waves-light btn ba-button-more" v-if="index + 1 === cardsDisplayed.length && index + 1 !== cards.length" v-on:click="loadMore()">еще</button>
					</div>
				</div>
				<!-- /.person-card -->
			</div>
			<!-- /.ba-card -->
		</div>
	</div>
</section>
<!-- /.ba-section-cards -->

</template>

<script>
	// import json from './json/cards.json';
export default {

	data() {
		isLoading: false;		
		isMoreLoading: false;
		
		return {
			initialCards: [],
			cards: [],
			cardsDisplayed: [],
			isActive:false,
			filters: {
				city: "",
				drink: "",
				company: "",
				date: ""
			}
		}
	},
	methods:{
		toggleFollowToPerson(id) {
      let followToPerson = [];
      if (localStorage.followToPerson !== undefined) {
        followToPerson = JSON.parse(localStorage.followToPerson);
      }

      console.log(followToPerson);
      if (!followToPerson.length) {
        followToPerson.push(id);
      } else {
        const check = followToPerson.find(saveId => saveId === id);
        if (check) {
          followToPerson = followToPerson.filter(saveId => saveId !== id);
        } else {
          followToPerson.push(id);
        }
      }
      console.log(followToPerson);

      localStorage.setItem("followToPerson", JSON.stringify(followToPerson));
    },
		loadMore(){
			this.cardsDisplayed.push(
				...this.cards.slice(this.cardsDisplayed.length, this.cardsDisplayed.length + 3)
				)
		}, 
		showSinglePage(id) {
      	localStorage.singelPageId = id;
    	},
		filter(){
			const cards = this.initialCards;

			const filters = this.filters;

			for (let f in this.filters) {
				if (this.filters[f] === '') delete filters[f];
			}

			this.cards = cards.filter(card => {
				let found = null;
				for (let f in filters) {
					console.log(card.city, filters[f]);
					if (f !== 'company' || filters[f] <= 5) {
						found = card[f] === filters[f] && found !== false;
					} else if (f === 'company' && filters[f] > 5) {
						found = card[f] > 5 && found !== false;
					}
				}
				return found;
			});
			this.cardsDisplayed = this.cards.slice(0, 5);
		},
		changeCity(event){
			this.filters.city = event.target.value;
			this.filter();
		},
		changeDrink(event){
			this.filters.drink = event.target.value;
			this.filter();
		},
		changeCompany(event){
			this.filters.company = +event.target.value;
			this.filter();
		},
		changeDate(event) {
			const d = new Date(event.target.value);
		
			this.filters.date = `${d.getDate()}.${d.getMonth() + 1 <= 9 ? '0' + (d.getMonth() + 1) : d.getMonth() + 1}.${d.getFullYear()}`;
			this.filter();
		},
		resetFilter(event){
			event.preventDefault();

			event.target.closest('form').reset();
			this.filters = {
				city: "",
				drink: "",
				company: "",
				date: ""
			};
			this.cards = this.initialCards;
			this.cardsDisplayed = this.cards.slice(0, 5);
		}
	},
	mounted(){
		fetch('assets/json/cards.json')
		.then(res => res.json())
		.then(list => {
			this.initialCards = list;
			this.cards = list;
			this.cardsDisplayed = list.slice(0, 5); 
			let element = $('#form-dropdown');
			
			var elem = new Foundation.Dropdown(element);
		});
	}
};

</script>