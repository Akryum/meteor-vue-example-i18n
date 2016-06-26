<template>
<div class="app">
  <h1>{{$t('title')}}</h1>
  <locale-select></locale-select>
</div>
</template>

<script>
import {LocaleSelect} from 'meteor/akryum:vue-i18n-ui';

export default {
  components: {
    LocaleSelect
  }
}
</script>
