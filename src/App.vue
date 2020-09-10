<template>
  <div id="app" class="small-container">
    <h1>SAN-M Tech Employees</h1>
    <employee-form @add:employee="addEmployee"/>
    <employee-table :employees="employees" @delete:employee="deleteEmployee"  />
  </div>
</template>

<script>
  import EmployeeTable from '@/components/EmployeeTable.vue'
  import EmployeeForm from '@/components/EmployeeForm.vue'

  export default {
    name: 'app',
    components: {
      EmployeeTable,
      EmployeeForm,
    },
    data() {
    return {
      employees: [
        {
          id: 1,
          name: 'Nsubuga Muhamood',
          email: 'nmuhamood3@gmail.com',
        },
        {
          id: 2,
          name: 'Lubwama Acram',
          email: 'acramlins@gmail.com',
        },
        {
          id: 3,
          name: 'Ssenfuka Ashiraf',
          email: 'ssenfukaa@yahoo.com',
        },
      ],
    }
  },
    methods: {
  addEmployee(employee) {
    const lastId =
    this.employees.length > 0
      ? this.employees[this.employees.length - 1].id
      : 0;
  const id = lastId + 1;
  const newEmployee = { ...employee, id };
    this.employees = [...this.employees, newEmployee]
  }
},

  mounted() {
    this.getEmployees()
  },
  editEmployee(id, updatedEmployee) {
      this.employees = this.employees.map(employee =>
        employee.id === id ? updatedEmployee : employee
      );
    },
   deleteEmployee(id) {
    this.employees = this.employees.filter(
      employee => employee.id !== id
    )
  }
  
  }
</script>

<style>
  button {
  background: #009435;
  border: 1px solid #009435;
}

button:hover,
button:active,
button:focus {
  background: #32a95d;
  border: 1px solid #32a95d;
}

.small-container {
  max-width: 680px;
}
</style>