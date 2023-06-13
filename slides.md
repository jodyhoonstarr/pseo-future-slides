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

# Q&A
