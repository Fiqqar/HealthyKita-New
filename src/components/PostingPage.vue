<template>

    <body>
        <div>
            <header class="navbar">
                <div class="container">
                    <p class="brand">HealthyKita.</p>
                    <div class="nav-wrapper">
                        <nav :class="['nav-list', { show: isMenuOpen }]">
                            <router-link to="/home" class="nav-link">Beranda</router-link>
                            <router-link to="/quiz/start" class="nav-link">Kuis</router-link>
                        </nav>
                        <button class="menu-toggle" @click="toggleMenu">
                            <i class="fas fa-bars"></i>
                        </button>
                        <div class="user-profile" @click="toggleProfileDropdown">
                            <img :src="require('/src/assets/download (1).jpg')" alt="Foto Profil"
                                class="profile-picture" />
                            <div :class="['dropdown-menu', { show: isProfileDropdownOpen }]">
                                <div class="dropdown-content">
                                    <div class="profile-card">
                                        <div class="profile-card-header">
                                            <img :src="require('/src/assets/download (1).jpg')" alt="Foto Profil"
                                                class="card-profile-picture" />
                                        </div>
                                        <div class="notification-icon">
                                            <router-link to="/notification"><i class="fa fa-bell"></i>
                                                <span class="notification-count">3</span></router-link>

                                        </div>
                                        <span class="nickname">Nama Panggilan</span>
                                        <div class="social-icons">
                                            <a href="#" class="social-icon"><i class="fa-brands fa-facebook"></i></a>
                                            <a href="#" class="social-icon"><i class="fa-brands fa-tiktok"></i></a>
                                            <a href="#" class="social-icon"><i class="fa-brands fa-youtube"></i></a>
                                            <a href="#" class="social-icon"><i class="fa-brands fa-google"></i></a>
                                        </div>
                                        <div class="profile-stats">
                                            <div class="stat">
                                                <span class="stat-number">350</span>
                                                <span class="stat-label">Post</span>
                                            </div>
                                            <div class="stat">
                                                <span class="stat-number">200</span>
                                                <span class="stat-label">Mengikuti</span>
                                            </div>
                                            <div class="stat">
                                                <span class="stat-number">124K</span>
                                                <span class="stat-label">Pengikut</span>
                                            </div>
                                        </div>
                                        <div class="dropdown-divider"></div>
                                        <router-link to="/profile/:username" class="dropdown-item">Profil</router-link>
                                        <div class="dropdown-divider"></div>
                                        <router-link to="/rank" class="dropdown-item">Daftar Peringkat</router-link>
                                        <div class="dropdown-divider"></div>
                                        <router-link to="/login" class="dropdown-item">Keluar</router-link>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </header>

            <div class="container1">
                <h1>Posting</h1>
                <div class="container2">
                    <label for="judul">Judul</label>
                    <textarea v-model="judul" id="judul" placeholder="Judul..."></textarea>
                </div>
                <br>
                <div class="container2">
                    <label for="deskripsi">Deskripsi</label>
                    <textarea v-model="deskripsi" id="deskripsi" placeholder="Deskripsimu..."></textarea>
                </div>
                <br>
                <div class="container2">
                    <label for="link">Link</label>
                    <textarea v-model="link" id="link" placeholder="Unggah Link..."></textarea>
                </div>
                <br>
                <div class="toggle-container">
                    <label class="toggle-label">

                        <input type="checkbox" class="toggle-switch" />
                        <span>Aktifkan Komentar</span>

                    </label>
                </div>
                <div class="preview-section">
                    <div class="preview-box">
                        <h2>Hasil Analitik Saya</h2>
                        <div class="preview-content">
                            <h3>{{ judul || 'Judul Anda' }}</h3>
                            <p>{{ deskripsi || 'Deskripsi Anda akan muncul di sini.' }}</p>
                            <a :href="link || '#'" target="_blank">{{ link || 'Link Anda' }}</a>
                        </div>
                    </div>
                    <br>
                    <button class="btn-apply" @click="applyChanges">Terapkan</button>
                </div>
            </div>
        </div>
    </body>
</template>

<script>
export default {
    data() {
        return {
            isProfileDropdownOpen: false,
            isMenuOpen: false,
            judul: '',
        };
    },
    methods: {
        toggleProfileDropdown() {
            this.isProfileDropdownOpen = !this.isProfileDropdownOpen;
        },
        toggleMenu() {
            this.isMenuOpen = !this.isMenuOpen;
        },
        handleClickOutside(event) {
            const profileDropdown = this.$el.querySelector(".user-profile");
            const menuDropdown = this.$el.querySelector(".nav-wrapper");
            if (
                profileDropdown &&
                !profileDropdown.contains(event.target) &&
                this.isProfileDropdownOpen
            ) {
                this.isProfileDropdownOpen = false;
            }
            if (
                menuDropdown &&
                !menuDropdown.contains(event.target) &&
                this.isMenuOpen
            ) {
                this.isMenuOpen = false;
            }
        },

        applyChanges() {
            console.log('Perubahan diterapkan:', {
                judul: this.judul,
                deskripsi: this.deskripsi,
                link: this.link,
            });
        },
    },
    mounted() {
        document.addEventListener("click", this.handleClickOutside);
    },
    beforeUnmount() {
        document.removeEventListener("click", this.handleClickOutside);
    },
};
</script>
<style scoped>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

.toggle-container {
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 20px auto;
    width: 100%;
    padding: 10px 0;
}

.toggle-label {
    display: flex;
    align-items: center;
    gap: 10px;
    font-size: 1rem;
    font-weight: bold;
    color: black;
}

.toggle-switch {
    width: 40px;
    height: 20px;
    appearance: none;
    background-color: #ccc;
    border-radius: 20px;
    position: relative;
    outline: none;
    cursor: pointer;
    transition: background-color 0.3s ease;
}

.toggle-switch:checked {
    background-color: #188754;
}

.toggle-switch:before {
    content: "";
    width: 18px;
    height: 18px;
    background-color: white;
    border-radius: 50%;
    position: absolute;
    top: 1px;
    left: 1px;
    transition: transform 0.3s ease;
}

.toggle-switch:checked:before {
    transform: translateX(20px);
}

/* Pratinjau */
.preview-section {
    margin: 30px auto;
    max-width: 500px;
    display: flex;
    flex-direction: column;
    align-items: center;
}

.preview-box {
    background-color: white;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    width: 100%;
}

.preview-box h2 {
    font-size: 1.2rem;
    margin-bottom: 10px;
    padding-bottom: 10px;
    font-weight: bold;
    text-align: center;
    border-bottom: gray solid 1px;
}

.preview-content {
    color: #333;
}

.preview-content h3 {
    font-size: 1.5rem;
    color: #188754;
}

.preview-content p {
    font-size: 1rem;
    margin-top: 10px;
}

.preview-content a {
    display: block;
    margin-top: 10px;
    color: #188754;
    text-decoration: none;
}

.preview-content a:hover {
    text-decoration: underline;
}

.form-container {
    display: flex;
    justify-content: space-between;
}

.form-section {
    width: 60%;
}

.notification-icon {
    position: absolute;
    top: 23px;
    right: 23px;
    font-size: 20px;
    color: #fff;
    background-color: #188754;
    border-radius: 50%;
    width: 30px;
    height: 30px;
    display: flex;
    align-items: center;
    justify-content: center;
    box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
    cursor: pointer;
    transition: transform 0.2s ease;
}

.notification-count {
    position: absolute;
    top: -5px;
    right: -5px;
    background: #fff;
    color: #e74c3c;
    font-size: 12px;
    border-radius: 50%;
    width: 15px;
    height: 15px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: bold;
}

.notification-icon:hover {
    transform: scale(1.1);
}

.notification-icon:active {
    transform: scale(0.95);
}

body {
    background-color: #F5FFFA;
    color: black;
    font-family: 'Quicksand', sans-serif;
    height: 100vh;
    overflow-x: hidden;
}

/* Navbar */
.navbar {
    background-color: #188754;
    padding: 2rem 0;
    position: sticky;
    top: 0;
    z-index: 100;
}

.navbar .container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 90%;
    max-width: 1200px;
    margin: 0 auto;
}

.brand {
    color: white;
    font-size: 1.5rem;
    font-weight: bold;
    cursor: pointer;
}

.nav-wrapper {
    display: flex;
    align-items: center;
}

.nav-list {
    display: flex;
    gap: 1.5rem;
    background-color: #188754;
    list-style: none;

}

.nav-link {
    font-size: 1rem;
    color: white;
    padding: 10px 15px;
    border-radius: 999px;
    text-decoration: none;
    transition: background-color 0.3s ease, color 0.3s ease;
}

.nav-link:hover {
    color: black;
    background-color: white;
}

.menu-toggle {
    display: none;
    font-size: 1.5rem;
    color: white;
    background: transparent;
    border: none;
    cursor: pointer;

}

/* Profile Dropdown */
.user-profile {
    position: relative;
    cursor: pointer;
}

.profile-picture {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    object-fit: cover;
    margin-left: 30px;
    transition: transform 0.3s ease;
}

.profile-picture:hover {
    transform: scale(1.1);
}

.dropdown-menu {
    position: absolute;
    top: 100%;
    right: 0;
    background-color: #188754;
    border-radius: 10px;
    min-width: 300px;
    min-height: 300px;
    z-index: 1000;
    padding: 16px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
    opacity: 0;
    transform: translateY(-10px);
    transition: opacity 0.3s ease, transform 0.3s ease;
    margin-top: 20px;
    pointer-events: none;
}

.dropdown-menu.show {
    opacity: 1;
    transform: translateY(0);
    pointer-events: auto;
    animation: fadeInSlideDown 0.3s ease-in-out forwards;
}

.dropdown-content {
    background-color: white;
    border-radius: 10px;
    padding: 16px;
    color: black;
}

.profile-card {
    text-align: center;
    flex-direction: column;
}

.card-profile-picture {
    width: 80px;
    height: 80px;
    border-radius: 50%;
    object-fit: cover;
    border: 2px solid #ddd;
}

.nickname {
    font-size: 1.2em;
    font-weight: bold;
}

.social-icons {
    display: flex;
    justify-content: center;
    gap: 10px;
    margin: 10px 0;
}

.social-icon {
    color: black;
    font-size: 1.2rem;
    transition: color 0.3s ease, transform 0.3s ease;
}

.social-icon:hover {
    color: #188754;
    transform: scale(1.1);
}

.dropdown-item {
    display: block;
    padding: 10px;
    text-align: center;
    text-decoration: none;
    color: black;
    border-radius: 5px;
    margin: 5px 0;
    transition: background-color 0.3s ease;
}

.dropdown-item:hover {
    background-color: #f1f1f1;
}

.profile-stats {
    display: flex;
    justify-content: space-around;
    margin-bottom: 30px;
}

.stat {
    text-align: center;
}

.stat-number {
    font-weight: bold;
    font-size: 18px;
    display: block;
}

.stat-label {
    font-size: 14px;
    color: #999;
}

@keyframes fadeInSlideDown {
    from {
        opacity: 0;
        transform: translateY(-10px);
    }

    to {
        opacity: 1;
        transform: translateY(0);
    }
}



.navbar {
    background-color: #188754;
    padding: 1rem 0;
    position: sticky;
    top: 0;
    z-index: 100;
}

.container1 {
    max-width: 600px;
    margin: 0 auto;
    margin-bottom: 25px;
    margin-top: 20px;
    background-color: white;
    padding: 20px;
    border-radius: 40px;
    box-shadow: 0 6px 8px rgba(86, 86, 86, 0.5);
}

h1 {
    font-size: 1.5em;
    margin-bottom: 20px;
}

.btn-apply {
    margin: 20px auto 0;
    display: block;
    background-color: #0363a4;
    color: white;
    border: none;
    border-radius: 25px;
    padding: 8px 16px;
    cursor: pointer;
    font-weight: 500;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    width: 100px;
    transition: background-color 0.3s ease, transform 0.2s ease;
}

.btn-apply:hover {
    background-color: #0077cc;
    transform: scale(1.05);
}

.btn-apply:active {
    transform: scale(0.95);
}


label {
    display: block;
    margin-bottom: 5px;
    font-weight: 500;
    color: #262626;
}

input[type="text"],
textarea,
select {
    width: 100%;
    padding: 8px;
    border: 1px solid #eee;
    border-radius: 15px;
    box-sizing: border-box;
    margin-bottom: 10px;
    background-color: #fafafa;
}

input[type="text"]:focus,
textarea:focus,
select:focus {
    outline: none;
    border-color: #ddd;
}

textarea {
    resize: vertical;
    min-height: 80px;
}

.container2 {
    background-color: #188754;
    border-radius: 20px;
    padding: 15px 15px 13px;

}

.container2 label {
    color: white;
    font-family: Arial, Helvetica, sans-serif;
    margin-left: 5px;
}

.container3 {
    background-color: #188754;
    border-radius: 20px;
    padding: 15px 15px 13px;
    margin-top: 20px;
    margin-bottom: 20px;
}

.container3 label {
    color: white;
    font-family: Arial, Helvetica, sans-serif;
    margin-left: 5px;
}

@media (max-width: 768px) {
    .container {
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
    }

    .nav-wrapper {
        flex-direction: row;
        width: auto;
        align-items: center;
    }

    .nav-list {
        position: absolute;
        top: 100%;
        left: 0;
        flex-direction: column;
        margin-left: 0;
        width: 100%;
        display: none;
        background-color: #188754;
        z-index: 100;
        padding: 1rem;
        box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
        animation: fadeInSlideDown 0.3s ease-in-out forwards;

    }

    .nav-list.show {
        display: flex;
    }

    .nav-link {
        display: block;
        width: 100%;
        text-align: left;
        padding: 0.7rem 1rem;
        border-radius: 40px;

    }

    .brand {
        margin-left: 0px;
        margin-bottom: 0;
    }

    .user-profile {
        margin-left: 0;


    }

    .menu-toggle {
        display: block;
        margin-left: 0;
    }

    .dropdown-menu {
        margin-top: 20px;
    }
}
</style>