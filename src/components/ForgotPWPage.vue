<template>

    <body>
        <div>
            <div class="container">
                <div class="logo">
                    <h4>HealthyKita.</h4>
                </div>
                <h1>Lupa Password</h1>
                <p class="instruction">Silahkan masukkan alamat email Anda yang telah terdaftar untuk mereset sandi Anda
                </p>
                <form>
                    <div class="form-group">
                        <label for="email">Email Address</label>
                        <input type="email" id="email" name="email" placeholder="Masukkan email Anda" required>
                    </div>
                    <button type="submit" class="button">Send Reset Link</button>
                </form>
            </div>
        </div>

    </body>

</template>

<script>

</script>

<style scoped>
body {
    font-family: sans-serif;
    background-color: #f8f8f8;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    margin: 0;
}

.container {
    background-color: white;
    padding: 40px;
    border-radius: 50px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    width: 90%;
    max-width: 1000px;
    text-align: center;
}

.logo {
    margin-bottom: 30px;
}

.logo h4 {
    max-width: 123px;
    height: auto;
    color: darkgreen;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

h1 {
    color: #333;
    margin-bottom: 15px;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.instruction {
    color: #777;
    margin-bottom: 30px;
    font-size: 14px;
}

.form-group {
    margin-bottom: 20px;
    text-align: left;
}

label {
    display: block;
    margin-bottom: 8px;
    color: #555;
    font-weight: 500;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

input[type="email"] {
    width: 100%;
    padding: 12px;
    box-sizing: border-box;
    border: 1px solid #ddd;
    border-radius: 50px;
    font-size: 16px;
    transition: border-color 0.3s;
    outline: none;
    background-color: #f5f5f5;
    font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
}

input[type="email"]:focus {
    border-color: darkgreen;
    box-shadow: 0 0 5px rgba(0, 123, 255, 0.2);
}

.button {
    width: 100%;
    padding: 14px;
    background-color: darkgreen;
    color: white;
    border: none;
    border-radius: 50px;
    font-size: 16px;
    cursor: pointer;
    transition: background-color 0.3s;
    font-family: Verdana, Geneva, Tahoma, sans-serif;
}

.button:hover {
    background-color: green;
}

@media (max-width: 480px) {
    .container {
        padding: 20px;
        border-radius: 20px;
    }

    h1 {
        font-size: 20px;
        margin-bottom: 10px;
    }

    .instruction {
        font-size: 12px;
        margin-bottom: 20px;
    }

    input[type="email"] {
        padding: 10px;
        font-size: 14px;
    }

    .button {
        padding: 12px;
        font-size: 14px;
    }
}
</style>