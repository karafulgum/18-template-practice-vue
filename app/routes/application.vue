<template lang="html">
  <div class="section">
    <div class="container">
      <nav class="panel">
        <p class="panel-heading">
          Sign Up For My Web App
        </p>
        <div class="panel-block" href="#">
          <p class="control has-icon">
            <input class="input" type="text" placeholder="First Name">
            <i class="fa fa-user" aria-hidden="true"></i>
          </p>
          <p class="control has-icon">
            <input class="input" type="text" placeholder="Last Name">
            <i class="fa fa-user" aria-hidden="true"></i>
          </p>
          <p class="control has-icon">
            <input class="input" type="text" placeholder="Email Address">
            <i class="fa fa-envelope" aria-hidden="true"></i>
          </p>
          <p class="control has-icon">
            <input class="input" type="text" placeholder="Current website url">
            <i class="fa fa-globe" aria-hidden="true"></i>
          </p>
          <p class="control">
            <span class="select is-fullwidth">
              <select>
                <option>English</option>
                <option>Spanish</option>
                <option>French</option>
                <option>Italian</option>
              </select>
            </span>
          </p>
          <p class="control has-icon">
            <textarea class="input textarea" placeholder="Your Comment"></textarea>
            <i class="fa fa-comments" aria-hidden="true"></i>
          </p>
          <p class="control has-icon">
            <input class="input" type="text" placeholder="Mobile Number">
            <i class="fa fa-mobile" aria-hidden="true"></i>
          </p>
          <p class="control has-icon">
            <input class="input" type="text" placeholder="Home Number">
            <i class="fa fa-phone" aria-hidden="true"></i>
          </p>
          <a class="button is-primary is-fullwidth">Submit</a>
        </div>
      </nav>
    </div>
  </div>
</template>

<script>
const apiUrl = 'http://json-data.herokuapp.com/forms';

export default {
  data() {
    return {
      formInputs: [],
      formValues: [],
      apiUrl: apiUrl,
    };
  },

  methods: {
    getData() {
      fetch(`${apiUrl}`)
      .then((r) => r.json())
      .then((formInputs) => {
        this.formInputs = formInputs;
      });
    },
    submitForm() {

    },
  },
};
</script>
