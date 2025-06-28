require('dotenv').config();
const express = require('express');
const mercadopago = require('mercadopago');
const app = express();

app.use(express.json());

// Configura Mercado Pago
mercadopago.configure({ access_token: process.env.MP_ACCESS_TOKEN });

// Rota para criar pagamentos
app.post('/create-payment', async (req, res) => {
    const { amount, effect } = req.body;
    
    const preference = {
        items: [{ title: `Doação ${effect}`, unit_price: amount, quantity: 1 }],
        notification_url: 'https://seu-backend.onrender.com/webhook',
        external_reference: effect
    };

    try {
        const response = await mercadopago.preferences.create(preference);
        res.json({ payment_url: response.body.init_point });
    } catch (err) {
        res.status(500).json({ error: err.message });
    }
});

// Webhook
app.post('/webhook', async (req, res) => {
    const { type, data } = req.body;
    if (type === "payment") {
        const payment = await mercadopago.payment.findById(data.id);
        console.log(`Efeito ativado: ${payment.body.external_reference}`);
    }
    res.status(200).send();
});

app.listen(process.env.PORT || 3000);
