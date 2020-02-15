<template>
	<section class="ba-section-profile" >
    <div class="row">
      <div class="column large-4 small-12">
        <div class="ba-img-wrap">
			  <img class="ba-section-profile-img" :src="card.img" :alt="card.name" />
		  </div>
		  <a href="search.html" class="ba-button ba-button-comeback"> 
			 	<svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg">
					<path d="M15.9999 6.99996V8.99996H3.99991L9.49991 14.5L8.07991 15.92L0.159912 7.99996L8.07991 0.0799561L9.49991 1.49996L3.99991 6.99996H15.9999Z" fill="white"/>
				</svg>
				Вернуться к списку событий
		  </a>
      </div>
      <div class="column large-7 small-12">
        <div class="ba-card-info">
          <span class="ba-person-name">{{ card.name }}</span>
          <span class="ba-data">{{ card.date }}</span>
        </div>
        <div class="ba-reason">{{ card.reason }}</div>
        <div class="ba-profile-list-info">
          <ul class="ba-list--2col">
            <li>
              <span class="ba-value">О встрече:</span>
              <span class="ba-answer">{{ card.info }}</span>
            </li>
            <li>
              <span class="ba-value">Заведение:</span>
              <span class="ba-answer">{{ card.place }}</span>
            </li>
            <li>
              <span class="ba-value">Компания:</span>
              <span class="ba-answer">{{ card.company }}</span>
            </li>
            <li>
              <span class="ba-value">Повод:</span>
              <span class="ba-answer">{{ card.reason }}</span>
            </li>
            <li>
              <span class="ba-value">Напиток:</span>
              <span class="ba-answer">{{ card.drink }}</span>
            </li>
            <li>
              <span class="ba-value">Собрано:</span>
              <span class="ba-answer">{{ card.people }}</span>
            </li>
          </ul>
			<button class="ba-button ba-button--lighter ba-button-conect large-offset-2">
				Присоединиться
			</button>
        </div>
      </div>
      <div class="column large-1 small-3 ba-rating-pos show-for-large">
        <div class="ba-rating-title">Рейтинг</div>
        <div class="ba-rating" v-if="card.rating">
				<span v-for="star in card.rating" v-if="card.rating >= 1">&#9733</span>
				<!-- {n = 4 - card.rating} -->
				<span v-for="star in n" v-if="card.rating < 4">&#9734</span>
      </div>
    </div>
	 </div>
  </section>
</template>

<script>
	// import json from './json/cards.json';
export default {
  data() {
    return {
      card: {},
    };
  },

  mounted() {
    fetch('assets/json/cards.json')
      .then(res => res.json())
      .then(list => {
        this.card = list.filter(item => {
          return item.id === localStorage.singelPageId;
        })[0];
      });
  },
};

</script>