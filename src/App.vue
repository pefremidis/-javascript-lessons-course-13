<template>
    <div id="app">
        <div class="container">
            <div class="mt-5">
                <label for="firstname" class="form-label">Firstname</label>
                <input v-model="firstname" type="text" class="form-control" :class="[!firstnameValidation ? 'border border-danger' : '']" id="firstname" placeholder="John">
                <span v-if="!firstnameValidation" class="text-danger fs-6 fst-italic">The field is required</span>
            </div>

            <div class="mt-2">
                <label for="lastname" class="form-label">Lastname</label>
                <input v-model="lastname" id="lastname" :class="[!lastnameValidation ? 'border border-danger' : '']" type="text" class="form-control" placeholder="Doe"/>
                <span v-if="!lastnameValidation" class="text-danger fs-6 fst-italic">The field is required</span>
            </div>

            <div class="mt-5">
                <button @click="submit" type="button" class="btn btn-primary">Submit</button>
            </div>


            <div class="mt-5">
                <h3>Formulate</h3>

                <FormulateForm v-model="form">
                    <FormulateInput
                        type="text"
                        name="firstname"
                        label="First Name"
                        validation="required|min:3"/>

                    <FormulateInput
                        type="text"
                        name="lastname"
                        label="Last Name"
                        validation="required|min:5"/>

                    <FormulateInput @click="submitFormulate"
                        type="submit"
                        label="Submit"/>
                </FormulateForm>
            </div>
        </div>

    </div>
</template>

<script>

    export default {
        name: 'App',

        data() {
            return {
                firstname: '',
                firstnameValidation: true,
                lastname: '',
                lastnameValidation: true,

                form: {
                    firstname: '',
                    lastname: ''
                }
            }
        },

        methods: {
            submit() {
                this.firstnameValidation = true;
                this.lastnameValidation = true;

                if (this.firstname.length === 0) {
                    this.firstnameValidation = false;
                }

                if (this.lastname.length === 0) {
                    this.lastnameValidation = false;
                }
            },

            submitFormulate() {
                console.log(this.form);
            }
        }
    }
</script>
