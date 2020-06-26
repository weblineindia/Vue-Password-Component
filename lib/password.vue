<!-- *************************************************************************

This File will be used to Password field

************************************************************************* -->
<template>
  <div>
    <div v-show="!hide">
      <input
        :id="id"
        v-model="value"
        v-validate="'min:3'"
        :name="name"
        :tabindex="tabindex"
        :placeholder="placeholder"
        :type="passwordFieldType"
        class="form-control w-94"
        :disabled="disabled"
        :maxlength="paswordMaxLength"
        @focus="onFocus($event)"
        @input="onChangePassword($event)"
        @blur="onBlurMethod($event)"
        @keypress.enter.prevent
      />

      <span v-show="isViewPassword">
        <span v-show="value" class="password-eye">
          <span v-show="passwordFieldType === 'text'">
            <font-awesome-icon icon="eye" class="pointer" @click.prevent="passwordVisibility" />
          </span>
          <span v-show="passwordFieldType === 'password'">
            <font-awesome-icon
              icon="eye-slash"
              class="pointer"
              @click.prevent="passwordVisibility"
            />
          </span>
        </span>
      </span>
      <div v-if="errors.items.length > 0">
        <div v-for="(error, key) in errors.items" :key="key">
          <p
            v-show="error.rule === 'min' && error.field === name"
            :class="{ control: true, 'error-msg mt-2': true }"
          >
            <span v-show="error.rule === 'min' && error.field === name">{{passwordErrorName}}</span>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<!-- *************************************************************************

SCRIPT

************************************************************************* -->
<script>
import * as Regex from "./regex.js";
import Vue from "vue";

// for load font awesome
import { library } from "@fortawesome/fontawesome-svg-core";
import {
  faPlus,
  faMinus,
  faCircle,
  faClone,
  faEye,
  faEyeSlash
} from "@fortawesome/free-solid-svg-icons";
import "@fortawesome/fontawesome-svg-core/styles.css";
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
library.add(faPlus, faMinus, faCircle, faClone, faEye, faEyeSlash);
Vue.component("font-awesome-icon", FontAwesomeIcon);

// for load vuelidate
import * as VeeValidate from "vee-validate";
import Vuelidate from "vuelidate";

Vue.use(Vuelidate);
Vue.use(VeeValidate, {
  events: "change|blur"
});

export default {
  components: {},
  props: {
    paswordMaxLength: {
      type: Number,
      default: 255
    },
    passwordFieldType: {
      type: String,
      default: "password"
    },
    name: {
      type: String,
      default: "password"
    },
    passwordErrorName: {
      type: String,
      default: "The password field must be at least 3 characters"
    },
    isViewPassword: {
      type: Boolean,
      default: true
    },
    value: {
      type: String,
      default: ""
    },
    placeholder: {
      type: String,
      default: "password"
    },
    hide: {
      type: Boolean,
      default: false
    },
    tabindex: {
      type: Number,
      default: 1
    },
    id: {
      type: String,
      default: "password"
    }
  },
  data() {
    return {};
  },

  methods: {
    /**
     * On change password event
     */
    onChangePassword(event) {
      if (this.value.trim() === "") {
        this.value = this.value
          .replace(Regex.ALPHABATICS_NUMERICS_REGEX_WITHOUT_SPACE, "")
          .trim();
      }
      this.$validator.reset();
      this.$emit("change", this.value, this.id);
    },
    /**
     * On Blur event
     */
    onBlurMethod() {
      this.$emit("blur", event, this.placeholder, this.errors.has(this.name));
    },
    /**
     * Password visibility method
     */
    passwordVisibility() {
      this.passwordFieldType =
        this.passwordFieldType === "password" ? "text" : "password";
    },
    /**on focus password */

    onFocus(event) {
      this.$emit("focus", event);
    }
  }
};
</script>
<style  scoped>
@import './style.css';
</style>
