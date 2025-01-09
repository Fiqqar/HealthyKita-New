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
                    <img :src="require('/src/assets/download (1).jpg')" alt="Profile Picture" class="card-profile-picture" />
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
                  <router-link to="/rank" class="dropdown-item">Daftar Ranking</router-link>
                  <div class="dropdown-divider"></div>
                  <router-link to="/login" class="dropdown-item">Logout</router-link>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </header>
    <div class="content">
        <div class="quiz-card">
    <div class="question-number">
      <span>1 / 13</span>
    </div>
    <div class="question-text">
      <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Magnam, saepe explicabo, asperiores earum debitis dicta voluptatum sed quos itaque provident commodi mollitia veritatis tenetur voluptates, quo necessitatibus! Mollitia, rerum deleniti.</p>
    </div>
    <div class="options">
      <button class="option">A. lorem</button>
      <button class="option">B. lorem</button>
      <button class="option">C. lorem</button>
      <button class="option">D. lorem</button>
    </div>

    <div class="btn-next-container">
        <button class="btn-next"><i class="fa fa-angle-double-right" aria-hidden="true"></i></button>
    </div>
  </div>
    </div>
    <!-- <div class="btn-next-container">
    <button class="btn-next">-></button>
  </div>
     -->
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

/* Navbar */
.navbar {
  background-color: #188754;
  padding: 1rem 2rem;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 1000;
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
.content {
  padding-top: 80px; 
  display: flex;
  justify-content: center;
  align-items: center;
  height: 80vh;
}

.quiz-card {
  background-color: #188754;
  color: white;
  width: 90%;
  max-width: 600px;
  padding: 60px;
  padding-bottom: 30px;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  text-align: center;
  position: relative;
}

.question-number {
  background-color: #ffffff30;
  color: white;
  border-radius: 50%;
  width: 50px;
  height: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 1rem;
  font-weight: bold;
  position: absolute;
  top: 17px;
  left: 50%;
  transform: translateX(-50%);
}

.question-text {
  margin: 20px 0;
  font-size: 1.2rem;
  line-height: 1.5;
}

.options {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.option {
  background-color: white;
  color: #188754;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  font-size: 1rem;
  font-weight: bold;
  cursor: pointer;
  transition: background-color 0.3s, transform 0.2s;
}

.option:hover {
  background-color: #002699;
  color: white;
  transform: scale(1.05);
}

.btn-next-container {
  display: flex;
  justify-content: center;
  margin-top: 30px;
}

.btn-next {
  background-color: #188754;
  color: white;
  border: none;
  padding: 10px 30px;
  border-radius: 5px;
  font-size: 1rem;
  font-weight: bold;
  cursor: pointer;
  transition: background-color 0.3s, transform 0.2s;
}

.btn-next:hover {
  background-color: #002699;
  transform: scale(1.05);
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

/* Media Queries */
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
    .dropdown-menu{
        margin-top: 20px;
    }
}
@media (max-width: 768px) {
  .quiz-card {
    width: 95%; 
    padding: 25px; 
    padding-top: 39px;
    font-size: 0.9rem; 
  }

  .question-number {
    width: 40px; 
    height: 40px;
    font-size: 0.8rem; 
    margin-top: -8px;
  }

  .question-text {
    font-size: 1rem; 
    line-height: 1.4; 
  }

  .options {
    gap: 10px; 
  }

  .option {
    font-size: 0.9rem; 
    padding: 8px 15px; 
  }
  
}

@media (max-width: 480px) {
  .quiz-card {
    width: 100%; 
    padding: 20px; 
    padding-top: 30px;
    margin: 20px;
  }

  .question-number {
    width: 35px;
    height: 35px;
    font-size: 0.75rem;
  }

  .question-text {
    font-size: 0.9rem;
    line-height: 1.3;
  }

  .options {
    gap: 8px;
  }

  .option {
    font-size: 0.8rem;
    padding: 6px 12px;
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
  