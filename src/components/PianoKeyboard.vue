<script setup lang="ts">
defineProps<{
  msg: string
}>()

interface Note {
  name: string
  frequency: number
  latinName: string
  englishName: string
}

const notes: Note[] = [
  {
    name: 'C',
    frequency: 261.63,
    latinName: 'Do',
    englishName: 'C'
  },
  {
    name: 'C#',
    frequency: 277.18,
    latinName: 'Do#',
    englishName: 'C Sharp'
  },
  {
    name: 'D',
    frequency: 293.66,
    latinName: 'Ré',
    englishName: 'D'
  },
  {
    name: 'D#',
    frequency: 311.13,
    latinName: 'Ré#',
    englishName: 'D Sharp'
  },
  {
    name: 'E',
    frequency: 329.63,
    latinName: 'Mi',
    englishName: 'E'
  },
  {
    name: 'F',
    frequency: 349.23,
    latinName: 'Fa',
    englishName: 'F'
  },
  {
    name: 'F#',
    frequency: 369.99,
    latinName: 'Fa#',
    englishName: 'F Sharp'
  },
  {
    name: 'G',
    frequency: 392.0,
    latinName: 'Sol',
    englishName: 'G'
  },
  {
    name: 'G#',
    frequency: 415.3,
    latinName: 'Sol#',
    englishName: 'G Sharp'
  },
  {
    name: 'A',
    frequency: 440.0,
    latinName: 'La',
    englishName: 'A'
  },
  {
    name: 'A#',
    frequency: 466.16,
    latinName: 'La#',
    englishName: 'A Sharp'
  },
  {
    name: 'B',
    frequency: 493.88,
    latinName: 'Si',
    englishName: 'B'
  }
]

console.log(notes)

interface Interval {
  name: string
  ratio: string
  semitones: number
  symbol: string
  frequency: number
}

const referenceFrequency: number = 440

const intervals: Interval[] = [
  {
    name: 'Unison', // Root notes
    ratio: '1/1',
    symbol: '',
    semitones: 0,
    frequency: calculateFrequency(0)
  },
  {
    name: 'Seconde mineure',
    ratio: '10⁄9',
    symbol: '2m',
    semitones: 1,
    frequency: calculateFrequency(1)
  },
  {
    name: 'Seconde majeure',
    ratio: '9⁄8',
    symbol: '2M',
    semitones: 2,
    frequency: calculateFrequency(2)
  },
  {
    name: 'Tierce Mineure',
    ratio: '6/5',
    symbol: '3m',
    semitones: 3,
    frequency: calculateFrequency(3)
  },
  {
    name: 'Tierce Majeure',
    ratio: '5/4',
    symbol: '3M',
    semitones: 4,
    frequency: calculateFrequency(4)
  },
  {
    name: 'Quarte',
    ratio: '4⁄3',
    symbol: '4j',
    semitones: 5,
    frequency: calculateFrequency(5)
  },
  {
    name: 'Quinte diminuée',
    ratio: '64/45',
    symbol: '5dim',
    semitones: 6,
    frequency: calculateFrequency(6)
  },
  {
    name: 'Quinte Juste',
    ratio: '3⁄2',
    symbol: '5j',
    semitones: 7,
    frequency: calculateFrequency(7)
  },
  {
    name: 'Sixte mineure',
    ratio: '8⁄5',
    symbol: '6m',
    semitones: 8,
    frequency: calculateFrequency(8)
  },
  {
    name: 'Sixte majeure',
    symbol: '6M',
    ratio: '5/3',
    semitones: 9,
    frequency: calculateFrequency(9)
  },
  {
    name: 'Septième mineure',
    symbol: '7m',
    ratio: '16/9',
    semitones: 10,
    frequency: calculateFrequency(10)
  },
  {
    name: 'Septième majeure',
    symbol: '7M',
    ratio: '15/8',
    semitones: 11,
    frequency: calculateFrequency(11)
  },
  {
    name: 'octave',
    symbol: '8v',
    ratio: '2/1',
    semitones: 12,
    frequency: calculateFrequency(12)
  }
]

// Fonction pour calculer la fréquence d'une note en fonction du nombre de demi-tons par rapport à la note de référence
function calculateFrequency(semitones: number): number {
  return referenceFrequency * Math.pow(2, semitones / 12)
}

console.log(intervals)

function playNote(note: string) {
  var audio = document.getElementById(`note-${note}`)
  audio.currentTime = 0
  audio.play()
}
</script>

<template>
  <div class="piano">
    <div>Hello i am a piano</div>
    <ul class="keyboard">
      <li @click="playNote(note)" class="touches" v-for="(note, i) in notes" :key="i">
        {{ note }}
      </li>
    </ul>
    <audio src="la.wav"></audio>
    <audio v-for="(note, i) in notes" :id="`note-${note}`" :key="i" :src="`/${note}.wav`"></audio>
  </div>
</template>

<style scoped>
.touches {
  border: silver 1px solid;
  padding: 5px;
}

.touches:hover {
  background-color: lightgray;
  cursor: pointer;
}
</style>
