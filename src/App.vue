<template>
  <div class="container mt-4">
    <h2 class="text-center mb-4">Employee Management System</h2>
    <EmployeeManager />
  </div>
</template>

<script>
import EmployeeManager from "./components/EmployeeManager.vue";

export default {
  components: { EmployeeManager }
};
</script>

<style>
body {
  background: linear-gradient(135deg, #667eea, #764ba2);
  font-family: 'Poppins', sans-serif;
  min-height: 100vh;
  color: #2d2d2d;
}

h2 {
  font-weight: 700;
  color: #ffffff;
  letter-spacing: 1px;
}

.container {
  max-width: 1100px;
}

/* Card */
.card {
  border-radius: 20px;
  backdrop-filter: blur(10px);
  background: rgba(255, 255, 255, 0.85);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.2);
  border: none;
}

/* Inputs */
input {
  border-radius: 12px !important;
  border: 1px solid #ddd !important;
  padding: 10px;
  transition: 0.3s;
}

input:focus {
  border-color: #667eea !important;
  box-shadow: 0 0 8px rgba(102, 126, 234, 0.4);
}

/* Buttons */
.btn {
  border-radius: 12px;
  padding: 8px 15px;
  font-weight: 500;
  transition: all 0.3s ease;
}

.btn-success {
  background: linear-gradient(to right, #43cea2, #185a9d);
  border: none;
}

.btn-warning {
  background: linear-gradient(to right, #f7971e, #ffd200);
  border: none;
  color: #000;
}

.btn-danger {
  background: linear-gradient(to right, #ff416c, #ff4b2b);
  border: none;
}

.btn-secondary {
  background: #6c757d;
  border: none;
}

.btn:hover {
  transform: translateY(-2px);
  opacity: 0.9;
}

/* Table */
.table {
  border-radius: 15px;
  overflow: hidden;
  background: white;
}

.table th {
  background: linear-gradient(to right, #667eea, #764ba2);
  color: white;
  text-align: center;
  padding: 12px;
}

.table td {
  text-align: center;
  padding: 10px;
}

/* Hover effect */
tr:hover {
  background-color: #f0f4ff;
  transition: 0.3s;
}
</style>