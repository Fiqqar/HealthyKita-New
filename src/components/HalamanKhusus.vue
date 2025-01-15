<template>
    <div class="d-flex justify-content-center align-items-center vh-100" style="background-color: #f4fdf4;">
        <div class="card shadow-sm" style="width: 24rem; border-radius: 40px; height: 478px;">
            <div class="card-body">
                <h3 class="card-title text-center mb-4" style="font-family: sans-serif;">Pertanyaan Mendalam</h3>
                <div class="mb-3" style="font-family: monospace;">
                    <label for="tall" class="form-label">Tinggi Badan</label>
                    <input type="text" id="tall" class="form-control" name="tall"
                        placeholder="Masukkan Tinggi Badan Kamu" v-model="userData.tall" required>
                </div>
                <div class="mb-3" style="font-family: monospace;">
                    <label for="weight" class="form-label">Berat Badan</label>
                    <input type="text" id="weight" class="form-control" placeholder="Masukkan Berat Badan Kamu"
                        name="weight" v-model="userData.weight" required>
                </div>
                <div class="mb-3" style="font-family: monospace; ">
                    <label for="birthdate" class="form-label">Masukkan Tanggal Lahir</label>
                    <input type="date" id="birthdate" class="form-control" name="birthdate" v-model="userData.birthdate"
                        required>
                </div>
                <div class="mb-3" style="font-family: monospace;">
                    <label for="intensActivity" class="form-label">Intensitas Aktivitas Dalam Seminggu</label>
                    <select name="intensActivity" id="intensActivity" class="form-control"
                        v-model="userData.intensActivity" required>
                        <option value="">Pilih Intensitas Aktivitas</option>
                        <option value="sedikit">Sedikit 1-3</option>
                        <option value="sedang">Sedang 3-5</option>
                        <option value="banyak">Banyak 5+</option>
                    </select>
                    <!-- <input type="text" id="intensActivity" class="form-control"
                        placeholder="Intensitas Aktivitas Kamu Dalam Seminggu" name="intensActivity" v-model="userData.intensActivity" required> -->
                </div>

                <button type="submit" class="btn btn-success w-100 animate"
                    style="border-radius: 40px; font-family: monospace;" @click="registerData"
                    :disabled="loading">Kirim</button>
            </div>
            <div v-if="loading" class="text-center">
                <p>harap tunggu...</p>
            </div>
            <h3 class="text-center" v-if="success && !loading">{{ response.message }}</h3>
            <h3 class="text-center" v-if="error && !loading">{{ response.message }}</h3>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import textFile from '!!raw-loader!./file.txt';
export default {
    name: 'HalamanKhusus',
    data() {
        return {
            arr: textFile,
            userData: {
                tall: "",
                weight: "",
                intensActivity: "",
                birthdate: "",

            },
            success: false,
            error: false,
            loading: false,
            response: {}
        };
    },
    methods: {
        registerData() {
            this.success = false;
            this.error = false;
            this.loading = true;
            const { tall, weight, intensActivity, birthdate } = this.userData;
            if (!tall || !weight || !intensActivity || !birthdate) {
                alert("Please fill out all required fields.");
                this.loading = false;
                return;
            }
            axios.post(`${ this.arr } / api / signup / user`, {
                tall: tall,
                weight: weight,
                intensActivity: intensActivity,
                birthdate: birthdate
            }, { withCredentials: true })
                .then(async (response) => {
                    this.success = true;
                    this.response = response.data;
                    this.userData = {
                        tall: "",
                        weight: "",
                        intensActivity: "",
                        birthdate: ""
                    };
                    this.loading = false;
                })
                .catch((error) => {
                    console.log(error);
                    this.error = true;
                    this.loading = false;
                });
        }
    },
}
</script>

<style scoped>
#login1 {
    color: black;
    text-decoration: none;
    font-size: 14px;
    margin-top: 5px;
    display: inline-block;
    margin-bottom: 10px;
    margin-left: 2px;
    margin-right: 5px;
}

#login {
    font-size: 14px;
    display: inline-block;
    transition: color 0.3s ease-in-out;
    margin-bottom: 10px;
}

#login:hover {
    color: #357ab8;
}

.animate {
    transition: all 0.3s ease;
}

.animate:hover {
    transform: scale(1.05);
}

.animate:active {
    transform: scale(0.95);
}
</style>