<script setup lang="ts">
import { ref, computed, watch, onMounted } from 'vue'

// ---------------------------------------------------------------------------
// Day 1 Part A — reactivity and templates
// ---------------------------------------------------------------------------

// TODO Day 1A: a) replace with your own name and bio
const name = 'Christa'
const bio =
  'UX research with focus on medical/health care. Programming: mainly working with php and javascript.'

// TODO Day 1A: b) replace with your own skills
const skills = ref(['JavaScript', 'PHP', 'HTML', 'CSS'])

const newSkill = ref('')

function addSkill() {
  // TODO Day 1A: f) push newSkill.value into skills, then clear the input
  //console.log('addSkill:', newSkill.value)
  skills.value.push(newSkill.value)
  newSkill.value = ''
}

// ---------------------------------------------------------------------------
// Day 1 Part B — computed, watch, onMounted
// ---------------------------------------------------------------------------

// TODO Day 1B: add a computed property `skillCount` that returns the number
// of skills — hint: skills.value.length
// const skillCount = computed(() => ...)

// TODO Day 1B: use onMounted to load saved skills from localStorage
// (key: 'portfolio-skills') — hint: JSON.parse() to convert back to an array
// onMounted(() => { ... })

// TODO Day 1B: use watch to save skills to localStorage whenever the list changes
// hint: JSON.stringify() to convert the array to a string, { deep: true } option
// watch(skills, (val) => { ... }, { deep: true })

// ---------------------------------------------------------------------------
// Bonus
// ---------------------------------------------------------------------------

function removeSkill(index: number) {
  // TODO Bonus: remove the skill at the given index from the skills array
  skills.value.splice(index, 1)
}
</script>

<template>
  <section class="hero">
    <!-- TODO Day 1A: c) render name and bio -->
    <h1>{{ name }}</h1>
    <p class="bio">{{ bio }}</p>

    <!-- TODO Day 1B: replace the hardcoded "Skills" heading with
         "Skills ({{ skillCount }})" once you've added the computed -->
    <h3>Skills</h3>
    <ul class="skills">
      <!-- TODO Day 1A: d) Render the skills list using "li" + `v-for`
             CH: doppelpunkt vor key für Reaktiviät; key angeben, damit jeder eintrag einen key hat (für löschen u.ä. notwendig) und damit jeder Eintrag einen key hat, ist es skill und nicht skills - bei skills wäre es nur ein key für alle skills-->
      <!-- Bonus: <button @click="removeSkill(skills.indexOf(skill))">×</button> -->
      <li v-for="skill in skills" :key="skill">
        {{ skill }}
        <button @click="removeSkill(skills.indexOf(skill))">×</button>
      </li>
    </ul>

    <!-- TODO Day 1A: e) wire up v-model and the addSkill button
         Bonus: text-input should also add skill on <ENTER> -->
    <!-- TODO Day 1A: just for showing first output: Remove when implementation of v-for is done -->
    <div class="add-skill">
      <input v-model="newSkill" placeholder="Add a skill…" @keyup.enter="addSkill" />
      <button @click="addSkill">Add</button>
    </div>
    <!-- TODO Day 1A: just for debugging: Remove when implementation is ready -->
    <div class="placeholder">{{ newSkill }}</div>
  </section>
</template>
