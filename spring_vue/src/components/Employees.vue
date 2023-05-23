<template>
  <div class="container">
    <h1 class="text-center">Список сотрудников</h1>
    <table class="table table-striped">
      <thead>
        <th>Id</th>
        <th>Имя</th>
        <th>Фамилия</th>
        <th>Email</th>
      </thead>
      <tbody>
        <tr v-for="employee in employees" v-bind:key="employee.Id">
          <td>{{ employee.id }}</td>
          <td>{{ employee.firstName }}</td>
          <td>{{ employee.lastName }}</td>
          <td>{{ employee.email }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import EmployeeService from "../services/EmployeeService";

export default {
  name: "Employees",
  data() {
    return {
        employees : []
    }    
  },
  methods: {
    getEmployees() {
      EmployeeService.getEmployees().then((response) => {
        this.employees = response.data;
      });
    },
  },
  created() {
    this.getEmployees();
  },
};
</script>