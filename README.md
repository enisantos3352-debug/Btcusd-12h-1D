
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Matrix - Alerta de Cruzamento (12h / Diário)</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #0b0e11;
            color: #d1d4dc;
            margin: 0;
            padding: 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        .container {
            width: 100%;
            max-width: 520px;
            background: #1e222d;
            border: 1px solid #2a2e39;
            border-radius: 8px;
            padding: 20px;
            box-sizing: border-box;
            box-shadow: 0 4px 12px rgba(0,0,0,0.4);
        }
        h2 {
            color: #3861fb;
            font-size: 15px;
            text-align: center;
            margin-top: 0;
            margin-bottom: 15px;
            letter-spacing: 1px;
        }
        .live-card {
            background: #131722;
            padding: 12px;
            border-radius: 6px;
            text-align: center;
            margin-bottom: 12px;
            border: 1px solid #2a2e39;
        }
        .live-label {
            font-size: 11px;
            color: #848e9c;
            text-transform: uppercase;
        }
        .live-value {
            font-size: 22px;
            font-weight: bold;
            color: #f3ba2f;
            margin-top: 3px;
        }
        .grid-ma {
            display: grid;
            grid-template-columns: 1fr 1fr 1fr 1fr;
            gap: 6px;
            margin-bottom: 12px;
        }
        .ma-card {
            background: #131722;
            padding: 8px 4px;
            border-radius: 6px;
            text-align: center;
            border: 1px solid #f3ba2f;
        }
        .ma-label { font-size: 9px; color: #f3ba2f; font-weight: bold; text-transform: uppercase; }
        .ma-value { font-size: 11px; font-weight: bold; color: #ffffff; margin-top: 4px; }

        .grid-stats {
            display: grid;
            grid-template-columns: 1fr 1fr 1fr;
            gap: 8px;
            margin-bottom: 12px;
        }
        .stat-box {
            background: #131722;
            padding: 8px;
            border-radius: 6px;
            text-align: center;
            border: 1px solid #2a2e39;
        }
        .stat-label {
            font-size: 9px;
            color: #848e9c;
            margin-bottom: 2px;
            text-transform: uppercase;
        }
        .stat-val { font-size: 11px; font-weight: bold; color: #3861fb; }

        .signal-box {
            padding: 14px;
            border-radius: 6px;
            text-align: center;
            font-weight: bold;
            font-size: 13px;
            background: #131722;
            border: 1px solid #2a2e39;
        }
        .signal-buy { background: #005c29; color: #fff; border-color: #2ebd85; }
        .signal-sell { background: #7a1c2a; color: #fff; border-color: #f6465d; }
        .signal-wait { color: #848e9c; }

        /* Tela de Bloqueio com o Pix */
        #tela-bloqueio {
            display: none;
            background: #131722;
            border: 2px solid #f6465d;
            border-radius: 8px;
            padding: 20px;
            text-align: center;
        }
        #tela-bloqueio h3 { color: #f6465d; margin-top: 0; }
        .pix-box {
            background: #1e222d;
            border: 1px dashed #2ebd85;
            padding: 12px;
            border-radius: 6px;
            margin: 12px 0;
        }
        .pix-chave {
            font-size: 16px;
            font-weight: bold;
            color: #2ebd85;
            margin-top: 5px;
            word-break: break-all;
        }
        .btn-whatsapp {
            display: inline-block;
            margin-top: 10px;
            background: #25d366;
            color: #fff;
            padding: 12px 18px;
            border-radius: 6px;
            text-decoration: none;
            font-weight: bold;
            font-size: 14px;
        }

        .footer-info {
            font-size: 10px;
            color: #787b86;
            text-align: center;
            margin-top: 12px;
        }
    </style>
</head>
<body>

    <div class="container">
        <h2>Matrix - Cruzamento Alinhado (12h / Diário)</h2>
        
        <!-- PAINEL PRINCIPAL -->
        <div id="painel-principal">
            <div class="live-card">
                <div class="live-label">Preço Atual ao Vivo (BTC)</div>
                <div class="live-value" id="preco-atual">Carregando...</div>
            </div>

            <div class="grid-ma">
                <div class="ma-card">
                    <div class="ma-label">MÉD 9</div>
                    <div class="ma-value" id="ma-9">--</div>
                </div>
                <div class="ma-card">
                    <div class="ma-label">MÉD 21</div>
                    <div class="ma-value" id="ma-21">--</div>
                </div>
                <div class="ma-card">
                    <div class="ma-label">MÉD 50</div>
                    <div class="ma-value" id="ma-50">--</div>
                </div>
                <div class="ma-card">
                    <div class="ma-label">MÉD 200</div>
                    <div class="ma-value" id="ma-200">--</div>
                </div>
            </div>

            <div style="font-size: 10px; color: #848e9c; text-transform: uppercase; margin-bottom: 5px; font-weight: bold;">Aberturas Principais (Dia Anterior)</div>
            <div class="grid-stats">
                <div class="stat-box">
                    <div class="stat-label">00h (Meia-Noite)</div>
                    <div class="stat-val" id="ant-00h">--</div>
                </div>
                <div class="stat-box">
                    <div class="stat-label">03h da Manhã</div>
                    <div class="stat-val" id="ant-03h">--</div>
                </div>
                <div class="stat-box">
                    <div class="stat-label">06h da Manhã</div>
                    <div class="stat-val" id="ant-06h">--</div>
                </div>
                <div class="stat-box">
                    <div class="stat-label">12h (Meio-Dia)</div>
                    <div class="stat-val" id="ant-12h">--</div>
                </div>
                <div class="stat-box">
                    <div class="stat-label">18h da Tarde</div>
                    <div class="stat-val" id="ant-18h">--</div>
                </div>
                <div class="stat-box">
                    <div class="stat-label">21h da Noite</div>
                    <div class="stat-val" id="ant-21h">--</div>
                </div>
            </div>

            <div id="sinal-cruzamento" class="signal-box signal-wait">
                Aguardando alinhamento do leque de médias para vela longa...
            </div>
        </div>

        <!-- TELA DE BLOQUEIO COM PIX -->
        <div id="tela-bloqueio">
            <h3>⏰ Período de Teste Expirado!</h3>
            <p style="font-size: 13px; color: #d1d4dc;">Seu teste gratuito de 3 dias acabou. Para renovar por <strong>R$ 25/mês</strong>, faça o Pix para a chave abaixo:</p>
            
            <div class="pix-box">
                <div style="font-size: 11px; color: #848e9c; text-transform: uppercase;">Chave Pix (Telefone)</div>
                <div class="pix-chave">92985966939</div>
                <div style="font-size: 11px; color: #d1d4dc; margin-top: 5px;">Valor: <strong>R$ 25,00</strong></div>
            </div>

            <p style="font-size: 12px; color: #848e9c;">Assim que fizer o pagamento, mande o comprovante para o WhatsApp abaixo:</p>
            
            <a href="https://wa.me/5585992704001?text=Olá!%20Acabei%20de%20fazer%20o%20Pix%20de%20R$%2025%20para%20renovar%20o%20painel." target="_blank" class="btn-whatsapp">Mandar Comprovante no WhatsApp</a>
        </div>

        <div class="footer-info">Sistema de Teste Gratuito - 3 Dias</div>
    </div>

    <script>
        function verificarValidadeTeste() {
            const diasDeTeste = 3; 
            const msPorDia = 24 * 60 * 60 * 1000;
            
            let dataInicio = localStorage.getItem('matrix_inicio_teste_v16');
            
            if (!dataInicio) {
                dataInicio = new Date().getTime();
                localStorage.setItem('matrix_inicio_teste_v16', dataInicio);
            }

            let agora = new Date().getTime();
            let tempoDecorrido = agora - parseInt(dataInicio);
            let limiteTeste = diasDeTeste * msPorDia;

            if (tempoDecorrido > limiteTeste) {
                document.getElementById('painel-principal').style.display = 'none';
                document.getElementById('tela-bloqueio').style.display = 'block';
                return false;
            }
            return true;
        }

        let hist9 = JSON.parse(localStorage.getItem('matrix_hist_v16_9')) || [];
        let hist21 = JSON.parse(localStorage.getItem('matrix_hist_v16_21')) || [];
        let hist50 = JSON.parse(localStorage.getItem('matrix_hist_v16_50')) || [];
        let hist200 = JSON.parse(localStorage.getItem('matrix_hist_v16_200')) || [];

        async function carregarDadosHistoricos() {
            if (!verificarValidadeTeste()) return;

            try {
                const resTicker = await fetch('https://api.binance.com/api/v3/ticker/24hr?symbol=BTCUSDT');
                const dataTicker = await resTicker.json();
                const precoAtual = parseFloat(dataTicker.lastPrice);

                const resKlines = await fetch('https://api.binance.com/api/v3/klines?symbol=BTCUSDT&interval=1h&limit=72');
                const klines = await resKlines.json();

                let agoraData = new Date();
                let diaOntemUTC = new Date(agoraData.getTime() - (24 * 60 * 60 * 1000)).getUTCDate();

                let aberturasOntem = { 0: 0, 3: 0, 6: 0, 12: 0, 18: 0, 21: 0 };

                klines.forEach(candle => {
                    let dataCandle = new Date(candle[0]);
                    let diaCandleUTC = dataCandle.getUTCDate();
                    let horaUTC = dataCandle.getUTCHours();
                    let open = parseFloat(candle[1]);

                    if (diaCandleUTC === diaOntemUTC) {
                        if (aberturasOntem.hasOwnProperty(horaUTC)) {
                            aberturasOntem[horaUTC] = open;
                        }
                    }
                });

                Object.keys(aberturasOntem).forEach(h => {
                    if (aberturasOntem[h] === 0) aberturasOntem[h] = precoAtual;
                });

                // Função auxiliar para calcular média
                function calcularMedia(hist, periodo, valorPadrao) {
                    hist.push(precoAtual);
                    if (hist.length > periodo) hist.shift();
                    let soma = hist.reduce((acc, val) => acc + val, 0);
                    let div = hist.length;
                    if (div < periodo) {
                        soma += (periodo - div) * valorPadrao;
                        div = periodo;
                    }
                    return soma / div;
                }

                let media9 = calcularMedia(hist9, 9, aberturasOntem[0]);
                let media21 = calcularMedia(hist21, 21, aberturasOntem[0]);
                let media50 = calcularMedia(hist50, 50, aberturasOntem[0]);
                let media200 = calcularMedia(hist200, 200, aberturasOntem[0]);

                // Salvando histórico no localStorage a cada ciclo de atualização
                localStorage.setItem('matrix_hist_v16_9', JSON.stringify(hist9));
                localStorage.setItem('matrix_hist_v16_21', JSON.stringify(hist21));
                localStorage.setItem('matrix_hist_v16_50', JSON.stringify(hist50));
                localStorage.setItem('matrix_hist_v16_200', JSON.stringify(hist200));

                // Atualizando os textos na tela
                document.getElementById('preco-atual').innerText = `$ ${precoAtual.toLocaleString('en-US', {minimumFractionDigits: 2, maximumFractionDigits: 2})}`;
                document.getElementById('ma-9').innerText = `$ ${media9.toLocaleString('en-US', {minimumFractionDigits: 0, maximumFractionDigits: 0})}`;
                document.getElementById('ma-21').innerText = `$ ${media21.toLocaleString('en-US', {minimumFractionDigits: 0, maximumFractionDigits: 0})}`;
                document.getElementById('ma-50').innerText = `$ ${media50.toLocaleString('en-US', {minimumFractionDigits: 0, maximumFractionDigits: 0})}`;
                document.getElementById('ma-200').innerText = `$ ${media200.toLocaleString('en-US', {minimumFractionDigits: 0, maximumFractionDigits: 0})}`;

                document.getElementById('ant-00h').innerText = `$ ${aberturasOntem[0].toLocaleString('en-US', {minimumFractionDigits: 2, maximumFractionDigits: 2})}`;
                document.getElementById('ant-03h').innerText = `$ ${aberturasOntem[3].toLocaleString('en-US', {minimumFractionDigits: 2, maximumFractionDigits: 2})}`;
                document.getElementById('ant-06h').innerText = `$ ${aberturasOntem[6].toLocaleString('en-US', {minimumFractionDigits: 2, maximumFractionDigits: 2})}`;
                document.getElementById('ant-12h').innerText = `$ ${aberturasOntem[12].toLocaleString('en-US', {minimumFractionDigits: 2, maximumFractionDigits: 2})}`;
                document.getElementById('ant-18h').innerText = `$ ${aberturasOntem[18].toLocaleString('en-US', {minimumFractionDigits: 2, maximumFractionDigits: 2})}`;
                document.getElementById('ant-21h').innerText = `$ ${aberturasOntem[21].toLocaleString('en-US', {minimumFractionDigits: 2, maximumFractionDigits: 2})}`;

                // --- SINAL DE PRECISÃO TOTAL PARA VELAS 12H / DIÁRIA ---
                let caixaSinal = document.getElementById('sinal-cruzamento');
                
                // Leque de Alta Perfeito: Preço > 9 > 21 > 50 > 200 e acima do teto das 21h
                let altaPerfeita = (precoAtual > media9) && (media9 > media21) && (media21 > media50) && (media50 > media200) && (precoAtual > aberturasOntem[21]);

                // Leque de Baixa Perfeito: Preço < 9 < 21 < 50 < 200 e abaixo do piso das 03h
                let baixaPerfeita = (precoAtual < media9) && (media9 < media21) && (media21 < media50) && (media50 < media200) && (precoAtual < aberturasOntem[3]);

                if (altaPerfeita) {
                    caixaSinal.className = 'signal-box signal-buy';
                    caixaSinal.innerHTML = '🚀 ALERTA DE COMPRA (VELA LONGA)!<br><span style="font-size: 11px; font-weight: normal;">Leque 9/21/50/200 100% alinhado na alta!</span>';
                } 
                else if (baixaPerfeita) {
                    caixaSinal.className = 'signal-box signal-sell';
                    caixaSinal.innerHTML = '📉 ALERTA DE VENDA (VELA LONGA)!<br><span style="font-size: 11px; font-weight: normal;">Leque 9/21/50/200 100% alinhado na baixa!</span>';
                } 
                else {
                    caixaSinal.className = 'signal-box signal-wait';
                    caixaSinal.innerHTML = '⚖️ AGUARDANDO CRUZAMENTO PERFEITO<br><span style="font-size: 11px; font-weight: normal;">Monitore o alinhamento das 4 médias...</span>';
                }

            } catch (e) {
                console.error("Erro ao buscar dados históricos:", e);
            }
        }

        if (verificarValidadeTeste()) {
            setInterval(carregarDadosHistoricos, 2000);
            carregarDadosHistoricos();
        }
    </script>

</body>
</html>
