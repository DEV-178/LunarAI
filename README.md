<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lunar AI - Chatbot</title>
    <style>
        body {
            margin: 0;
            font-family: Arial, sans-serif;
            background: linear-gradient(135deg, #4b0082, #8a2be2);
            color: #fff;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: space-between;
            height: 100vh;
        }

        header {
            width: 100%;
            padding: 1rem 2rem;
            background: rgba(0, 0, 0, 0.4);
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.6);
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: fixed;
            top: 0;
        }

        header h1 {
            font-size: 1.8rem;
            margin: 0;
        }

        header nav a {
            text-decoration: none;
            color: #fff;
            margin-left: 1.5rem;
            transition: color 0.3s;
        }

        header nav a:hover {
            color: #ffdb58;
        }

        .chat-container {
            margin-top: 7rem;
            flex-grow: 1;
            width: 100%;
            max-width: 600px;
            padding: 2rem;
            background: rgba(255, 255, 255, 0.1);
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.6);
            border-radius: 8px;
        }

        .messages {
            height: 400px;
            overflow-y: auto;
            margin-bottom: 1rem;
            padding: 1rem;
            background: rgba(255, 255, 255, 0.2);
            border-radius: 8px;
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }

        .message {
            padding: 0.8rem;
            border-radius: 8px;
            max-width: 80%;
            word-wrap: break-word;
        }

        .message.user {
            background: #8a2be2;
            align-self: flex-end;
        }

        .message.bot {
            background: #4b0082;
            align-self: flex-start;
        }

        .input-container {
            display: flex;
            gap: 1rem;
        }

        .input-container input {
            flex-grow: 1;
            padding: 0.8rem;
            border: none;
            border-radius: 8px;
            font-size: 1rem;
        }

        .input-container button {
            padding: 0.8rem 1.5rem;
            border: none;
            background: #ffdb58;
            color: #4b0082;
            font-size: 1rem;
            font-weight: bold;
            border-radius: 8px;
            cursor: pointer;
            transition: background 0.3s;
        }

        .input-container button:hover {
            background: #ffcc33;
        }
    </style>
</head>
<body>
    <header>
        <h1>Lunar AI</h1>
        <nav>
            <a href="#">Home</a>
            <a href="#">About</a>
            <a href="#">Contact</a>
        </nav>
    </header>

    <div class="chat-container">
        <div class="messages" id="messages">
            <!-- Chat messages will appear here -->
        </div>
        <div class="input-container">
            <input type="text" id="userInput" placeholder="Type your message here...">
            <button onclick="sendMessage()">Send</button>
        </div>
    </div>

    <script>
        const messagesContainer = document.getElementById('messages');

        function addMessage(content, sender) {
            const messageDiv = document.createElement('div');
            messageDiv.classList.add('message', sender);
            messageDiv.textContent = content;
            messagesContainer.appendChild(messageDiv);
            messagesContainer.scrollTop = messagesContainer.scrollHeight;
        }

        function sendMessage() {
            const userInput = document.getElementById('userInput');
            const message = userInput.value.trim();
            if (!message) return;

            addMessage(message, 'user');
            userInput.value = '';

            setTimeout(() => {
                const botReply = `Lunar AI says: "${message}"! (This is a placeholder reply.)`;
                addMessage(botReply, 'bot');
            }, 1000);
        }
    </script>
</body>
</html>
