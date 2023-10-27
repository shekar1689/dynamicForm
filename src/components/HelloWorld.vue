<template>
  <div class="hello">
    <div>
      <div>
        <div>
          <form @submit.prevent="submitForm()">
            <div v-for="(item, index) in blocks" :key="index" class="form">
              <div v-if="item.type == 'text'" class="form-div">
                <label>{{ item.props.title }}</label>
                <input type="text" :placeholder="item.props.placeholder" :required="item.props.required" />
              </div>
              <div v-if="item.type == 'checkbox'" class="form-div">
                <label>{{ item.props.title }}</label>
                <input type="checkbox" :default="item.props.default" :required="item.props.required" />
              </div>
              <div v-if="item.type == 'date'" class="form-div">
                <label>{{ item.props.title }}</label>
                <input type="date" />
              </div>
              <div v-if="item.type == 'number'" class="form-div">
                <label>{{ item.props.title }}</label>
                <input type="number" :placeholder="item.props.placeholder" :required="item.props.required" />
              </div>
            </div>

            <button type="submit">submit</button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      blocks: [
        {
          "token": "Person_name",
          "type": "text",
          "props": {
            "title": "Enter your name",
            "required": true,
            "placeholder": "e.g. John Deo"
          }
        },
        {
          "token": "Is_Person_Minor",
          "type": "checkbox",
          "props": {
            "title": "Is the current Person Minor ?",
            "default": false
          }
        },
        {
          "token": "Person_DOB",
          "type": "date",
          "props": {
            "title": "Enter your DOB",
            "required": "Is_Person_Minor",
            "placeholder": "e.g.01/01/2000"
          }
        },
        {
          "token": "Person_Age",
          "type": "number",
          "props": {
            "title": "Enter your Age",
            "required": true,
            "placeholder": "e.g. 25"
          }
        },
      ]
    }
  },
  methods: {
    submitForm() {
      console.log('SUBMIT');
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

.form-div {
  display: flex;
  gap: 10px;
}

.form {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
