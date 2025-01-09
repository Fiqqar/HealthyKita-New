<template>
    <body>
        <div>
            <header class="navbar">
      <div class="container">
        <p class="brand">HealthyKita.</p>
        <div class="nav-wrapper">
          <nav :class="['nav-list', { show: isMenuOpen }]" aria-label="Main Navigation">
            <router-link to="/home" class="nav-link">Home</router-link>
            <router-link to="/quiz/:start" class="nav-link">Quiz</router-link>
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
  
      <section class="hero">
        <div class="container2">
          <h1 class="hero-title">Pemantauan Kesehatan Mental dan Fisik.</h1>
          <p class="hero-text">
            AirAware adalah platform andalan untuk memantau kualitas udara secara real-time. Dapatkan informasi
            terkini mengenai tingkat polusi udara,
            termasuk detail tentang partikel berbahaya seperti PM2.5, PM10,
            karbon monoksida, ozon, dan nitrogen dioksida.
          </p>
          <form class="search-form">
            <div class="search-container">
              <i class="fa-solid fa-magnifying-glass search-icon"></i>
              <input type="search" placeholder="Search..." class="search-input" />
              <i class="fa-regular fa-circle-xmark search-clear" style="display: none;"></i>
            </div>
          </form>
  
          <a href="https://www.mentalhealth.org.uk/explore-mental-health/a-z-topics/physical-health-and-mental-health"
            class="hero-btn">Learn more</a>
        </div>
      </section>
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

        body,
        h1,
        p,
        a {
            margin: 0;
            padding: 0;
            text-decoration: none;
            color: inherit;
            font-family: 'Quicksand', sans-serif;
            box-sizing: border-box;
        }



        body {
            /* background-color: #F0F8FF;#F5FFFA */
            background-color: #F5FFFA ;
            color: black;
            height: 100vh;
            
        }

        .navbar {
            background-color: #188754;
            padding: 1rem 0;
        }

        .navbar .container {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .search-box {
            width: 100%;
            width: 600px;
            margin: 0 auto;
        }

        .search-form {
            width: 100%;
            display: flex;
            align-items: center;
            margin-top: 1.5rem;
            justify-content: center;
        }

        .search-container {
            display: flex;
            align-items: center;
            border: 1px solid #ccc;
            border-radius: 50px;
            padding: 0.5rem 1rem;
            width: 100%;
            height: 50px;
            max-width: 600px;
            box-sizing: border-box;
            background-color: #fff;
            position: relative;
        }

        .search-icon {
            margin-right: 0.5rem;
            color: #999;
            font-size: 1rem;
        }

        .search-input {
            /* box-sizing: border-box; */
            border-right: none;
            outline: none;
            width: 100%;
            padding: 0.5rem;
            border: 0px solid #ccc;
            border-radius: 5px;
            margin-right: 0.5rem;
            border-radius: 5px 0 0 5px;
            border-right: none;
        }   

        .search-clear {
            position: absolute;
            right: 1rem;
            top: 50%;
            transform: translateY(-50%);
            cursor: pointer;
            color: #999;
            font-size: 1.2rem;
        }

        .search-clear:hover {
            color: #000;
        }

      

        .container {
            width: 90%;
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .nav-wrapper {
            display: flex;
            align-items: center;
        }

        .container2 {
            display: contents;
            align-items: center;
        }

        .brand {
            color: white;
            font-size: 1.5rem;
            font-weight: bold;
            margin: 0;
            margin-right: auto;
            margin-left: -11px;
            padding: 0;
        }


        .nav-list {
            background-color: #188754;
            display: flex;
            gap: 1.5rem;
            margin-left: 25px;
            
        }

        .nav-list :hover a {
            background-color: whitesmoke;
            color: black;
        }

        .nav-link {
            font-size: 1rem;
            color: #fff;
            opacity: 0.8;
            border-radius: 999px;
            padding: 10px 15px;
            transition: background-color 0.6s ease, color 0.6s ease;
        }

        .nav-link:hover {
            color: black;
            background-color: white;
        }

        .nav-link:hover,
        .nav-link.active {
            opacity: 1;
        }

        .hero {
            margin-top: 9rem;
            padding: 2rem 1rem;
            text-align: center;
            background-color: #f9fff9;
        }

        .hero-title {
            /* color: #2f3d4c; */
            color: #1a1a1a;
            font-size: 2.5rem;
            margin-bottom: 1rem;
            font-weight: 700;
            
        
        }

        .hero-text {
            font-size: 1.3rem;
            line-height: 1.4;
            /* margin-bottom: 2rem;
            text-align: center; */
            margin: 0 auto 1.5rem auto;
            max-width: 90%;
            color: gray;
        }
        

        .hero-btn {
            display: inline-block;
            background-color: #fff;
            color: #1a1a1a;
            padding: 0.6rem 1.5rem;
            font-size: 1rem;
            font-weight: bold;
            border-radius: 5px;
            margin-top: 1rem;
            transition: background-color 0.3s, color 0.3s;
        }

        .hero-btn:hover {
            background-color: #444;
            color: #fff;
        }

        .user-profile {
            position: relative;
            cursor: pointer;
            margin-top: 18px;
        }

        .profile-picture {
            width: 40px;
  height: 40px;
  border-radius: 50%;
  object-fit: cover;
  margin-left: 10px;        
  margin-top: -17px;
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

        /* .profile-card-header {
            display: flex;
            flex-direction: column;
            align-items: center;
            margin-bottom: 16px;
        } */

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

        .dropdown-divider {
            border-top: 1px solid #eee;
            margin: 16px 0;
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
            background-color: #e0e0e0;
        }

        .user-profile .profile-picture {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            object-fit: cover;
            transition: transform 0.3s ease-in-out;
           
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
        .menu-toggle {
    display: none;
    background: transparent;
    border: none;
    font-size: 1.5rem;
    cursor: pointer;
    color: white;
    margin-right: 1rem; 
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
       
    }

    .nav-list.show {
        display: flex;
        animation: fadeInSlideDown 0.3s ease-in-out forwards;
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
    margin-top: 18px;
    margin-bottom: 0;
  }

    .menu-toggle {
        display: block;
        margin-left: 0;
    }
}
@media (max-width: 1024px) {
  .hero-title {
    font-size: 2.5rem;
  }
  .hero-text {
    font-size: 1.3rem;
    max-width: 600px;
  }
}

@media (max-width: 768px) {
    .hero-title {
    font-size: 2.3rem;
  }

  .hero-text {
    font-size: 1rem;
  }

  .hero-search input {
    padding: 0.4rem;
    font-size: 0.9rem;
  }

  .hero-btn {
    padding: 0.5rem 1rem;
    font-size: 0.85rem;
  }
  .search-container{
    margin-left: 40px;
    margin-right: 40px;
  }
}

@media (max-width: 480px) {
  .hero {
    padding: 1.5rem 0.5rem;
  }

  .hero-title {
    font-size: 1.5rem;
  }

  .hero-text {
    font-size: 1rem;
  }

  .hero-btn {
    padding: 0.5rem 1rem;
    font-size: 0.9rem;
  }
  .search-container{
    margin-left: 50px;
    margin-right: 50px;
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
  