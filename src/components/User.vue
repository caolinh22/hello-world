<template>
  <div>
    {{ titleConverted }} <br />
    {{ students.length }}
    <Table :columns="columns" :data="students" />
  </div>
</template>

<script>
import Table from "../components/Table";

export default {
  name: "Student",
  components: {
    Table,
  },
  data() {
    return {
      title: "user management",
      students: [],
      columns: [
        {
          label: "Id",
          field: "id",
        },
        {
          label: "Name",
          field: "name",
        },
        {
          label: "Username",
          field: "username",
        },
        {
          label: "Email",
          field: "email",
        },
      ],
    };
  },
  mounted() {
    this.loadStudent();
  },
  methods: {
    loadStudent() {
      fetch("https://jsonplaceholder.typicode.com/users")
        .then((response) => response.json())
        .then((data) => (this.students = data));
    },
  },
  computed: {
    titleConverted() {
      return this.title.toUpperCase();
    },
  },
};
</script>

<style scoped>
.error {
  color: red;
}
</style>