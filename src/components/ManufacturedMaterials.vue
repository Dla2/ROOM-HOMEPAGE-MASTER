<template>
    <section>

        <h1>Manufactured with the best materials</h1>

        <p>Our modern furniture store provide a high level of quality. Our company has invested in advanced technology 
  to ensure that every product is made as perfect and as consistent as possible. With three decades of 
  experience in this industry, we understand what customers want for their home and office.</p>
        <p class="shop-now-btn">SHOP NOW <span><img src="../assets/icon-arrow.svg" alt=""></span></p>

        <div class="change-btns">
          <button><img src="../assets/icon-angle-left.svg" alt="angle left/ go left button icon" @click="$emit('sub-count', props.count)"></button>
          <button><img src="../assets/icon-angle-right.svg" alt="angle right/ go right button icon" @click="$emit('add-count', props.count)"></button>
        </div>

    </section>
</template>

<script setup>
const props = defineProps(['count'])
defineEmits(['sub-count', 'add-count'])
</script>

<style scoped>
section {
  padding: 3.75rem 2rem 4.75rem;
  font-weight: 500;
}

section h1 {
  font-size: 2rem;
  font-weight: 700;
  margin-bottom: 1.75rem;
}

section p {
  color: var(--Dark-Gray);
  font-size: 1rem;
  margin-bottom: 3rem;
}

section .shop-now-btn {
  margin-bottom: 0rem;
  letter-spacing: 1rem;
  color: var(--Black);
  display: grid;
  grid-template-columns: max-content max-content;
  transition: color 0.5s ease;
  cursor: pointer;
}
section .shop-now-btn:hover {
  color: var(--Dark-Gray);
}

section .shop-now-btn span{
  align-self: center;
}
section .shop-now-btn span img {
  margin-top: 3.6px;
}
section .change-btns {
  display: none;
}
section .change-btns button{
  border: none;
  background-color: var(--Black);
  padding: 1.25rem 1.5rem;
  cursor: pointer;
  transition: background 0.5s ease;
}
section .change-btns button:hover {
  background-color: var(--Very-Dark-Gray);
}

@media screen and (min-width: 500px) {
  section {
    text-align: center;
  }
  section .shop-now-btn {
    display: inline-flex;
  }
  section .change-btns {
    display: block;
    margin: 2rem auto 0rem;
  }
}

@media screen and (min-width: 840px) {
  section {
    position: relative;
    padding: clamp(3.75rem, 5.75rem , 7.75rem) clamp(2rem, 4.125rem , 6.25rem) clamp(4.75rem,7.25rem , 9.75rem);
    text-align: left;
  }

  section p {
    margin-bottom: 1.5rem;
  }

  section p {
    margin-bottom: 1.75rem;
  }
  section .change-btns {
    display: block;
    position: absolute;
    left: 0;
    bottom: 0;
    margin: 0;
  }
}
</style>