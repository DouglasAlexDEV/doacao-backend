<!DOCTYPE html>
<html>
<head>
    <title>Doações para a Live!</title>
    <style>
        body { 
            font-family: Arial, sans-serif; 
            background: #1a1a1a; 
            color: white; 
            text-align: center; 
            padding: 20px;
        }
        .donation-card {
            background: #2a2a2a;
            border-radius: 10px;
            padding: 20px;
            margin: 10px;
            display: inline-block;
            width: 250px;
        }
        .donate-btn {
            background: #00b4ff;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
            margin-top: 10px;
        }
    </style>
</head>
<body>
    <h1>Doações para a Live!</h1>
    <p>Escolha um valor e divirta-se com os efeitos!</p>
    
    <div class="donation-card">
        <h3>Pisca-Pisca (R$ 10)</h3>
        <p>Faz a tela piscar!</p>
        <button class="donate-btn" onclick="doar(10, 'piscar')">Doar R$ 10</button>
    </div>
    
    <div class="donation-card">
        <h3>Mouse Louco (R$ 15)</h3>
        <p>Move o mouse para cima!</p>
        <button class="donate-btn" onclick="doar(15, 'mouse')">Doar R$ 15</button>
    </div>
    
    <script>
        function doar(valor, efeito) {
            // Você vai substituir isso pelo link do Mercado Pago depois
            alert(`Você escolheu doar R$ ${valor} para ativar: ${efeito}`);
            
            // Link temporário - depois você coloca o do Mercado Pago
            window.location.href = `https://exemplo.com/doar?valor=${valor}&efeito=${efeito}`;
        }
    </script>
</body>
</html>
