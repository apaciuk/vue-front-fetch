<template>
<div>
    <h1>Nuxt Mountains</h1>
  <p v-if="$fetchState.pending">Fetching mountains...</p>
  <p v-else-if="$fetchState.error">An error occurred :(</p>
<article  v-for="mountain of mountains" :key="mountain.id" class="br2 ba dark-gray b--black-10 mv4 w-100 w-50-m w-25-l mw5 center">
  <img src="https://picsum.photos/id/1016/600/300" class="db w-100 br2 br--top" alt="Mountain.">
  <div class="pa2 ph3-ns pb3-ns">
    <div class="dt w-100 mt1">
      <div class="dtc">
        <h1 class="f5 f4-ns mv0">{{ mountain.title }}</h1>
      </div>
     
    </div>
    <p class="f6 lh-copy measure mt2 mid-gray">
    {{mountain.description}}
    </p>
</div>
</article>
<button @click="$fetch">Refresh</button>
</div>
</template>

<script>
  export default {
    data() {
      return {
        mountains: []
      }
    },
    async fetch() {
      this.mountains = await fetch(
        'https://api.nuxtjs.dev/mountains'
      ).then(res => res.json())
    }
  }
</script>
<style scoped>
.ba {
    border-style: solid;
    border-width: 1px;
}

.b--black-10 {
    border-color: rgba(0, 0, 0, .1);
}

.br2 {
    border-radius: .25rem;
}

.br--top {
    border-bottom-left-radius: 0;
    border-bottom-right-radius: 0;
}

.db {
    display: block;
}

.dt {
    display: table;
}

.dtc {
    display: table-cell;
}

.lh-copy {
    line-height: 1.5;
}

.mw5 {
    max-width: 16rem;
}

.w-100 {
    width: 100%;
}

.dark-gray {
    color: #333;
}

.mid-gray {
    color: #555;
}

.pa2 {
    padding: .5rem;
}

.mt1 {
    margin-top: .25rem;
}

.mt2 {
    margin-top: .5rem;
}

.mv0 {
    margin-top: 0;
    margin-bottom: 0;
}

.mv4 {
    margin-top: 2rem;
    margin-bottom: 2rem;
}

.tr {
    text-align: right;
}

.f5 {
    font-size: 1rem;
}

.f6 {
    font-size: .875rem;
}

.measure {
    max-width: 30em;
}

.center {
    margin-right: auto;
    margin-left: auto;
}

@media screen and (min-width: 30em) {
    .pb3-ns {
        padding-bottom: 1rem;
    }

    .ph3-ns {
        padding-left: 1rem;
        padding-right: 1rem;
    }

    .f4-ns {
        font-size: 1.25rem;
    }
}

@media screen and (min-width: 30em) and (max-width: 60em) {
    .w-50-m {
        width: 50%;
    }
}

@media screen and (min-width: 60em) {
    .w-25-l {
        width: 25%;
    }
}


</style>
