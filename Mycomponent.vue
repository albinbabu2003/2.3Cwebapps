<template>
  <div>
    <h1>Hello World</h1>

    <!-- 1. Template Syntax -->
    <div class="section">
      <!-- a. Text Interpolation -->
      <p>{{ greeting }}</p>

      <!-- b. Raw HTML [v-html] -->
      <p v-html="rawHTML"></p>

      <!-- c. Attribute Bindings [v-bind:id] -->
      <div :id="elementId">Dynamic ID Element</div>

      <!-- d. JavaScript expressions inside syntax i.e.{{ }} -->
      <p>{{ 3 * 5 }}</p>
    </div>

    <!-- 2. Methods -->
    <div class="section">
      <button class="button" @click="sayHello">Say Hello</button>
    </div>

    <!-- 3. Reactivity Fundamentals [ref(), <script setup>] -->
    <div class="section">
      <p>{{ count }}</p>
      <button class="button" @click="incrementCount">Increment Count</button>
    </div>

    <!-- 4. Computed Properties -->
    <div class="section">
      <p>Computed Property: {{ doubleCount }}</p>
    </div>

    <!-- 5. Class and Style Bindings -->
    <div class="section">
      <!-- a. Binding HTML class [v-bind:class] -->
      <div :class="{'active': isActive, 'error': hasError}">Conditional Classes</div>

      <!-- b. Binding Inline Styles [v-bind:style] -->
      <div :style="{'color': textColor, 'font-size': fontSize + 'px'}">Inline Styles</div>
    </div>

    <!-- 6. List Rendering -->
    <div class="section">
      <!-- a. v-for with an Object -->
      <ul>
        <li v-for="(value, key) in myObject">{{ key }}: {{ value }}</li>
      </ul>

      <!-- b. v-for with a Range -->
      <ul>
        <li v-for="n in 3">{{ n }}</li>
      </ul>

      <!-- c. v-for on <template> -->
      <template v-for="item in items">
        <p>{{ item }}</p>
      </template>

      <!-- d. v-for with v-if -->
      <ul>
        <li v-for="item in itemsWithConditions" v-if="item.condition">{{ item.text }}</li>
      </ul>
    </div>

    <!-- 7. Event Handling: Listening to Events [v-on:click] -->
    <div class="section">
      <!-- a. Inline Handlers -->
      <button class="button" @click="showAlert">Show Alert (Inline)</button>

      <!-- b. Method Handlers -->
      <button class="button" @click="handleButtonClick">Custom Event Handler</button>
    </div>

    <!-- 8. Form Input Bindings -->
    <div class="section">
      <input class="input" type="text" v-model="textInput" placeholder="Type something">
      <br>
      <label class="checkbox-label">
        <input type="checkbox" v-model="isChecked"> Check this
      </label>
      <br>
      <label class="radio-label">
        <input type="radio" v-model="selectedRadio" value="option1"> Option 1
      </label>
      <label class="radio-label">
        <input type="radio" v-model="selectedRadio" value="option2"> Option 2
      </label>
      <br>
      <select class="input" v-model="selectedOption">
        <option value="option1">Option 1</option>
        <option value="option2">Option 2</option>
      </select>
      <br>
      <textarea class="input" v-model="textareaInput" placeholder="Enter text"></textarea>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // 1. Template Syntax
      greeting: "Hello, Vue!",
      rawHTML: "<em>Rendered as HTML</em>",
      elementId: "my-dynamic-element",

      // 2. Methods
      sayHello() {
        alert("Hello!");
      },

      // 3. Reactivity Fundamentals
      count: 0,
      incrementCount() {
        this.count++;
      },

      // 4. Computed Properties
      // Computed properties are defined below using computed().

      // 5. Class and Style Bindings
      isActive: true,
      hasError: false,
      textColor: "green",
      fontSize: 20,

      // 6. List Rendering
      myObject: { x: 1, y: 2, z: 3 },
      items: ["Item A", "Item B", "Item C"],
      itemsWithConditions: [
        { text: "Show me", condition: true },
        { text: "Hide me", condition: false },
      ],

      // 8. Form Input Bindings
      textInput: "",
      isChecked: false,
      selectedRadio: "",
      selectedOption: "",
      textareaInput: "",
    };
  },
  computed: {
    // 4. Computed Properties
    doubleCount() {
      return this.count * 2;
    },
  },
  methods: {
    // 7. Event Handling: Listening to Events
    showAlert() {
      alert("Inline Handler: Hello!");
    },
    handleButtonClick() {
      this.$emit("customEvent");
    },
  },
};
</script>
