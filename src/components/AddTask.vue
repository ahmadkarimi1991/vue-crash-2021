<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label for="">Task</label>
      <input type="text" v-model="text" name="text" placeholder="Add Task" />
    </div>
    <div class="form-control">
      <label for="">Day & Time</label>
      <input
        type="text"
        v-model="day"
        name="day"
        placeholder="Add Day & Time"
      />
    </div>
    <div class="form-control form-control-check">
      <label for="">Set Reminder</label>
      <input type="checkbox" v-model="reminder" name="reminder" />
    </div>
    <input type="submit" value="Save Task" class="btn btn-block" />
  </form>
</template>

<script>
export default {
  name: "AddTask",
  data() {
    return {
      text: '',
      day: '',
      reminder: false
    }
  },
  methods: {
    onSubmit(event) {
      event.preventDefault();

      // Let's do some validation
      if (!this.text) {
        alert('Please add a task');
        return;
      }

      const newTask = {
        // id: Math.floor(Math.random() * 100000),
        text: this.text,
        day: this.day,
        reminder: this.reminder,
      }

      this.$emit('add-task', newTask)

      this.text = '';
      this.day = '';
      this.reminder = false;
    }
  },
};
</script>

<style scoped>
.add-form {
  margin-bottom: 2.5rem;
}

.form-control {
  margin: 1.25rem 0;
}

.form-control label {
  display: block;
}
.form-control input {
  width: 100%;
  height: 2.5rem;
  margin: 0.5rem 0;
  padding: 0.25rem 0.5rem;
  font-size: 1rem;
}

.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.form-control-check label {
  flex: 1;
}

.form-control-check input {
  flex: 2;
  height: 1.25rem;
}
</style>
