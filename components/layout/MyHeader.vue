<template>
  <header class="h">
    <div class="Top__header" :class="className">
      <div class="header__logo">
        <img :src="imageSrc" :alt="imageAlt" />
      </div>
      <div class="header__nav">
        <!-- <nav>
          <ul>
            <li>Home</li>
            <li>Menu</li>
            <li>Service</li>
            <li>Shope</li>
          </ul>
        </nav> -->
        <RouterLink class="link_router" :to="`/`"> home</RouterLink>
        <RouterLink class="link_router" :to="`/recipes/AllRecipes`">
          Menu</RouterLink
        >
        <RouterLink class="link_router" :to="`/`"> Service</RouterLink>
        <RouterLink class="link_router" :to="`/`"> Shope</RouterLink>
      </div>
      <div class="header__schearbar">
        <div class="__search">
          <MyIcon color="none" name="Search" />
          <input placeholder="Search" type="text" />

          <MyIcon color="none" name="Market" />
        </div>
      </div>
    </div>
  </header>
</template>

<script setup>
import { useGlobalStore } from "@/stores/global";

const store = useGlobalStore();
console.log(store);
import { computed } from "vue";
import MyIcon from "../elements/icons/MyIcon.vue";
const props = defineProps({
  imageAlt: String,
  imageSrc: String,
  theme: String,
  size: Boolean,
});
const className = computed(() => ({
  " -smart": props.size === "smartphone",
  " -device": props.size === "destop",

  " -ligth": props.theme === "ligthmode",
  " -darck": props.theme === "darckmode",
}));
</script>

<style lang="scss">
.Top__header {
  background-color: white;
  display: flex;
  justify-content: space-around;
  align-items: center;

  .header__nav {
    ul {
      list-style: none;
      font-family: $primary-font-familly;
      display: flex;
      justify-content: space-evenly;
      margin: 0;
      padding: 10px;
      gap: 25px;
    }
    .link_router {
      text-decoration: none;
      color: $black;
      font-family: $primary-font-familly;
      display: inline-block;
      margin: 0;
      padding: 10px;
      gap: 25px;
      transition: border-bottom 0.3s;
      border-bottom: 2px solid transparent;
    }
    .link_router:hover {
      border-bottom: 2px solid $primary-color;
     
    }
  }
  ::placeholder {
    font-family: Montserrat;
    font-size: 18px;
    font-style: normal;
    font-weight: 600;
    line-height: normal;
    color: black;
  }
  .header__schearbar {
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    gap: 25px;
    input {
      border: none;
      padding-inline: 10px;
      font-family: $primary-font-familly;
      font-size: 18px;
      font-style: normal;
    }
    .__search {
      border-bottom: 1px solid;
      border-radius: 10px;
      box-shadow: 0px 0px 17px 0px rgba(0, 0, 0, 0.15);
      padding: 5px;
    }
  }
}

.Top__header.-dark {
  background-color: var(--background-color-dark);
  color: var(--text-color-dark);
}

@media screen and (max-width: 768px) {
  /* Styles pour les écrans dont la largeur est de 768 pixels ou moins */
  .Top__header {
    flex-direction: column;
  }

  .header__logo {
    display: none;
  }

  .header__nav ul {
    flex-direction: column;
    gap: 10px;
  }
}
</style>
