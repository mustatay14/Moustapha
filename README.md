<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Reservas Flyboard & Jetpack</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background: #f0f0f0;
        }
        header {
            background: #0077cc;
            color: white;
            padding: 15px 20px;
            text-align: center;
        }
        .container {
            max-width: 800px;
            margin: 20px auto;
            padding: 20px;
            background: white;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        form {
            display: flex;
            flex-direction: column;
        }
        label {
            margin: 10px 0 5px;
        }
        input, select, button {
            padding: 10px;
            margin-bottom: 15px;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 16px;
        }
        button {
            background: #0077cc;
            color: white;
            cursor: pointer;
            border: none;
        }
        button:hover {
            background: #005fa3;
        }
        .summary {
            margin-top: 20px;
            padding: 15px;
            border: 1px solid #0077cc;
            border-radius: 5px;
            background: #e6f3ff;
        }
    </style>
</head>
<body>
    <header>
        <h1>Reservas Flyboard & Jetpack</h1>
    </header>
    <div class="container">
        <h2>Reserva tu aventura</h2>
        <form id="bookingForm">
            <label for="activity">Elige una actividad:</label>
            <select id="activity" required>
                <option value="Flyboard">Flyboard</option>
                <option value="Jetpack">Jetpack</option>
            </select>

            <label for="date">Fecha:</label>
            <input type="date" id="date" required>

            <label for="time">Hora:</label>
            <input type="time" id="time" required>

            <label for="duration">Duración:</label>
            <select id="duration" required>
                <option value="30">30 minutos - €50</option>
                <option value="60">60 minutos - €90</option>
            </select>

            <label>
                <input type="checkbox" id="videoOption"> Agregar grabación de video (+€20)
            </label>

            <button type="button" onclick="calculatePrice()">Calcular Precio</button>

            <div id="summary" class="summary" style="display: none;">
                <p><strong>Resumen de la reserva:</strong></p>
                <p id="summaryDetails"></p>
                <button type="submit">Confirmar y Pagar</button>
            </div>
        </form>
    </div>

    <script>
        function calculatePrice() {
            const activity = document.getElementById('activity').value;
            const date = document.getElementById('date').value;
            const time = document.getElementById('time').value;
            const duration = document.getElementById('duration').value;
            const videoOption = document.getElementById('videoOption').checked;

            if (!date || !time || !duration) {
                alert('Por favor, completa todos los campos antes de calcular el precio.');
                return;
            }

            let basePrice = parseInt(duration === '30' ? 50 : 90);
            if (videoOption) basePrice += 20;

            document.getElementById('summaryDetails').innerHTML = `
                Actividad: ${activity}<br>
                Fecha: ${date}<br>
                Hora: ${time}<br>
                Duración: ${duration} minutos<br>
                Precio total: €${basePrice}
            `;

            document.getElementById('summary').style.display = 'block';
        }
    </script>
</body>
</html>
