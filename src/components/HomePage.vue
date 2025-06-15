<script>
export default {
  data() {
    return {
      students: [],
      id: 0,
      name: "",
      city: "",
      isEdit: false
    };
  },
  created() {
    this.getStudents();
  },
  methods: {
    async getStudents() {
      const res = await fetch("http://localhost:3000/students");
      const data = await res.json();
      this.students = data;
    },
    async addStudent() {
      if (!this.id || !this.name || !this.city) return;

      const newStudent = {
        id: this.id,
        name: this.name,
        city: this.city
      };

      await fetch("http://localhost:3000/students", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(newStudent)
      });

      this.getStudents();
      this.resetForm();
    },
    async deleteStudent(id) {
      await fetch(`http://localhost:3000/students/${id}`, {
        method: "DELETE"
      });

      this.getStudents();
    },
    editStudent(student) {
      this.id = student.id;
      this.name = student.name;
      this.city = student.city;
      this.isEdit = true;
      my_modal_1.showModal();
    },
    async updateStudent() {
      const updated = {
        id: this.id,
        name: this.name,
        city: this.city
      };

      await fetch(`http://localhost:3000/students/${this.id}`, {
        method: "PUT",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(updated)
      });

      this.getStudents();
      this.resetForm();
    },
    resetForm() {
      this.id = 0;
      this.name = "";
      this.city = "";
      this.isEdit = false;
    }
  }
};
</script>

<template>
  <div class="p-8">
    <div class="flex gap-3 justify-center items-center mb-4"> 
      <h1 class="text-3xl font-bold">Students List</h1>
      <p class="text-xl text-gray-500">({{ students.length }})</p>
    </div>

    <div class="flex justify-center mb-4">
      <button class="btn btn-primary" onclick="my_modal_1.showModal();">Add Student</button>
    </div>

    <div class="overflow-x-auto">
      <table class="table w-full">
        <thead>
          <tr>
            <th>ID</th>
            <th>Name</th>
            <th>City</th>
            <th>Actions</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="student in students" :key="student.id">
            <td>{{ student.id }}</td>
            <td>{{ student.name }}</td>
            <td>{{ student.city }}</td>
            <td class="flex gap-2">
              <button @click="editStudent(student)" class="btn btn-sm btn-warning">Edit</button>
              <button @click="deleteStudent(student.id)" class="btn btn-sm btn-error">Delete</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>

    <!-- Modal -->
    <dialog id="my_modal_1" class="modal">
      <div class="modal-box">
        <h3 class="font-bold text-lg">{{ isEdit ? 'Edit' : 'Add' }} Student</h3>

        <form method="dialog" class="space-y-3 mt-4">
          <input v-model="id" type="number" placeholder="Student ID" class="input input-bordered w-full" :disabled="isEdit">
          <input v-model="name" type="text" placeholder="Student Name" class="input input-bordered w-full">
          <input v-model="city" type="text" placeholder="Student City" class="input input-bordered w-full">

          <div class="modal-action">
            <div class="flex gap-3">
              <button
                type="button"
                class="btn"
                @click="isEdit ? updateStudent() : addStudent()"
              >
                {{ isEdit ? 'Update' : 'Add' }}
              </button>
              <button class="btn" @click="resetForm">Close</button>
            </div>
          </div>
        </form>
      </div>
    </dialog>
  </div>
</template>
