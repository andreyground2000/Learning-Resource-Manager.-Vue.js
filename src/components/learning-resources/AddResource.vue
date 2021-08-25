<template>
   <base-dialog v-if="inputIsInvalid" title="Invalid Input" @close="confirmError">
        <template #default>
            <p>Unfortunately, at least one input value is invalid.</p>
            <p>Please make sure that you enter in each input at least a few characters.</p>
        </template>
        <template #actions>
            <base-button @click="confirmError">Okay</base-button>
        </template>
   </base-dialog>
   <base-card>
        <form @submit.prevent="addResource">
            <div class="form-control">
                <label for="title">Title</label>
                <input type="text" id="title" name="title" v-model="enteredValues.title">
            </div>
            <div class="form-control">
                <label for="description">Description</label>
                <textarea rows="3" id="description" name="description" v-model="enteredValues.description"></textarea>
            </div>
            <div class="form-control">
                <label for="link">Link</label>
                <input type="url" id="link" name="link" v-model="enteredValues.link">
            </div>
            <div>
                <base-button type="submit">Add resource</base-button>
            </div>
        </form>
   </base-card> 
</template>

<script>
import BaseButton from '../UI/BaseButton.vue';
import BaseDialog from '../UI/BaseDialog.vue';
export default {
  components: { BaseDialog, BaseButton },
    inject:['submitResource'],
    data() {
        return {
            enteredValues: {
                title: "",
                description: "",
                link: "",
            },
            inputIsInvalid: false
        };
    },
    methods: {
        addResource() {
            const { title, description, link } = this.enteredValues;
            if (title.trim() === "" || description.trim() === "" || link.trim() === "") {
                this.inputIsInvalid = true;
                return;
            }
            this.submitResource(title, description, link);
        },
        confirmError() {
            this.inputIsInvalid = false;
        }
    },
}
</script>

<style>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>

