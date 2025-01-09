<template>

    <body>
        <div>
            <header class="navbar">
                <div class="container">
                    <p class="brand">HealthyKita.</p>
                    <div class="nav-wrapper">
                        <nav :class="['nav-list', { show: isMenuOpen }]">
                            <router-link to="/home" class="nav-link">Beranda</router-link>
                            <router-link to="/quiz/:start" class="nav-link">Kuis</router-link>
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
                <button class="btn-apply" @click="applyChanges">Terapkan</button>

                
            </div>  
        </div>
    </body>
</template>

<script>
export default {
    data() {
        return {
            isProfileDropdownOpen: false,
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
        openModal() {
            this.isModalOpen = true;
        },
        closeModal() {
            this.isModalOpen = false;
        },
       
        applyChanges() {
            console.log('Perubahan diterapkan:', {
                judul: this.judul,
                deskripsi:this.deskripsi,
                link:this.link,
            });
        }
    }
};
</script>
<style scoped>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
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
    margin-top: 25px;
    background-color: white;
    padding: 20px;
    border-radius: 40px;
    box-shadow: 0 6px 8px rgba(86, 86, 86, 0.5);
}

h1 {
    font-size: 1.5em;
    margin-bottom: 20px;
}


.profile-header {
    display: flex;
    align-items: flex-start;
    margin-bottom: 20px;
    position: relative;
    background-color: #188754;
    border-radius: 30px;
    padding: 15px 15px 15px;
}

.profile-image {
    width: 80px;
    height: 70px;
    border-radius: 50%;
    background-color: #eee;
    margin-right: 20px;
    margin-top: 7px;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
    position: relative;
    cursor: pointer;
}

.profile-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

.profile-image input[type="file"] {
    display: none;
}

.profile-image .photo-placeholder {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: #999;
    font-weight: 500;
}

.profile-info {

    flex-grow: 1;
}

.profile-info input[type="text"] {
    width: 100%;
    padding: 8px;
    border: 1px solid #eee;
    border-radius: 40px;
    box-sizing: border-box;
    margin-bottom: 5px;
    background-color: #fafafa;
}

.profile-info input[type="text"]:focus {
    outline: none;
    border-color: #ddd;
}


.profile-header .chg-btn {
    background-color: #0095f6;
    color: white;
    border: none;
    border-radius: 50px;
    padding: 8px 16px;
    cursor: pointer;
    font-weight: 500;
    bottom: 0;

    margin-top: 15px;
    margin-left: 5px;
    position: relative;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.profile-header .chg-btn:hover {
    background-color: #0077cc;
}

.btn-apply {
    background-color: #0095f6;
    color: white;
    border: none;
    border-radius: 25px;
    padding: 8px 16px;
    cursor: pointer;
    font-weight: 500;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    position: relative;
    width: 100px;
}

.btn-apply:hover {
    background-color: #0077cc;
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

select {
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    color: gray;
    background-color: white;

    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 15px;

    background-image: url("data:image/svg+xml;utf8,<svg fill='black' height='24' viewBox='0 0 24 24' width='24' xmlns='http://www.w3.org/2000/svg'><path d='M7 10l5 5 5-5z'/><path d='M0 0h24v24H0z' fill='none'/></svg>");

    background-repeat: no-repeat;
    background-position: right 8px center;
    padding-right: 30px;
}


.modal {
    display: none;
    position: fixed;
    z-index: 1;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    overflow: auto;
    background-color: rgba(0, 0, 0, 0.4);
    justify-content: center;
    align-items: center;
}

.modal-content {
    background-color: #fefefe;
    margin: 15% auto;
    padding: 20px;
    border: 1px solid #888;
    width: fit-content;
    border-radius: 8px;
    display: flex;
    flex-direction: column;
    gap: 1rem;
    text-align: center;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.modal-content button {
    padding: 0.7rem 1rem;
    border: none;
    background: none;
    border-top: 1px solid lightgray;
    font-size: large;
    cursor: pointer;
}

.modal-content button:first-child {
    border: none;
}

.modal-content button.red {
    color: red;
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

.button-group {
    display: flex;
    gap: 10px;
    margin-top: 15px;
}

.chg-btn.remove {
    background-color: #ff4d4d;
    color: white;
}

.chg-btn.remove:hover {
    background-color: #cc0000;
}
.profile-actions {
    display: flex;
    gap: 10px;
    margin-top: 15px;
}

.file-label {
    cursor: pointer;
}

.file-label input[type="file"] {
    display: none;
}

.chg-btn {
    background-color: #0095f6;
    color: white;
    border: none;
    border-radius: 25px;
    padding: 8px 16px;
    cursor: pointer;
    font-weight: 500;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    text-align: center;
    transition: background-color 0.3s ease;
}

.chg-btn:hover {
    background-color: #0077cc;
}

.chg-btn.remove {
    background-color: #f44336;
}

.chg-btn.remove:hover {
    background-color: #d32f2f;
}

</style>