<template>
  <form @submit.prevent="handleSubmit">
    <label>Email:</label>
    <input type="email" required v-model="email" />

    <label>Password:</label>
    <input
      type="password"
      required
      v-model="password"
      @keyup="handlePasswordValidate"
    />
    <div class="error" v-if="passwordError">{{ passwordError }}</div>

    <label>Role:</label>
    <select v-model="role">
      <option value="default">Select an option</option>
      <option value="developer">Web developer</option>
      <option value="designer">Web designer</option>
    </select>

    <div class="terms">
      <input type="checkbox" required v-model="terms" />
      <label>Accept Terms and Conditions</label>
    </div>

    <div>
      <input type="checkbox" value="alex" v-model="names" />
      <label>Alex</label>
    </div>

    <div>
      <input type="checkbox" value="mario" v-model="names" />
      <label>Mario</label>
    </div>

    <div>
      <input type="checkbox" value="steven" v-model="names" />
      <label>Steven</label>
    </div>

    <label> Skills:</label>
    <input type="text" v-model="tempSkill" @keyup="addSkill" />

    <div
      v-for="skill in skills"
      :key="skill"
      class="pill"
      @click="removeSkill(skill)"
    >
      {{ skill }} x
    </div>
    <div class="submit">
      <button>Submit Information</button>
    </div>
  </form>
</template>

<script>
export default {
  name: "SignUpForm",
  data() {
    return {
      email: "",
      password: "",
      role: "default",
      terms: false,
      names: [],
      tempSkill: "",
      skills: [],
      passwordError: "",
    };
  },
  methods: {
    addSkill(e) {
      if (e.key === "," && this.tempSkill) {
        this.tempSkill = this.tempSkill.slice(0, this.tempSkill.length - 1);

        if (!this.skills.includes(this.tempSkill)) {
          this.skills.push(this.tempSkill);
        }

        this.tempSkill = "";
      }
    },
    removeSkill(skill) {
      this.skills = this.skills.filter((el) => el !== skill);
    },
    handleSubmit() {
      this.passwordError =
        this.password.length > 5
          ? ""
          : "Password must be at least 6 characters long";
    },
    handlePasswordValidate() {
      if (this.password.length > 5) {
        this.passwordError = "";
      }
    },
  },
};
</script>

<style>
form {
  max-width: 420px;
  margin: 30px auto;
  background: white;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
}
label {
  color: #aaa;
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 0.7em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
input,
select {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid #ddd;
  color: #555;
}
input:focus {
  outline-color: #000;
}

input[type="checkbox"] {
  display: inline-block;
  width: 16px;
  margin: 0 10px 0 0;
  position: relative;
  top: 2px;
}

.pill {
  color: indigo;
  display: inline-block;
  padding: 6px 12px;
  background-color: #eee;
  border-radius: 20px;
  font-size: 12px;
  letter-spacing: 10px;
  font-weight: bold;
  cursor: pointer;
  margin: 20px 10px 0 0;
}

button {
  background-color: #0b6dff;
  border: 0;
  padding: 10px 20px;
  margin-top: 20px;
  color: white;
  border-radius: 20px;
}
.submit {
  text-align: center;
}

.error {
  color: #ff0062;
  margin-top: 10px;
  font-weight: bold;
}
</style>
