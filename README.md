<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quebra-Cabeça - Engenharia Social</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #282c34;
            color: #ffffff;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .puzzle-container {
            width: 300px;
            height: 300px;
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            grid-gap: 2px;
            background: #444;
            border: 5px solid #ffffff;
        }
        .piece {
            background-color: #61dafb;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 16px;
            font-weight: bold;
            border: 1px solid #000;
            cursor: pointer;
        }
        .piece.blank {
            background-color: #282c34;
            cursor: default;
        }
    </style>
</head>
<body>
    <div class="puzzle-container" id="puzzle">
        <!-- Pieces dynamically inserted by JavaScript -->
    </div>

    <script>
        const pieces = [
            "Eng", "e", "nha", "ria",
            "So", "ci", "al", "",
        ]; // Add blank space at the end
        const container = document.getElementById('puzzle');

        function shuffleArray(array) {
            for (let i = array.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [array[i], array[j]] = [array[j], array[i]];
            }
            return array;
        }

        function createPuzzle() {
            const shuffled = shuffleArray([...pieces]);
            shuffled.forEach((text, index) => {
                const div = document.createElement('div');
                div.textContent = text;
                div.className = text === "" ? 'piece blank' : 'piece';
                div.setAttribute('data-index', index);
                container.appendChild(div);
            });
        }

        createPuzzle();

        // Event listener for interactivity (drag-and-drop logic can be added)
    </script>
</body>
</html>
