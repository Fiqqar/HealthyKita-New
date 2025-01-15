<template>

  <body>
    <div>
      <header class="navbar">
        <div class="container">
          <p class="brand">HealthyKita.</p>
          <div class="nav-wrapper">
            <nav :class="['nav-list', { show: isMenuOpen }]" aria-label="Main Navigation">
              <router-link to="/home" class="nav-link">Home</router-link>
              <router-link to="/quizstart" class="nav-link">Quiz</router-link>
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
                        <span class="stat-label">Unggahan</span>
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
                    <router-link to="/login" class="dropdown-item">Logout</router-link>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </header>
      <main class="content">
        <div class="article">
          <h1>Hasil Audit</h1>
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Ullam tenetur ex eum non, rem odit
            itaque possimus sapiente nam ab molestiae et laboriosam, est aut earum quasi excepturi maiores
            eveniet.
          </p>
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

body {
  background-color: #F5FFFA;
  color: black;
  font-family: 'Quicksand', sans-serif;
  height: 100vh;
  overflow-x: hidden;
}

.notification-icon {
  position: absolute;
  top: 23px;
  right: 23px;
  font-size: 20px;
  color: white;
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

.article {
  text-align: center;
  margin-top: 240px;
}

.article h1 {
  margin-bottom: 15px;
  font-weight: bold;
}

.article p {

  padding-left: 300px;
  padding-right: 300px;

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

  .article p {
    margin-left: 20px;
    margin-right: 20px;
    padding-left: 0;
    padding-right: 0;
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