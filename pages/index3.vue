<template>
  <div class="container">
  <div class="bb">
  <a
  href="#"
  v-for="locale in availableLocales"
  :key="locale.code"
  @click.prevent.stop="$i18n.setLocale(locale.code)">{{ locale.name }}</a>
  </div>

<div>
<input class="input-phone" type="text"/>
</div>

    <div class="Chart">
      <h1 style="text-align: center">Chart Vue</h1>
      <bar-example />
    </div>
    <div class="ckeditor">
      <h1>ckeditoraa {{ $t('name') }}</h1>
    <ckeditor v-model="editorData" :config="editorConfig"></ckeditor>
    </div>
  </div>
</template>

<script>
import BarExample from '~/plugins/BarExample'
import Vue from 'vue'
import CKEditor from 'ckeditor4-vue'
Vue.use(CKEditor)




export default {
  layout(context) {
    return 'default2'
  },
  name: 'index',

computed: {
  availableLocales () {
    return this.$i18n.locales.filter(i => i.code !== this.$i18n.locale)
  }
},
  components: {
    BarExample,
  },
 data() {
            return {
        editorData: '<p>Content of the editor.</p>',
        editorConfig: {
        language : 'en',
            uiColor : '#AADC6E',  
            autoGrow_minHeight : 200,
        autoGrow_maxHeight : 600,
        autoGrow_bottomSpace : 50,
        magicline_color : '#000', 
            }
        }
   },
   }
</script>

<style>
.container {
  max-width: 800px;
  margin: 0 auto;
}

h1 {
  font-family: 'Helvetica', Arial;
  color: #464646;
  text-transform: uppercase;
  border-bottom: 1px solid #f1f1f1;
  padding-bottom: 15px;
  font-size: 28px;
  margin-top: 0;
}

.Chart {
  padding: 20px;
  box-shadow: 0px 0px 20px 2px rgba(0, 0, 0, 0.4);
  border-radius: 20px;
  margin: 50px 0;
}
</style>
