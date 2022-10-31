<template>
  <div>
    <h1>fullwidth-halfwidth</h1>
    <table>
      <thead>
        <tr>
          <th>
            <b>text to convert</b>
          </th>
        </tr>
        <tr>
          <th>
            <textarea v-model="textToConvert" placeholder="edit me"></textarea>
          </th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>
            <button @click="clear()">clear</button>
            <button @click="paste()">paste</button>
            <button @click="convert()">convert</button>
          </td>
        </tr>
        <tr>
          <td>
            <b>fullwidth</b>
          </td>
          <td>
            <b>halfwidth</b>
          </td>
        </tr>
        <tr>
          <td>
            <textarea v-model="fullWidth"></textarea>
          </td>
          <td>
            <textarea v-model="halfWidth"></textarea>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      textToConvert: '',
      fullWidth: '',
      halfWidth: ''
    }
  },
  methods: {
    clear() {
      this.textToConvert = ''
      this.fullWidth = ''
      this.halfWidth = ''
    },
    async paste() {
      this.textToConvert = await navigator.clipboard.readText()
    },
    convert() {
      const src = this.textToConvert
      this.fullWidth = src
      this.halfWidth = src
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 40px;
  margin-left: 30px;
  margin-right: 30px;
}

table {
  background: #f2f2f2;
  border-radius: 5px;
  border-style: solid;
  border-width: 1px;
  border-color: #d9d9d9;
  padding: 10px;
  width: 100%;
}

th {
  text-align: left;
}

td {
  width: 50%;
}

button {
  font-size: 1rem;
  margin-left: 5px;
  margin-right: 5px;
  margin-bottom: 50px;
}

textarea {
  min-height: 100px;
  height: 100%;
  width: 95%;
}
</style>
