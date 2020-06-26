# Vue-password-component

A Vue password component is provide to add password as a text/password property with validation.
The password value is automatically validated on blur event.
You can also disable and hide password field using disable and hide  props.

## Table of contents

- [Browser Support](#browser-support)
- [Demo](#demo)
- [Getting started](#getting-started)
- [Usage](#usage)
- [Available Props](#available-props)
- [Methods](#methods)
- [Want to Contribute?](#want-to-contribute)
- [Need Help / Support?](#need-help)
- [Collection of Components](#collection-of-components)
- [Changelog](#changelog)
- [License](#license)
- [Keywords](#Keywords)

## Browser Support

| ![Chrome](https://raw.github.com/alrra/browser-logos/master/src/chrome/chrome_48x48.png) | ![Firefox](https://raw.github.com/alrra/browser-logos/master/src/firefox/firefox_48x48.png) | ![Safari](https://raw.github.com/alrra/browser-logos/master/src/safari/safari_48x48.png) | ![Edge](https://raw.github.com/alrra/browser-logos/master/src/edge/edge_48x48.png) | ![IE](https://raw.github.com/alrra/browser-logos/master/src/archive/internet-explorer_9-11/internet-explorer_9-11_48x48.png) |
| ---------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| 83.0 ✔                                                                                   | 77.0 ✔                                                                                      | 13.1.1 ✔                                                                                 | 83.0 ✔                                                                             | 11.9 ✔                                                                                                                       |

## Demo

[![](password.gif)](https://github.com/weblineindia/Vue-Password-Component/password.gif)

## Getting started

Install the npm package:

```bash
npm install vue-weblineindia-password
#OR
yarn add vue-weblineindia-password
```

## Usage

Use the `<vue-weblineindia-password>` component:

```vue
<template>
  <div>
    <password
      id="password"
      name="password"
      :tabindex="1"
      :placeholder="'password'"
      :hide="false"
      :value="passwordValue"
      :disabled="false"
      :is-view-password="true"
      :passwordFieldType="'password'"
      @change="onChangePassword"
      @blur="onBlur"
      @focus="onFocus"
    />
  </div>
</template>

<script>
import password from "vue-weblineindia-password";
export default {
  components: { password },
  data: function() {
    return {
      passwordValue: ""
    };
  },

  methods: {
    /** on change password*/
    onChangePassword(value, id) {
      this.passwordValue = value;
    },

    /** on blur password field*/
    onBlur(event, placeholder, errorObj) {
      event.target.placeholder = placeholder;
    },

    /** on focus password field*/
    onFocus(event) {
      event.target.placeholder = "";
    }
  }
};
</script>
```

## Available Props

| Prop           | Type    | default     | Description        |
| -------------- | ------- | ----------- | ------------------ |
| paswordMaxLength          | Number  |    255         | max length for password          |
| passwordFieldType     | String  | password    | field type of password(like text or password)           |
| passwordErrorName | String  |  The password field must be at least 3 characters           | error name for password      |
| placeholder    | String  | password | password placeholder    |
| disabled       | Boolean | false       | disable password field  |
| name           | String  | password | name for password field |
| tabindex       | Number  | 1           | password tabIndex       |
| id             | String  | password | name for password field |
| hide           | Boolean | false       | for hide password field |
| isViewPassword           | Boolean | true       | To hide/show eye icon |
| value           | String |        | value for password  |
| hide           | Boolean | false       | for hide password field |


## Methods

| Name     | Description                                             |
| -------- | ------------------------------------------------------- |
| focus    | Gets triggered when the password input field receives focus. |
| blur   | Gets triggered when the password input field loses focus.    |
| change | Gets triggered every time password got changed.              |

## Want to Contribute?

- Created something awesome, made this code better, added some functionality, or whatever (this is the hardest part).
- [Fork it](http://help.github.com/forking/).
- Create new branch to contribute your changes.
- Commit all your changes to your branch.
- Submit a [pull request](http://help.github.com/pull-requests/).

---

## Need Help?

We also provide a free, basic support for all users who want to use this VueJS password Component in their software project. In case you want to customize this VueJS password Component to suit your development needs, then feel free to contact our [VueJS developers](https://www.weblineindia.com/hire-vuejs-developer.html).

---

## Collection of Components

We have built many other components and free resources for software development in various programming languages. Kindly click here to view our [Free Resources for Software Development](https://www.weblineindia.com/software-development-resources.html)

---

## Changelog

Detailed changes for each release are documented in [CHANGELOG.md](./CHANGELOG.md).

## License

[MIT](LICENSE)

[mit]: https://github.com/weblineindia/Vue-Password-Component/blob/master/LICENSE

## Keywords

vue-weblineindia-password,password,vue components,vuejs,vuejs component
