<template>
  <div :class="getClasses">
    <input-text
      v-if="
        formControl.type === 'text' ||
        formControl.type === 'email' ||
        formControl.type === 'password' ||
        formControl.type === 'url' ||
        formControl.type === 'number'
      "
      :formControl="formControl"
      @change="valueChange"
      :style="getStyles"
    />
    <input-textarea
      v-if="formControl.type === 'textarea'"
      :formControl="formControl"
      @change="valueChange"
      :style="getStyles"
    />
    <input-select
      v-if="formControl.type === 'select'"
      :formControl="formControl"
      @change="valueChange"
      :style="getStyles"
    />
    <input-checkbox
      v-if="formControl.type === 'checkbox'"
      :formControl="formControl"
      @change="valueChange"
      :style="getStyles"
    />
    <input-radio
      v-if="formControl.type === 'radio'"
      :formControl="formControl"
      @change="valueChange"
      :style="getStyles"
    />
    <slot
      v-if="formControl.type === 'custom-field'"
      :name="'custom-field'"
      :control="formControl"
      :valueChange="valueChange"
      :onFocus="onFocus"
      :onBlur="onBlur"
      :style="getStyles"
    />
    <label
      class="form-label"
      :for="formControl.name"
      v-if="formControl.type !== 'checkbox'"
    >
      {{ formControl.label }}
    </label>
    <span class="form-bar"></span>
    <p class="form-hint" v-if="formControl.helper">
      {{ formControl.helper }}
    </p>
    <div v-if="showErrors">
      <p
        v-for="(errorText, $index) in errorMessages"
        :key="`${$index}`"
        class="error"
      >
        {{ errorText }}
      </p>
    </div>
  </div>
</template>
<script src="./DynamicInput.js"></script>
