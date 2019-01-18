<template>
  <div id="app">
    <h1>Telephone Input Vue</h1>
    <h2 style="color: #999">made with &#x2764; by Steven.</h2>

    <div>
      Debug Config
      <input type="text" v-model="displayFormat" placeholder="Display Format"/>
      <input type="text" v-model="outputFormat" placeholder="Output Format"/>
    </div>

    <div style="width: 500px; margin: 20px auto;">
      <vue-tel-input v-model="myPhoneNumber" @onInput="onInput" :preferredCountries="['us', 'gb', 'ua']" :displayFormat="displayFormat" :outputFormat="outputFormat"></vue-tel-input>
    </div>
    <div style="color: #e83e8c">
      <span>
        Output:
        <strong>{{ myPhoneNumber }}</strong>,&nbsp;
      </span>
    </div>
    <div v-if="phone.number" style="color: #e83e8c">
      <span>
        Number:
        <strong>{{ phone.number }}</strong>,&nbsp;
      </span>
      <span>
        Is valid:
        <strong>{{ phone.isValid }}</strong>,&nbsp;
      </span>
      <span>
        Country:
        <strong>{{ phone.country }}</strong>
      </span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data() {
    return {
      myPhoneNumber: '',
      phone: {
        number: '',
        isValid: false,
        country: undefined,
      },
      displayFormat : 'International',
      outputFormat : 'International'
    };
  },
  methods: {
    onInput({ number, isValid, country }) {
      this.phone.number = number;
      this.phone.isValid = isValid;
      this.phone.country = country && country.name;
    },
  },
};
</script>
