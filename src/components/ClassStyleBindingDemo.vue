<template>
    <div class="container">
        <h2>Class bindings</h2>
        <p :class="{ 'blue-color': isBlueColor }">Background color of this sentence is blue</p>
        <p class="normal-class" :class="{ 'blue-color': isBlueColor }">This sentence has plain class as well as :class
            directive</p>
        <p :class="[isNormalClass, isRedColorClass]">:class directive is bound to an array to apply multiple classes</p>
        <p :class="[isYellowColorClass ? 'yellow-color-class' : 'green-color-class']">Toggle Yellow and green color classes
        </p><button @click="toggleClasses">Toggle</button>

        <h2>Style bindings</h2>
        <p :style="{ color: 'red' }">Bind red color to this sentence</p>
        <p :style="[isActive ? { color: 'blue' } : { color: 'red' }]">Toggle between red and blue color</p>
        <button @click="isActive ? isActive = false : isActive = true">Toggle</button>
    </div>
</template>

<script setup>
import { ref } from 'vue';
const isBlueColor = ref(true);
const isRedColorClass = ref('red-color-class');
const isNormalClass = ref('normal-class');
const isGreenColorClass = ref(true);
const isYellowColorClass = ref(false);
const isActive = ref(true);
function toggleClasses() {

    if (isYellowColorClass.value) {
        isYellowColorClass.value = false;
        isGreenColorClass.value = true;
    } else {
        isYellowColorClass.value = true;
        isGreenColorClass.value = false;
    }
}

</script>

<style scoped>
.container {
    border: 1px solid white;
    text-align: center;
}

.blue-color {
    color: blue;
}

.normal-class {
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    font-size: large;
}

.red-color-class {
    color: red;
}

.green-color-class {
    color: green;
}

.yellow-color-class {
    color: yellow;
}
</style>