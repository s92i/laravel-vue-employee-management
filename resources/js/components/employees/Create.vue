<template>
    <div>

        <div class="container">
            <div class="row justify-content-center">
                <div class="col-md-8">
                    <div class="card">
                        <div class="card-header">
                            Create employees
                            <router-link :to="{ name: 'EmployeesIndex' }" class="float-right">Back</router-link>
                        </div>

                        <div class="card-body">
                            <form>

                                <div class="form-group row">
                                    <label for="first_name" class="col-md-4 col-form-label text-md-end">First
                                        name</label>

                                    <div class="col-md-6">
                                        <input id="first_name" type="text" class="form-control" name="name" required>
                                    </div>
                                </div>

                                <div class="form-group row">
                                    <label for="middle_name" class="col-md-4 col-form-label text-md-end">Middle
                                        name</label>

                                    <div class="col-md-6">
                                        <input id="middle_name" type="text" class="form-control" name="name" required>
                                    </div>
                                </div>

                                <div class="form-group row">
                                    <label for="last_name" class="col-md-4 col-form-label text-md-end">Last
                                        name</label>

                                    <div class="col-md-6">
                                        <input id="last_name" type="text" class="form-control" name="name" required>
                                    </div>
                                </div>

                                <div class="form-group row">
                                    <label for="address" class="col-md-4 col-form-label text-md-end">Address</label>

                                    <div class="col-md-6">
                                        <input id="address" type="text" class="form-control" name="name" required>
                                    </div>
                                </div>

                                <div class="form-group row">
                                    <label for="country" class="col-md-4 col-form-label text-md-right">Country</label>
                                    <div class="col-md-6">
                                        <select name="country" class="form-control" aria-label="Select a country">
                                            <option selected>Select a country</option>
                                        </select>
                                    </div>
                                </div>

                                <div class="form-group row">
                                    <label for="state" class="col-md-4 col-form-label text-md-right">State</label>
                                    <div class="col-md-6">
                                        <select name="state" class="form-control" aria-label="Select a state">
                                            <option selected>Select a state</option>
                                        </select>
                                    </div>
                                </div>

                                <div class="form-group row">
                                    <label for="department"
                                        class="col-md-4 col-form-label text-md-right">Department</label>
                                    <div class="col-md-6">
                                        <select name="department" class="form-control" aria-label="Select a department">
                                            <option selected>Select a department</option>
                                        </select>
                                    </div>
                                </div>

                                <div class="form-group row">
                                    <label for="city" class="col-md-4 col-form-label text-md-right">City</label>
                                    <div class="col-md-6">
                                        <select name="city" class="form-control" aria-label="Select a city">
                                            <option selected>Select a city</option>
                                        </select>
                                    </div>
                                </div>

                                <div class="form-group row">
                                    <label for="zip_code" class="col-md-4 col-form-label text-md-end">Zip
                                        code</label>

                                    <div class="col-md-6">
                                        <input id="zip_code" type="text" class="form-control" name="name" required>
                                    </div>
                                </div>

                                <div class="row mb-0">
                                    <div class="col-md-6 offset-md-4">
                                        <button type="submit" class="btn btn-primary">
                                            Store
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
export default {

}
</script>

<style>

</style>