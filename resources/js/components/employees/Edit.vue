<template>
    <div>

        <div class="container">
            <div class="row justify-content-center">
                <div class="col-md-8">
                    <div class="card">
                        <div class="card-header">
                            Update employees
                            <router-link :to="{ name: 'EmployeesIndex' }" class="float-right">Back</router-link>
                        </div>

                        <div class="card-body">
                            <form @submit.prevent="updateEmployee">

                                <div class="form-group row">
                                    <label for="first_name" class="col-md-4 col-form-label text-md-end">First
                                        name</label>

                                    <div class="col-md-6">
                                        <input id="first_name" type="text" class="form-control" name="name"
                                            v-model="form.first_name" required>
                                    </div>
                                </div>

                                <div class="form-group row">
                                    <label for="middle_name" class="col-md-4 col-form-label text-md-end">Middle
                                        name</label>

                                    <div class="col-md-6">
                                        <input id="middle_name" type="text" class="form-control" name="name"
                                            v-model="form.middle_name" required>
                                    </div>
                                </div>

                                <div class="form-group row">
                                    <label for="last_name" class="col-md-4 col-form-label text-md-end">Last
                                        name</label>

                                    <div class="col-md-6">
                                        <input id="last_name" type="text" class="form-control" name="name"
                                            v-model="form.last_name" required>
                                    </div>
                                </div>

                                <div class="form-group row">
                                    <label for="address" class="col-md-4 col-form-label text-md-end">Address</label>

                                    <div class="col-md-6">
                                        <input id="address" type="text" class="form-control" name="name"
                                            v-model="form.address" required>
                                    </div>
                                </div>

                                <div class="form-group row">
                                    <label for="country" class="col-md-4 col-form-label text-md-end">Country</label>
                                    <div class="col-md-6">
                                        <select name="country" class="form-control" aria-label="Select a country"
                                            v-model="form.country_id" @change="getStates()">
                                            <option v-for="country in countries" :key="country.id" :value="country.id">
                                                {{ country.name }}
                                            </option>
                                        </select>
                                    </div>
                                </div>

                                <div class="form-group row">
                                    <label for="state" class="col-md-4 col-form-label text-md-end">State</label>
                                    <div class="col-md-6">
                                        <select name="state" class="form-control" aria-label="Select a state"
                                            v-model="form.state_id" @change="getCities()">
                                            <option v-for="state in states" :key="state.id" :value="state.id">
                                                {{ state.name }}
                                            </option>
                                        </select>
                                    </div>
                                </div>

                                <div class="form-group row">
                                    <label for="department"
                                        class="col-md-4 col-form-label text-md-end">Department</label>
                                    <div class="col-md-6">
                                        <select name="department" class="form-control" aria-label="Select a department"
                                            v-model="form.department_id">
                                            <option v-for="department in departments" :key="department.id"
                                                :value="department.id">{{ department.name }}</option>
                                        </select>
                                    </div>
                                </div>

                                <div class="form-group row">
                                    <label for="city" class="col-md-4 col-form-label text-md-end">City</label>
                                    <div class="col-md-6">
                                        <select name="city" class="form-control" aria-label="Select a city"
                                            v-model="form.city_id">
                                            <option v-for="city in cities" :key="city.id" :value="city.id">
                                                {{ city.name }}
                                            </option>
                                        </select>
                                    </div>
                                </div>

                                <div class="form-group row">
                                    <label for="zip_code" class="col-md-4 col-form-label text-md-end">Zip
                                        code</label>

                                    <div class="col-md-6">
                                        <input id="zip_code" type="text" class="form-control" name="name"
                                            v-model="form.zip_code" required>
                                    </div>
                                </div>

                                <div class="form-group row">
                                    <label for="zip_code" class="col-md-4 col-form-label text-md-end">Birthdate</label>
                                    <div class="col-md-6">
                                        <datepicker input-class="form-control" v-model="form.birthdate"></datepicker>
                                    </div>
                                </div>

                                <div class="form-group row">
                                    <label for="zip_code" class="col-md-4 col-form-label text-md-end">Date hired</label>
                                    <div class="col-md-6">
                                        <datepicker input-class="form-control" v-model="form.date_hired"></datepicker>
                                    </div>
                                </div>

                                <div class="form-group row mb-0 mt-4">
                                    <div class="col-md-6 offset-md-4">
                                        <button type="submit" class="btn btn-primary">
                                            Update
                                        </button>
                                    </div>
                                </div>
                            </form>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Datepicker from 'vuejs-datepicker'
import moment from 'moment'

export default {
    components: {
        Datepicker
    },
    data() {
        return {
            countries: [],
            states: [],
            departments: [],
            cities: [],
            form: {
                first_name: '',
                middle_name: '',
                last_name: '',
                address: '',
                country_id: '',
                state_id: '',
                department_id: '',
                city_id: '',
                zip_code: '',
                birthdate: null,
                date_hired: null
            }
        }
    },
    created() {
        this.getCountries()
        this.getDepartments()
        this.getEmployees()
    },
    methods: {
        getEmployees() {
            axios.get('/api/employees/' + this.$route.params.id).then(res => {
                this.form = res.data.data
                this.getStates()
                this.getCities()
            }).catch(error => {
                console.log(console.error)
            })
        },
        getCountries() {
            axios.get('/api/employees/countries').then(res => {
                this.countries = res.data
            }).catch(error => {
                console.log(console.error)
            })
        },
        getStates() {
            axios.get('/api/employees/' + this.form.country_id + '/states').then(res => {
                this.states = res.data
            }).catch(error => {
                console.log(console.error)
            })
        },
        getCities() {
            axios.get('/api/employees/' + this.form.country_id + '/cities').then(res => {
                this.cities = res.data
            }).catch(error => {
                console.log(console.error)
            })
        },
        getDepartments() {
            axios.get('/api/employees/departments').then(res => {
                this.departments = res.data
            }).catch(error => {
                console.log(console.error)
            })
        },
        updateEmployee() {
            axios.put('/api/employees' + this.$route.params.id, {
                first_name: this.form.first_name,
                middle_name: this.form.middle_name,
                last_name: this.form.last_name,
                address: this.form.address,
                country_id: this.form.country_id,
                state_id: this.form.state_id,
                city_id: this.form.city_id,
                department_id: this.form.department_id,
                zip_code: this.form.zip_code,
                birthdate: this.format_date(this.form.birthdate),
                date_hired: this.format_date(this.form.date_hired)
            }).then(res => {
                this.$router.push({ name: 'EmployeesIndex' })
            })
        },
        format_date(value) {
            if (value) {
                return moment(String(value)).format('YYYYMMDD')
            }
        }
    }
}
</script>

<style>

</style>