# Chat-project-
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hacker Chat</title>
    <style>
        body {
            font-family: "Courier New", Courier, monospace;
            background-color: #000; /* Dark background */
            color: #00ff00; /* Green text for hacker style */
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            overflow: hidden;
        }

        .chat-container {
            width: 90%;
            max-width: 700px;
            background-color: #000; /* Black container */
            border: 2px solid #00ff00; /* Green border */
            border-radius: 10px;
            overflow: hidden;
            display: flex;
            flex-direction: column;
            box-shadow: 0 0 20px #00ff00;
        }

        .messages {
            flex: 1;
            padding: 15px;
            overflow-y: auto;
            background-color: #000; /* Dark terminal-like background */
            color: #00ff00; /* Green neon text */
            font-size: 14px;
            line-height: 1.5;
        }

        .message {
            margin-bottom: 10px;
            padding: 8px 10px;
            border-radius: 5px;
            max-width: 70%;
            word-wrap: break-word;
        }

        .message.user1 {
            background-color: rgba(0, 255, 0, 0.1); /* Light green for User 1 */
            align-self: flex-start;
        }

        .message.user2 {
            background-color: rgba(0, 255, 0, 0.2); /* Darker green for User 2 */
            align-self: flex-end;
        }

        .input-container {
            display: flex;
            padding: 10px;
            background-color: #000;
            border-top: 2px solid #00ff00;
        }

        .input-container input {
            flex: 1;
            padding: 10px;
            border: 2px solid #00ff00;
            border-radius: 5px;
            background-color: #000;
            color: #00ff00;
            font-family: "Courier New", Courier, monospace;
        }

        .input-container button {
            padding: 10px 15px;
            border: 2px solid #00ff00;
            border-radius: 5px;
            background-color: #000;
            color: #00ff00;
            font-family: "Courier New", Courier, monospace;
            cursor: pointer;
        }

        .input-container button:hover {
            background-color: #00ff00;
            color: #000;
        }

        /* Scrollbar style */
        .messages::-webkit-scrollbar {
            width: 10px;
        }
        .messages::-webkit-scrollbar-thumb {
            background: #00ff00;
            border-radius: 5px;
        }
        .messages::-webkit-scrollbar-track {
            background: #000;
        }
    </style>
</head>
<body>
    <div class="chat-container">
        <div class="messages" id="messages"></div>
        <div class="input-container">
            <input type="text" id="messageInput" placeholder="Type a message..." />
            <button onclick="sendMessage()">Send</button>
        </div>
    </div>

    <script>
        let userToggle = true; // Toggle between user1 and user2

        function sendMessage() {
            const input = document.getElementById('messageInput');
            const messagesContainer = document.getElementById('messages');
            const messageText = input.value.trim();

            if (messageText === '') return;

            // Create a new message div
            const messageDiv = document.createElement('div');
            messageDiv.classList.add('message');
            messageDiv.classList.add(userToggle ? 'user1' : 'user2');
            messageDiv.textContent = messageText;

            // Add the message to the messages container
            messagesContainer.appendChild(messageDiv);

            // Scroll to the bottom of the messages container
            messagesContainer.scrollTop = messagesContainer.scrollHeight;

            // Clear the input field
            input.value = '';

            // Toggle user
            userToggle = !userToggle;
        }
    </script>
</body>
</html>
