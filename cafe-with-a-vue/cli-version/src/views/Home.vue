<template>
  <div id="app">
    <h1>{{ restaurantName }}</h1>
		<p class="description">
			Bienvenue dans notre café {{ restaurantName }}! Nous sommes réputés pour
			notre pain et nos merveilleuses pâtisseries. Faites vous plaisir dès le
			matin ou avec un goûter réconfortant. Mais attention, vous verrez qu'il
			est difficile de s'arrêter.
		</p>

		<section class="menu">
			<h2>Menu</h2>
			<div v-for="item in simpleMenu" :key="item.name" class="menu-item">
				<img
					class="menu-item__image"
					:src="item.image.source"
					:alt="item.image.alt"
				/>
				<div>
					<h3>{{ item.name }}</h3>
					<p v-if="item.inStock">En stock</p>
					<p v-else>En rupture de stock</p>
					<div>
						<label for="add-item-quantity"
							>Quantité : {{ item.quantity }}</label
						>
						<input
							v-model.number="item.quantity"
							id="add-item-quantity"
							type="number"
						/>
						<button @click="addToShoppingCart(item.quantity)">
							Ajouter au panier
						</button>
					</div>
				</div>
			</div>
		</section>

		<aside class="shopping-cart">
			<h2>Panier d'achat : {{ shoppingCart }} articles</h2>
		</aside>
  </div>
</template>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>

<script>
export default {
  name: "Home",
  data() {
		return {
			restaurantName: "La belle vue",
				shoppingCart: 0,
				simpleMenu: [
					{
						name: "Croissant",
						image: {
							source: "/images/crossiant.jpg",
							alt: "Un croissant"
						},
						inStock: true,
						quantity: 1
					},
					{
						name: "Baguette de pain",
						image: {
							source: "/images/french-baguette.jpeg",
							alt: "Quatre baguettes de pain"
						},
						inStock: true,
						quantity: 1
					},
					{
						name: "Éclair",
						image: {
							source: "/images/eclair.jpg",
							alt: "Éclair au chocolat"
						},
						inStock: false,
						quantity: 1
					}
				]
		}
	}
};
</script>
