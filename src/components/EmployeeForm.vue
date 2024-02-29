<template>
  <h1>Add New Employee</h1>
  <div class="employee-form">
    <label for="name">Name:</label>
    <input type="text" id="name" v-model="form.name" /><br />
    Gender:<input
      type="radio"
      id="male"
      value="Male"
      v-model="form.gender"
    />Male
    <input
      type="radio"
      id="female"
      value="Female"
      v-model="form.gender"
    />Female
    <input type="radio" id="other" value="Other" v-model="form.gender" />Other
    <label for="dob">DOB:</label>
    <input type="date" id="dob" v-model="form.dob" /><br />
    <label for="position">Position:</label>
    <select id="position" v-model="form.position">
      <option v-for="(it, key) in positionOpts" :key="key" :value="it.value">
        {{ it.label }}
      </option>
    </select>
    <br />
    <button @click="addEmployee">Add New</button>
  </div>
</template>

<script>
import { ref, defineEmits } from "vue";

export default {
  setup(_, { emit }) {
    const initForm = ref({
      name: "",
      gender: "Male",
      dob: new Date(),
      position: "",
    });
    const form = ref({ ...initForm.value });

    const positionOpts = [
      { label: "Web Developer", value: "Web Developer" },
      { label: "Software Developer", value: "Software Developer" },
      { label: "Full-stack Developer", value: "Full-stack Developer" },
      { label: "Networking", value: "Networking" },
      { label: "UX/UI Designer", value: "UX/UI Designer" },
    ];

    const addEmployee = () => {
      // Emit to parent
      emit("addEmployee", form.value);
      // Reset
      form.value = initForm.value;
    };

    return {
      ...defineEmits(["addEmployee"]),
      form,
      positionOpts,
      addEmployee,
    };
  },
};
</script>

<style scoped>
.employee-form {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #f9f9f9;
}

.employee-form label {
  display: block;
  margin-bottom: 5px;
}

.employee-form input[type="text"],
.employee-form input[type="date"],
.employee-form select {
  width: calc(100% - 12px);
  padding: 8px;
  margin-bottom: 10px;
  border: 1px solid #ccc;
  border-radius: 3px;
}

.employee-form button {
  padding: 10px 20px;
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 3px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.employee-form button:hover {
  background-color: #0056b3;
}
h1 {
  text-align: center;
}
</style>
