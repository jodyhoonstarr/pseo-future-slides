---
layout: cover
highlighter: shiki
css: unocss
colorSchema: dark
transition: fade-out
---

<h1 flex="~ col">
<div class="text-gradient text-6xl font-bold">PSEO</div>
<div flex="~ gap3" items-center text-4xl>Planning data and application futures</div>
</h1>

<div uppercase text-sm tracking-widest>
Pitching the idea, not the implementation
</div>

<div abs-br mx-10 my-12 flex="~ col" text-sm text-right>
  <div text-sm opacity-50>June 14th 2023</div>
</div>

---
layout: center
class: text-center
growX: 50
growY: -20
---

# Why change?

<div class="leading-10 opacity-80">
Expand number of institution partners. Expand the userbase.<br>
Lower friction for data and app users.<br>
More focus on infrequent data users.
</div>

---
growX: 50
growY: -80
growSize: 2
class: h-full flex flex-col justify-center
---

# PSEO User Base

<v-clicks>

- Institution Admins

- Data Savvy Public

- Desktop Browser

- Excel

- English Language

</v-clicks>

---
growX: 50
growY: -80
growSize: 2
class: h-full flex flex-col justify-center
---

# Targeting New Users/Partners

<v-clicks>

- Mobile first

- Text heavy, plain language, interactive articles with visualizations

- Integrate docs with data

- English/Spanish Language

- Direct non-partner institutions show how to join

</v-clicks>

---

# What content should be provided

<v-clicks>

- Both earnings and counts

- Counts show change over time

- Grad employment rate (dependent on w2 data)

- Explain why data not available

- Show expected release years/dates

  - e.g. latest cohort: 2016-2018, 2019-2021 expected in ????

</v-clicks>

<v-click>
<div class="text-gradient pt-8 font-bold">
Research: Relatedness 
</div>

- Which institutions/degrees/etc. are related?

- Cross link in app

</v-click>

---
layout: intro
class: text-center pb-5
growX: 50
growY: 120
---

## Mockup, for clarity

Using published data, nothing new

---

## Example

<img class="h-full abs-tr" src="/earnings_ut_eng.png" >

---

## Including Flows

<img class="h-full abs-tr" src="/counts_ut_eng.png" >

---

## Employment rate

- hidden away currently

- Contingent on w2 earnings data

<img class="h-full abs-tr" src="/counts_ut_eng_emppct.png" >

---


## Spanish

<img class="h-full abs-tr" src="/earnings_ut_eng_sp.png" >

---

# How the margins fit in

<v-clicks>

- <span class="text-gradient">/institution</span> - all institutions

  - popular institutions
  - highest earning institutions (margins)

- <span class="text-gradient">/institution-CU</span> - single institution

  - margins/aggregate earnings (by degree level?)
  - n grads (employment rate?)
  - popular/highest earning programs
  - related institutions

</v-clicks>
<v-clicks>
<div class="pt-4 text-gradient">/institution-CU/degreelevel</div>  
<div class="text-gradient">/institution-CU/degreelevel-BA</div>  
<div class="text-gradient">/institution-CU/degreelevel-BA/program</div>  
<div class="text-gradient">/institution-CU/degreelevel-BA/program-ENG</div>  
<div class="text-gradient">/institution-CU/degreelevel-BA/program-ENG/detailedprogram</div>  
</v-clicks>
---


# Top level margin examples

<v-clicks>

- <span class="text-gradient">/detailedprogram-COMPENG</span> - overview (e.g. computer eng)

  - aggregate earnings
  - institutions offering
  - related programs

- <span class="text-gradient">/state-TX</span> - overview 

  - map of institutions and size
  - aggregate earnings
  - instate employment from counts
  - popular programs/institutions

- <span class="text-gradient">/industry-CONSTRUCTION</span>

  - popular institutions contributing grads
  - aggregate earnings

</v-clicks>

---

## Public Data

#### What we have now, simplified


<v-click>

Categorical Variables:

```ts
state = 'Colorado'
institution = 'University of Colorado'
degree_level = 'BA'
program_detail = 'general'
program = 'Engineering'
cohort = '*'
```

</v-click>
<v-click>

Earnings Data:

| years after graduation | 25% | 50% | 75%
| :----: | :------: | :----: | :----:
| 1  | $45k | $61k | $75k
| 5 | $66k | $83k | $103k
| 10 | $81k | $105k | $135K

```ts
25% 45 66 81
```

</v-click>

---

## Public Data

#### What we need


<v-click>

Margins across institution:

```ts
state = 'Colorado'
institution = '*' // <-- All institutions
degree_level = 'BA'
program_detail = 'general'
program = 'Engineering'
cohort = '*'
```

Earnings Data:

| years after graduation | 25% | 50% | 75%
| :----: | :------: | :----: | :----:
| 1  | ? | ? | ?
| 5 | ? | ? | ?
| 10 | ? | ? | ?

```ts
25% 45 66 81
```


</v-click>

---

## Public Data

#### What we need


<v-click>

Margins for all BA Engineers:

```ts
state = '*' // <-- All States
institution = '*' // <-- All institutions
degree_level = 'BA'
program_detail = 'general'
program = 'Engineering'
cohort = '*'
```

</v-click>

<v-click>

Margins generic BA:

```ts
state = '*' // <-- All States
institution = '*' // <-- All institutions
degree_level = 'BA'
program_detail = 'general'
program = '*' // <-- All programs, not just engineers
cohort = '*'
```

</v-click>

---

## Public Data

#### Changes required

<div mt4/>

<v-click>
<div class="text-gradient font-bold">
Margins only - no changes to privacy budget
</div>
</v-click>

<v-click>

What we have:

```ts
pseoe_all.csv
pseof_all.csv
pseoe_ak.csv
pseof_ak.csv
//...
```

</v-click>
<v-click>

What we need:

```ts
// Construct BDS style tables
pseo_earnings_us
pseo_earnings_us_degreelevel
pseo_earnings_us_degreelevel_program
pseo_earnings_us_degreelevel_program_detailedprogram
pseo_earnings_tx
pseo_earnings_tx_degreelevel
//...
```

</v-click>

---

## Next Steps

<v-click>
<div class="text-gradient font-bold py-12">
Large project, long process, begin before w2 changes hit
</div>
</v-click>

<v-click>
TODOs:
</v-click>
<v-clicks>

- Create margins/aggregates from public use files

- Determine which are valuable, pass to prod

- Begin relatedness research

- Develop `routes` (e.g. `/state-TX/degreelevel-BA`) based on margins

- Generate rough mockups per route

- App development

</v-clicks>


---
layout: center
class: text-center
growX: 50
growY: -20
---

# ANTFU SLIDES BELOW FOR REFERENCE

---
layout: cover
---


<h1 flex="~ col">
<div>Developer Experience</div>
<div flex="~ gap3" items-center>with <span inline-block i-logos-nuxt-icon text-1.2em mb-2/> <b font-bold>Nuxt DevTools</b></div>
</h1>

<div uppercase text-sm tracking-widest>
Anthony Fu
</div>

<div abs-br mx-10 my-12 flex="~ col" text-sm text-right>
  <div>StrasbourgJS</div>
  <div text-sm opacity-50>May. 25th 2023</div>
</div>

---
layout: intro
growX: 50
growY: 90
style: 'padding-left: 8rem;'
---

# Anthony Fu

<div class="leading-10 opacity-80">
Core team member of Vue, Vite and Nuxt.<br>
Creator of VueUse, Vitest, UnoCSS, Slidev and Elk.<br>
Working at NuxtLabs.<br>
</div>

<div my-10 w-min flex="~ gap-1" items-center justify-center>
  <div i-ri-user-3-line op50 ma text-xl/>
  <div><a href="https://antfu.me" target="_blank" class="border-none! font-300">antfu.me</a></div>
  <div i-ri-github-line op50 ma text-xl ml4/>
  <div><a href="https://github.com/antfu" target="_blank" class="border-none! font-300">antfu</a></div>
  <div i-ri-mastodon-line op50 ma text-xl ml4/>
  <div><a href="https://m.webtoo.ls/@antfu" target="_blank" class="border-none! font-300">antfu@webtoo.ls</a></div>
  <div i-ri-twitter-line op50 ma text-xl ml4/>
  <div><a href="https://twitter.com/antfu7" target="_blank" class="border-none! font-300">antfu7</a></div>
</div>

<img src="https://antfu.me/avatar.png" rounded-full w-35 abs-tr mt-32 mr-40/>

<div flex="~ gap2">

</div>

---
layout: center
growX: 50
growY: 50
---

<h1 font-bold class="text-5xl!">Developer Experience</h1>

<div absolute left-100 top-80 v-click>File-based Routing</div>
<div absolute left-52 top-50 v-click>Modules Ecosystem</div>
<div absolute left-100 top-50 v-click>Hot Module Replacement</div>
<div absolute left-50 top-80 v-click>Server-side Rendering</div>

<v-click>

<div absolute left-158 top-50>Nitro</div>
<div absolute left-145 top-80>ESM First</div>
<div absolute left-170 top-80>Vite Powered</div>
<div absolute left-60 top-90 op80>Zero-config</div>
<div absolute left-90 top-90>Edge Rendering</div>

</v-click>
<v-click>

<div absolute left-85 top-40>Hybrid Rendering</div>
<div absolute left-130 top-90>Components Auto Imports</div>
<div absolute left-125 top-40 op70>Composables Auto Imports</div>
<div absolute left-55 top-40 op70>Middleware</div>
<div absolute left-175 top-50 op70>SEO</div>

</v-click>
<v-click>

<div absolute left-145 top-100 op60>Server API</div>
<div absolute left-100 top-30 op70>Serverless</div>
<div absolute left-70 top-30 op70>TypeScript</div>
<div absolute left-130 top-30 op70>Server Components</div>
<div absolute left-120 top-100 op70>Layouts</div>
<div absolute left-70 top-100 op60>Static Site Generation</div>

</v-click>

---
growX: 0
growY: 50
class: flex
---

<div my-auto w-full grid="~ cols-2 gap-5" px20>
<div flex="~ col gap-5">
<h1 v-click>Conventions</h1>
<h1 v-click>Abstractions</h1>
<h1 v-click>Sensible Defaults</h1>
<h1 v-click>Normalizations</h1>
</div>
<div flex="~ gap-5 items-center">
<h1 v-click class="text-right" w-full>Transparency</h1>
</div>
</div>

---
growX: 50
growY: -80
growSize: 2
class: h-full flex flex-col justify-center
---

# Transparency

<v-clicks>

- Easy to learn & understand

- Easy to modify

- Easy to debug

</v-clicks>

---
layout: 'center'
class: 'text-center'
growX: 50
growY: 10
---

<div v-click transition-all duration-500 :class="$slidev.nav.clicks === 0 ? 'op0' : $slidev.nav.clicks > 1 ? 'op50 text-2xl' : 'translate-y-10 text-4xl'">Introducing</div>

<div class="nuxt-devtools-logo" v-click>
  <NuxtDevTools h-20/>
</div>

---

<div ml-14 text-lg op50 mb--4>The goal of</div>
<h1><NuxtDevTools h-15/></h1>

<div text-2xl>
<v-clicks>

- Enhance your DX with Nuxt

- Improve Transparency

- Performance & analysis

- Interactive & playful

- Personalized documentations


</v-clicks>
</div>


---
layout: center
class: text-center
growX: 50
growY: 50
growSize: 0.4
---

<h1>Demo time!</h1>

---
layout: center
class: text-center
growX: 50
growY: 0
---

---
layout: center
class: text-center
growX: 10
growY: 90
---

# Open Sourced at

<Repo name="nuxt/devtools" />


---
layout: center
class: text-center
growX: 50
growY: -20
---

# Q&A


---
layout: intro
class: text-center pb-5
growX: 50
growY: 120
---

# Thank You!

Slides on [antfu.me](https://antfu.me)
