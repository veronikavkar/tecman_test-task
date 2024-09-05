<template>
  <label class="custom-checkbox">
    <input
      type="checkbox"
      :checked="modelValue"
      @change="handleChange"
      ref="checkbox"
    />
    <span class="checkmark"></span>
  </label>
</template>

<script>
export default {
  name: "CustomCheckbox",
  props: {
    modelValue: {
      type: Boolean,
      default: false,
    },
    indeterminate: {
      type: Boolean,
      default: false,
    },
  },
  mounted() {
    this.updateIndeterminateState();
  },
  watch: {
    indeterminate(val) {
      this.updateIndeterminateState();
    },
  },
  methods: {
    updateIndeterminateState() {
      this.$refs.checkbox.indeterminate = this.indeterminate;
    },
    handleChange(event) {
      this.$emit("update:modelValue", event.target.checked);
    },
  },
};
</script>

<style scoped>
.custom-checkbox input[type="checkbox"] {
  position: absolute;
  opacity: 0;
  cursor: pointer;
}

.custom-checkbox {
  display: inline-block;
  position: relative;
  cursor: pointer;
}

.custom-checkbox .checkmark {
  position: absolute;
  top: -16px;
  left: 0;
  height: 18px;
  width: 18px;
  background-color: #ffffff;
  border: 2px solid #888888;
  border-radius: 4px;
  transition: background-color 0.3s, border-color 0.3s;
}

.custom-checkbox input[type="checkbox"]:checked + .checkmark {
  background-color: #a53863;
  border-color: #a53863;
}

.custom-checkbox .checkmark:after {
  content: "";
  position: absolute;
  display: none;
  left: 5px;
  top: 1px;
  width: 6px;
  height: 10px;
  border: solid white;
  border-width: 0 2px 2px 0;
  transform: rotate(45deg);
}

.custom-checkbox input[type="checkbox"]:checked + .checkmark:after {
  display: block;
}
/* Стиль для состояния indeterminate (минус) */
.custom-checkbox input[type="checkbox"]:indeterminate + .checkmark {
  background-color: #a53863;
  border-color: #a53863;
}

.custom-checkbox input[type="checkbox"]:indeterminate + .checkmark:before {
  content: "";
  position: absolute;
  width: 10px;
  height: 2px;
  background-color: white;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  display: block;
}
.custom-checkbox input[type="checkbox"]:indeterminate + .checkmark:after {
  display: none;
}

@media screen and (max-width: 590px) {
  .custom-checkbox .checkmark {
    height: 14px;
    width: 14px;
  }
  .custom-checkbox .checkmark:after {
    left: 4px;
    top: -1px;
  }
}
@media screen and (max-width: 480px) {
  .custom-checkbox .checkmark:after {
    left: 4px;
    top: 1px;
    width: 4px;
    height: 7px;
  }
  .custom-checkbox .checkmark {
    height: 12px;
    width: 12px;
  }
  @media screen and (max-width: 424px) {
    .custom-checkbox .checkmark {
      display: none;
    }
  }
}
</style>
