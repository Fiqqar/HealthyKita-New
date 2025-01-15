<template>

  <body>
    <div>
      <header class="navbar">
        <div class="container">
          <p class="brand">HealthyKita.</p>
          <div class="nav-wrapper">
            <nav :class="['nav-list', { show: isMenuOpen }]" aria-label="Main Navigation">
              <router-link to="/home" class="nav-link">Home</router-link>
              <router-link to="/quiz/start" class="nav-link">Quiz</router-link>
            </nav>
            <button class="menu-toggle" @click="toggleMenu">
              <i class="fas fa-bars"></i>
            </button>
            <div class="user-profile" @click="toggleProfileDropdown">
              <img :src="require('/src/assets/download (1).jpg')" alt="Profile Picture" class="profile-picture" />
              <div :class="['dropdown-menu', { show: isProfileDropdownOpen }]">
                <div class="dropdown-content">
                  <div class="profile-card">
                    <div class="profile-card-header">
                      <img :src="require('/src/assets/download (1).jpg')" alt="Profile Picture"
                        class="card-profile-picture" />
                    </div>
                    <div class="notification-icon">
                      <router-link to="/notification"><i class="fa fa-bell"></i>
                        <span class="notification-count">3</span></router-link>

                    </div>
                    <span class="nickname">User.</span>
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
                        <span class="stat-label">Following</span>
                      </div>
                      <div class="stat">
                        <span class="stat-number">124K</span>
                        <span class="stat-label">Followers</span>
                      </div>
                    </div>
                    <div class="dropdown-divider"></div>
                    <router-link to="/profile/:username" class="dropdown-item">Profil</router-link>
                    <div class="dropdown-divider"></div>
                    <router-link to="/rank" class="dropdown-item">Daftar Peringkat</router-link>
                    <div class="dropdown-divider"></div>
                    <router-link to="/login" class="dropdown-item">Logout</router-link>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </header>
      <main class="profile-container">
        <div class="header">
          <div class="user-info">
            <div class="toggle-container">
              <label class="toggle-label">

                <input type="checkbox" class="toggle-switch" />
                <span>Aktifkan Label Dukungan</span>

              </label>
            </div>
            <div class="settings-dropdown">
              <button class="settings-button" @click="toggleSettingsDropdown">
                <i class="fas fa-cog"></i>
              </button>
              <div v-if="isSettingsDropdownOpen" class="dropdown-content1">
                <a href="/profile/settings" class="dropdown-item1">Edit profile</a>
              </div>
            </div>
          </div>
        </div>
        <div class="profile-details">
          <img :src="require('/src/assets/download (1).jpg')" alt="Logo" class="profile-picture" />
          <div class="user-bio">
            <span class="username">Nama Panggilan</span>

            <span class="full-name">Nama Lengkap</span>
            <span class="bio-text">
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Architecto ea officiis omnis culpa magni maxime
              dolor.
            </span>
          </div>
        </div>
        <div class="profile-stats">
          <div class="stat">
            <span class="stat-number">1</span>
            <span class="stat-label">Post</span>
          </div>
          <div class="stat">
            <span class="stat-number">2</span>
            <span class="stat-label">Followers</span>
          </div>
          <div class="stat">
            <span class="stat-number">2</span>
            <span class="stat-label">Following</span>
          </div>
          <div class="stat">
            <span class="stat-number">1</span>
            <span class="stat-label">Ranking</span>
          </div>
        </div>
        <div class="tabs">
          <div class="tab active"><router-link to="/analisis">Hasil Analitik</router-link></div>
          <div class="tab active"><router-link to="/profile/:username">POSTS</router-link></div>
          <div class="tab active-posts">DRAFT</div>
        </div>
        <div class="posts-section">
          <div class="tweet-card">
            <div class="tweet-header">
              <div class="tweet-title">
                <span class="title">Post</span>
                <span class="handle">@User</span>
                <span class="time">· 21h</span>
              </div>
            </div>
            <div class="tweet-content">
              <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Error cum vero eum nisi sapiente repudiandae
                quos, voluptatem adipisci neque, atque doloribus suscipit alias assumenda facilis, eius ipsum?
                Asperiores, eum adipisci. <span class="hashtag">#ANJAY</span></p>
            </div>
          </div>
          <div class="tweet-card">
            <div class="tweet-header">
              <div class="tweet-title">
                <span class="title">Hasil Analitik</span>
                <span class="handle">@User</span>
                <span class="time">· 21h</span>
              </div>
            </div>
            <div class="tweet-content">

              <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Error cum vero eum nisi sapiente repudiandae
                quos, voluptatem adipisci neque, atque doloribus suscipit alias assumenda facilis, eius ipsum?
                Asperiores, eum adipisci. <span class="hashtag">#ANJAY</span></p>
            </div>
          </div>
          <div class="tweet-card">
            <div class="tweet-header">
              <div class="tweet-title">
                <span class="handle">@User</span>
                <span class="time">· 21h</span>
              </div>
            </div>
            <div class="tweet-content">
              <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Error cum vero eum nisi sapiente repudiandae
                quos, voluptatem adipisci neque, atque doloribus suscipit alias assumenda facilis, eius ipsum?
                Asperiores, eum adipisci. <span class="hashtag">#ANJAY</span></p>
            </div>
          </div>

        </div>
        <div class="post-button-container">
          <button class="post-button">Edit</button><button class="delete-btn" @click="deleteButton">{{ isDelete ?
            'Terhapus' : 'Hapus' }}</button>
        </div>
      </main>
    </div>


  </body>
</template>
<script>

export default {
  data() {
    return {
      isProfileDropdownOpen: false,
      isMenuOpen: false,
      isSettingsDropdownOpen: false,
      isDelete: false,
    };
  },
  methods: {
    toggleProfileDropdown() {
      this.isProfileDropdownOpen = !this.isProfileDropdownOpen;

    },
    toggleMenu() {
      this.isMenuOpen = !this.isMenuOpen;
    },
    toggleSettingsDropdown() {
      this.isSettingsDropdownOpen = !this.isSettingsDropdownOpen;
    },
    deleteButton() {
      this.isDelete = !this.isDelete;
    },
    handleClickOutside(event) {
      const profileDropdown = this.$el.querySelector(".user-profile");
      const settingsDropdown = this.$el.querySelector(".settings-dropdown");
      const menuDropdown = this.$el.querySelector(".nav-wrapper");
      if (
        profileDropdown &&
        !profileDropdown.contains(event.target) &&
        this.isProfileDropdownOpen
      ) {
        this.isProfileDropdownOpen = false;
      }
      if (
        settingsDropdown &&
        !settingsDropdown.contains(event.target) &&
        this.isSettingsDropdownOpen
      ) {
        this.isSettingsDropdownOpen = false;
      }
      if (
        menuDropdown &&
        !menuDropdown.contains(event.target) &&
        this.isMenuOpen
      ) {
        this.isMenuOpen = false;
      }
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
@import "~@fortawesome/fontawesome-free/css/all.min.css";

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.user-info {

  display: inline-block;
  margin-bottom: 20px;
}

.title {
  font-weight: bold;
  margin-right: 6px;
  font-size: large;
}

.toggle-container {
  flex-direction: row;
  /* Pastikan selalu horizontal */
  align-items: center;
  /* Vertikal rata tengah */
  justify-content: flex-start;
  /* Rata kiri */
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

.toggle-label {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 1rem;
  font-weight: bold;
  color: black;
  margin-top: -3px;
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
  margin-left: 630px;
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

/* Profile Container */
.profile-container {
  position: relative;
  width: 935px;
  padding: 30px 20px;
  margin: auto;
}

.profile-details {
  display: flex;
  margin-bottom: 20px;
  align-items: center;
}

.profile-details .profile-picture {
  width: 150px;
  height: 150px;
  margin-right: 30px;
}

.user-bio {
  display: flex;
  flex-direction: column;
}

.username {
  font-weight: bold;
  font-size: 18px;
  margin-bottom: 10px;
}

.full-name {
  font-weight: bold;
  font-size: 14px;
  margin-bottom: 5px;
}

.bio-text {
  font-size: 14px;
  line-height: 1.4;
  word-wrap: break-word;
}

.settings-dropdown {
  position: absolute;
  display: inline-block;
  top: 30px;
  right: 10px;
}

.settings-button {
  background: none;
  border: none;
  color: #188754;
  font-size: 20px;
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 5px;
}

.dropdown-content1 {
  position: absolute;
  top: 100%;
  right: 0;
  background-color: #fff;
  border-radius: 10px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  padding: 10px;
  z-index: 10;
  min-width: 150px;
  animation: fadeInSlideDown 0.3s ease-in-out forwards;
}

.dropdown-item1 {
  padding: 10px;
  color: #188754;
  text-decoration: none;
  border-radius: 5px;
  display: block;
  transition: background-color 0.3s;
}

.dropdown-item1:hover {
  background-color: #188754;
  color: white;
}

/* Stats Section */
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

/* Tabs Section */
.tabs {
  display: flex;
  justify-content: space-around;
  border-top: 1px solid #ddd;
  border-bottom: 1px solid #ddd;
  margin-bottom: 30px;
}

.tab {
  padding: 10px 0;
  font-weight: bold;
  cursor: pointer;
  flex: 1;
  text-align: center;

}

.tab a {
  text-decoration: none;
  color: black;
}

.tab.active-posts {

  border-bottom: 2px solid black;
  transform: scale(1.09);

}

.tab.active {

  transition: transform 0.3s ease-in-out;

}

.tab.active:hover {
  border-bottom: 2px solid black;
  transform: scale(1.09);
}

/* Posts Section */
.posts-section {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}

.post-image {
  width: 100%;
  max-width: 200px;
  border: 1px solid #ddd;
  border-radius: 10px;
  margin: 10px;
  transition: transform 0.3s ease;
}

.post-image:hover {
  transform: scale(1.05);
}

.tweet-card {
  background-color: #ffffff;
  border-radius: 8px;
  padding: 16px;
  margin: 10px;
  max-width: 400px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.4);
}

.tweet-header {
  display: flex;
  align-items: center;
  margin-bottom: 12px;
}

.title-user {
  font-weight: bold;
  margin-right: 6px;
  font-size: large;
}


.handle {
  color: #888;
  margin-right: 6px;
}

.time {
  color: #888;
}

.tweet-content {
  font-size: 16px;
  line-height: 1.5;
}

.hashtag {
  color: #1d9bf0;
  font-weight: bold;
}

.post-button-container {
  text-align: center;
  margin-top: 20px;

}

.post-button {
  padding: 10px 40px;
  font-size: 16px;

  font-weight: bold;
  background-color: #188754;
  color: #ffffff;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.3s, transform 0.2s, color 0.3s ease;
}

.post-button:hover {
  background-color: #32c362;
  transform: scale(1.1);
  color: black;
}

.delete-btn {
  margin-left: 5px;
  padding: 10px 40px;
  font-size: 16px;
  font-weight: bold;
  background-color: red;
  color: #ffffff;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.3s, transform 0.2s, color 0.3s ease;
}

.delete-btn:hover {
  background-color: #32c362;
  transform: scale(1.05);
  color: white;
}

.delete-btn:active {
  transform: scale(0.95);
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

@media (max-width: 941px) {
  .container {
    flex-direction: column;
    align-items: flex-start;
  }

  .nav-list {
    display: none;
    flex-direction: column;
    width: 100%;
    background-color: #188754;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
    animation: fadeInSlideDown 0.3s ease-in-out forwards;
  }

  .nav-list.show {
    display: flex;
  }

  .menu-toggle {
    display: block;
  }

  .profile-container {
    width: 100%;
    padding: 20px;
  }

  .profile-details {
    flex-direction: column;
    align-items: center;
    text-align: center;
  }

  .profile-details .profile-picture {
    margin-bottom: 20px;

  }

  .settings-button {
    margin-right: 15px;
    margin-top: -5px;

  }

  .toggle-container {
    flex-direction: row;
    align-items: center;
    justify-content: flex-start;
  }

  .toggle-label {
    margin-top: 0;
    gap: 10px;
  }

  .toggle-switch {
    position: absolute;
    margin-left: 200px;
  }
}

@media (max-width: 941px) {
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
    margin-right: -15px;
  }
}

.navbar {
  background-color: #188754;
  padding: 1rem 0;
  position: sticky;
  top: 0;
  z-index: 100;
}
</style>