<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login</title>
</head>
<body>
    <script>
        let username = '';
        let password = '';

        function handleSubmit(event) {
            event.preventDefault();
            if (username === 'admin' && password === 'password') {
                alert('Login successful!');
                window.location.href = '/main-menu';
            } else {
                alert('Invalid username or password. Please try again.');
            }
        }

        document.addEventListener('DOMContentLoaded', () => {
            document.getElementById('login-form').addEventListener('submit', handleSubmit);

            document.getElementById('username').addEventListener('input', (e) => {
                username = e.target.value;
            });

            document.getElementById('password').addEventListener('input', (e) => {
                password = e.target.value;
            });
        });
    </script>
    <main>
        <form id="login-form">
            <label>
                Username:
                <input type="text" id="username" required>
            </label>
            <label>
                Password:
                <input type="password" id="password" required>
            </label>
            <button type="submit">Login</button>
        </form>
    </main>
</body>
</html>
    <style>
        main {
            max-width: 300px;
            margin: 0 auto;
            padding: 20px;
            border: 1px solid #00ffb7;
            border-radius: 5px;
            background-color: #f9f9f900;
        }

        input[type="text"],
        input[type="password"] {
            width: 100%;
            margin: 10px 0;
            padding: 10px;
            box-sizing: border-box;
            background-color: transparent; /* Make the input fields transparent */
            color: #00ffb7; /* Adjust the text color */
            border: 1px solid #00ffb7;
        }

        button {
            width: 100%;
            margin: 10px 0;
            padding: 10px;
            box-sizing: border-box;
            background-color: #00ffb7;
            color: white;
            border: none;
            cursor: pointer;
        }

        button:hover {
            background-color: #00ffb7a9;
        }
    </style>

