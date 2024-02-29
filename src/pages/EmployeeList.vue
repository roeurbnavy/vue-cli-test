<template>
  <div>
    <EmplpoyeeForm @add-employee="addEmployee" />
    <h1>Employee List</h1>
    <div class="employee-list">
      <table>
        <thead>
          <tr>
            <th>Name</th>
            <th>Gender</th>
            <th>DOB</th>
            <th>Position</th>
            <th>Action</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(employee, index) in employees" :key="index">
            <td>{{ employee.name }}</td>
            <td>{{ employee.gender }}</td>
            <td>{{ employee.dob }}</td>
            <td>{{ employee.position }}</td>
            <td><button @click="deleteEmployee(index)">Delete</button></td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
import EmplpoyeeForm from "../components/EmployeeForm.vue";

export default {
  components: {
    EmplpoyeeForm,
  },
  setup() {
    const employees = ref([]);

    const deleteEmployee = (index) => {
      employees.value.splice(index, 1);
    };

    const addEmployee = (value) => {
      employees.value.push(value);
    };

    return {
      employees,
      deleteEmployee,
      addEmployee,
    };
  },
};
</script>

<style scoped>
.employee-list {
  max-width: 800px;
  margin: 20px auto;
}

.employee-list table {
  width: 100%;
  border-collapse: collapse;
}

.employee-list th,
.employee-list td {
  padding: 10px;
  border: 1px solid #ddd;
  text-align: left;
}

.employee-list th {
  background-color: #f2f2f2;
}

.employee-list button {
  padding: 8px 12px;
  background-color: #dc3545;
  color: #fff;
  border: none;
  border-radius: 3px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.employee-list button:hover {
  background-color: #c82333;
}
h1 {
  text-align: center;
}
</style>
