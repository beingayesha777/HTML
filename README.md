<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Read Local Text File</title>
</head>
<body>
    <input type="file" id="fileInput" accept=".txt">
    <pre id="fileContent"></pre>

    <script>
        const fileInput = document.getElementById('fileInput');
        const fileContentDisplay = document.getElementById('fileContent');

        fileInput.addEventListener('change', (event) => {
            const file = event.target.files[0]; // Get the selected file

            if (file) {
                const reader = new FileReader();

                reader.onload = function(e) {
                    // When the file is loaded, display its content
                    fileContentDisplay.textContent = e.target.result;
                };

                reader.onerror = function() {
                    console.error('Error reading the file.');
                    fileContentDisplay.textContent = 'Error reading the file.';
                };

                // Read the file as text
                reader.readAsText(file, 'UTF-8'); // Specify encoding if needed
            } else {
                fileContentDisplay.textContent = 'No file selected.';
            }
        });
    </script>
</body>
</html>
