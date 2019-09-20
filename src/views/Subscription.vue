<template>
  <FormSchema :schema="schema" v-model="model" :components="components" ref="formSchema">
    <div class="operation">
      <el-button type="primary" @click="submit">Subscribe</el-button>
      <el-button @click="cancel">cancel</el-button>
    </div>
  </FormSchema>
</template>

<script>
  import FormSchema, { Components } from '@formschema/native'
  import ElementUIComponents from '../ElementUIComponents'

  export default {
    data: () => ({
      schema: require('../schema/Formschema1.json'),
      model: {},
      components:ElementUIComponents(Components)
    }),
    methods: {
      submit(e) {
        console.log(JSON.stringify(this.model));
        this.$emit('submit', e);
        e.preventDefault();
      },
      cancel(e) {
        this.$emit('cancel', e);
      }
    },
    components: {
      FormSchema
    }
  }
</script>
