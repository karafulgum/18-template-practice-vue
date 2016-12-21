<template lang="html">
  <div class="section">
    <div class="container">
      <form @submit.prevent="submitForm" class="panel">
        <p class="panel-heading">
          Sign Up For My Web App
        </p>
        <div class="panel-block">
          <p class="control has-icon" v-for="formInput in formInputs">
            <template v-if="formInput.type === 'select'" v-model="formValues[formInput.id]">
              <span class="select is-fullwidth">
                <select>
                  <option v-for="option in formInput.options">{{ option.label }}</option>
                </select>
              </span>
            </template>

            <template v-else>
              <template v-if="formInput.type === 'textarea'">
                <textarea class="input textarea" :placeholder="formInput.label" v-model="formValues[formInput.id]"></textarea>
                <i :class="formInput.icon" class="fa" aria-hidden="true"></i>
              </template>
              <template v-else>
                <input class="input" :placeholder="formInput.label" v-model="formValues[formInput.id]">
                <i :class="formInput.icon" class="fa" aria-hidden="true"></i>
              </template>
            </template>
          </p>
        </div>
        <div class="panel-block">
          <button class="button is-primary is-fullwidth">Submit</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
const apiUrl = 'http://json-data.herokuapp.com/forms';

export default {
  data() {
    return {
      formInputs: [],
      formValues: {},
      apiUrl: apiUrl,
    };
  },

  mounted() {
    this.getData();
  },

  methods: {
    getData() {
      fetch(`${apiUrl}`)
      .then((r) => r.json())
      .then((formInputs) => {
        this.formInputs = formInputs;
      });
    },
    submitForm(formValues) {
      fetch('http://tiny-tn.herokuapp.com/collections/form-kara>', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify(this.formValues)
      })
      .then(() => {
        console.log(formValues);
        this.formValues = formValues;
      });
    },
  },
};
</script>
