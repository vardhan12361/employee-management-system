<template>
  <div>
    <div class="card p-4 mb-4">
      <h4 class="mb-3 text-primary">
        {{ isEditing ? "Update Employee" : "Add Employee" }}
      </h4>

      <div class="row">
        <div class="col-md-6">
          <input v-model="employee.name" class="form-control mb-3" placeholder="Name" />
        </div>

        <div class="col-md-6">
          <input v-model="employee.designation" class="form-control mb-3" placeholder="Designation" />
        </div>

        <div class="col-md-6">
          <input v-model="employee.department" class="form-control mb-3" placeholder="Department" />
        </div>

        <div class="col-md-6">
          <input v-model="employee.salary" type="number" class="form-control mb-3" placeholder="Salary" />
        </div>
      </div>

      <div class="text-end">
        <button class="btn btn-success me-2" @click="saveEmployee">
          {{ isEditing ? "Update" : "Add" }}
        </button>

        <button v-if="isEditing" class="btn btn-secondary" @click="resetForm">
          Cancel
        </button>
      </div>
    </div>

    <table class="table table-striped">
      <thead>
        <tr>
          <th>ID</th>
          <th>Name</th>
          <th>Designation</th>
          <th>Department</th>
          <th>Salary</th>
          <th>Actions</th>
        </tr>
      </thead>

      <tbody>
        <tr v-for="emp in employees" :key="emp.id">
          <td>{{ emp.id }}</td>
          <td>{{ emp.name }}</td>
          <td>{{ emp.designation }}</td>
          <td>{{ emp.department }}</td>
          <td>{{ emp.salary }}</td>
          <td>
            <button class="btn btn-warning btn-sm me-2" @click="editEmployee(emp)">
              ✏️
            </button>
            <button class="btn btn-danger btn-sm" @click="deleteEmployee(emp.id)">
              🗑️
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from "axios";

const API_URL = "https://69f87620f7044aa0103de2da.mockapi.io/employees";

export default {
  data() {
    return {
      employees: [],
      employee: {
        id: null,
        name: "",
        designation: "",
        department: "",
        salary: ""
      },
      isEditing: false
    };
  },

  mounted() {
    this.fetchEmployees();
  },

  methods: {
    async fetchEmployees() {
      const res = await axios.get(API_URL);
      this.employees = res.data;
    },

    async saveEmployee() {
      if (this.isEditing) {
        await axios.put(`${API_URL}/${this.employee.id}`, this.employee);
      } else {
        await axios.post(API_URL, this.employee);
      }
      this.fetchEmployees();
      this.resetForm();
    },

    editEmployee(emp) {
      this.employee = { ...emp };
      this.isEditing = true;
    },
    resetForm() {
      this.employee = {
        id: null,
        name: "",
        designation: "",
        department: "",
        salary: ""
      };
      this.isEditing = false;
    },
    async deleteEmployee(id) {
  if (confirm("Are you sure you want to delete this employee?")) {
    try {
      await axios.delete(`${API_URL}/${id}`);
      alert("Employee deleted successfully");
      this.fetchEmployees();
    } catch (error) {
      console.error(error);
      alert("Error deleting employee");
    }
  }
}
  }
};
</script>