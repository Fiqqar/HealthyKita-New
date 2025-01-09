<template>
    <body>
        <div>
            <div class="container">
        <div class="card">
            <div class="logo">
                HealthyKita.
            </div>
            <h1>Kata Sandi Baru</h1>
            <p>Silahkan masukkan kata sandi baru Anda.</p>
            <form>
                <div class="form-group">
                    <label for="password">Kata Sandi Baru</label>
                    <input type="password" id="password" name="password" placeholder="Masukkan kata sandi baru"
                        required>
                </div>
                <div class="form-group">
                    <label for="confirm_password">Konfirmasi Kata Sandi</label>
                    <input type="password" id="confirm_password" name="confirm_password"
                        placeholder="Konfirmasi kata sandi baru" required>
                </div>
                <button type="submit" class="button">Simpan Kata Sandi</button>
            </form>
        </div>
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
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;

        }

        .card {
            background-color: white;
            padding: 40px;
            border-radius: 50px;

            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            max-width: 400px;

            width: 100%;

            box-sizing: border-box;

        }

        .logo {
            color: #008000;
            font-weight: bold;
            margin-bottom: 20px;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        h1 {
            color: #333;
            margin-bottom: 15px;
            text-align: center;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        p {
            color: #777;
            margin-bottom: 30px;
            text-align: center;

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

        input[type="password"] {
            width: 100%;
            padding: 12px;
            box-sizing: border-box;
            border: 1px solid #ddd;
            border-radius: 50px;

            font-size: 16px;
            transition: border-color 0.3s;
            outline: none;
            font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
            background-color: #f5f5f5;
        }

        input[type="password"]:focus {
            font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
            border-color: #008000;

            box-shadow: 0 0 5px rgba(0, 128, 0, 0.2);

        }

        .button {
            width: 100%;
            padding: 14px;
            background-color: #008000;

            color: white;
            border: none;
            border-radius: 24px;
            font-size: 16px;
            cursor: pointer;
            font-family: Verdana, Geneva, Tahoma, sans-serif;
            transition: background-color 0.3s;
        }

        .button:hover {
            background-color: #006400;

        }


        @media (max-width: 480px) {
            .card {
                padding: 20px;

            }
        }
</style>