!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Benefícios STECK</title>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@100;400;600&display=swap" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        :root {
            --primary: #f01c24;
            --secondary: #f01c24;
            --accent: #10B981;
            --danger: #EF4444;
            --light: #F8FAFC;
            --dark: #1E293B;
            --border-radius: 12px;
            --box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Montserrat', sans-serif;
        }

        body {
            background: #F1F5F9;
            color: var(--dark);
            line-height: 1.6;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
            display: flex;
            flex-direction: column;
            gap: 3rem;
        }

        .header {
            text-align: center;
            padding: 2rem;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow);
        }

        .header h1 {
            font-size: 2.5rem;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 1rem;
        }

        .section {
            background: white;
            border-radius: var(--border-radius);
            padding: 2rem;
            box-shadow: var(--box-shadow);
        }

        .form-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1.5rem;
            margin-bottom: 2rem;
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 600;
            color: var(--dark);
        }

        input, select, textarea {
            font-family: 'Montserrat', sans-serif;
            font-weight: 100;
            width: 100%;
            padding: 1rem;
            border: 2px solid #E2E8F0;
            border-radius: 8px;
            font-size: 1rem;
            transition: all 0.3s ease;
        }

        input:focus, select:focus, textarea:focus {
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
        }

        input::placeholder, textarea::placeholder {
            font-weight: 100;
            color: #94A3B8;
        }

        button {
            background: var(--primary);
            color: white;
            border: none;
            padding: 1rem 2rem;
            border-radius: 8px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
        }

        button:hover {
            background: var(--secondary);
            transform: translateY(-1px);
        }

        .radio-group {
            display: flex;
            gap: 1.5rem;
            margin: 1rem 0;
        }

        .radio-label {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            cursor: pointer;
        }

        .radio-label input[type="radio"] {
            width: 18px;
            height: 18px;
            accent-color: var(--primary);
        }

        .table-container {
            overflow-x: auto;
            margin-top: 1.5rem;
        }

        table {
            width: 100%;
            border-collapse: collapse;
        }

        th, td {
            padding: 1rem;
            text-align: left;
            border-bottom: 1px solid #E2E8F0;
        }

        th {
            background: var(--primary);
            color: white;
            font-weight: 600;
        }

        tr:hover {
            background: var(--light);
        }

        .chart-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 2rem;
            margin-top: 2rem;
        }

        .chart-wrapper {
            position: relative;
            height: 300px;
        }

        .hidden {
            display: none;
        }

        .show-details-btn {
            background: var(--accent);
            padding: 0.5rem 1rem;
            border-radius: 6px;
            font-size: 0.875rem;
            cursor: pointer;
        }

        .detalhe-item {
            background: var(--light);
            padding: 1rem;
            margin: 0.5rem 0;
            border-radius: 8px;
            display: grid;
            grid-template-columns: 1fr 2fr 2fr 3fr;
            gap: 1rem;
            align-items: center;
        }

        .detalhe-item div {
            padding: 0.5rem;
        }

        @media (max-width: 768px) {
            .container {
                padding: 1rem;
            }

            .header h1 {
                font-size: 2rem;
            }

            .form-grid {
                grid-template-columns: 1fr;
            }

            .chart-container {
                grid-template-columns: 1fr;
            }

            .detalhe-item {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Header -->
        <header class="header">
            <h1>Benefícios STECK</h1>
            <p>Gestão de Benefícios</p>
        </header>

        <!-- Seção Novo Registro -->
        <section class="section" id="novo-registro">
            <h2>📝 Novo Registro</h2>
            <div class="form-grid">
                <div class="form-group">
                    <label>Nome do Solicitante</label>
                    <input type="text" id="colaborador" placeholder="Digite o nome">
                </div>
                <div class="form-group">
                    <label>Nome do Beneficiário</label>
                    <input type="text" id="beneficiario" placeholder="Digite o nome">
                </div>
                <div class="form-group">
                    <label>Tipo de Benefício</label>
                    <select id="benefitType">
                        <option value="">Selecione...</option>
                        <option value="conv_medico">Convênio Médico</option>
                        <option value="conv_odontologico">Convênio Odontológico</option>
                        <option value="vt">Vale Transporte</option>
                        <option value="fretado">Transporte Fretado</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>Data do Registro</label>
                    <input type="date" id="dataRegistro">
                </div>
            </div>

            <div class="form-group">
                <label>Tipo de Operação</label>
                <div class="radio-group">
                    <label class="radio-label">
                        <input type="radio" name="operacao" value="inclusao" checked>
                        Inclusão
                    </label>
                    <label class="radio-label">
                        <input type="radio" name="operacao" value="exclusao">
                        Exclusão
                    </label>
                </div>
            </div>

            <div class="form-group">
                <label>Observações</label>
                <textarea id="observacoes" rows="3" placeholder="Adicione observações..."></textarea>
            </div>

            <button onclick="validarFormulario()">💾 Salvar Registro</button>
        </section>

        <!-- Seção Histórico -->
        <section class="section" id="historico-completo">
            <h2>📋 Histórico Completo</h2>
            <div class="table-container">
                <table id="historico">
                    <thead>
                        <tr>
                            <th>Data</th>
                            <th>Solicitante</th>
                            <th>Beneficiário</th>
                            <th>Benefício</th>
                            <th>Operação</th>
                            <th>Observações</th>
                            <th>Ações</th>
                        </tr>
                    </thead>
                    <tbody id="historicoBody"></tbody>
                </table>
            </div>
        </section>

        <!-- Seção Dashboard -->
        <section class="section" id="dashboard">
            <h2>📊 Dashboard</h2>
            <div class="chart-container" id="dashboardContainer">
                <div class="chart-wrapper">
                    <canvas id="graficoBeneficios"></canvas>
                </div>
                <div class="chart-wrapper">
                    <canvas id="graficoTiposBeneficios"></canvas>
                </div>
            </div>
        </section>
    </div>

    <script>
        console.log("Script carregado");

        let registros = JSON.parse(localStorage.getItem('registrosBeneficios')) || [
            { id: 1, colaborador: 'João Silva', beneficiario: 'Maria Silva', tipo: 'conv_medico', data: '2023-10-01', operacao: 'inclusao', observacoes: 'Primeira inclusão' },
            { id: 2, colaborador: 'Carlos Souza', beneficiario: 'Ana Souza', tipo: 'vt', data: '2023-10-02', operacao: 'inclusao', observacoes: 'Segunda inclusão' },
            { id: 3, colaborador: 'Pedro Oliveira', beneficiario: 'Lucas Oliveira', tipo: 'fretado', data: '2023-10-03', operacao: 'inclusao', observacoes: 'Terceira inclusão' }
        ];

        console.log("Registros carregados:", registros);

        // Função para validar e adicionar registro
        function validarFormulario() {
            const colaborador = document.getElementById('colaborador').value.trim();
            const beneficiario = document.getElementById('beneficiario').value.trim();
            const benefitType = document.getElementById('benefitType').value;
            const dataRegistro = document.getElementById('dataRegistro').value;

            if (!colaborador || !beneficiario || !benefitType || !dataRegistro) {
                alert('Preencha todos os campos obrigatórios!');
                return;
            }

            const registro = {
                id: Date.now(),
                colaborador,
                beneficiario,
                tipo: benefitType,
                data: dataRegistro,
                operacao: document.querySelector('input[name="operacao"]:checked').value,
                observacoes: document.getElementById('observacoes').value.trim()
            };

            registros.unshift(registro);
            localStorage.setItem('registrosBeneficios', JSON.stringify(registros));
            atualizarHistorico();
            limparFormulario();
            atualizarDashboard(); // Atualizar dashboard ao adicionar novo registro
        }

        // Função para atualizar o histórico
        function atualizarHistorico() {
            const tbody = document.getElementById('historicoBody');
            tbody.innerHTML = '';

            registros.forEach(registro => {
                const tr = document.createElement('tr');
                tr.innerHTML = `
                    <td>${formatarData(registro.data)}</td>
                    <td class="hidden colaborador">${registro.colaborador}</td>
                    <td class="hidden beneficiario">${registro.beneficiario}</td>
                    <td>${traduzirTipo(registro.tipo)}</td>
                    <td>${registro.operacao === 'inclusao' ? '✅ Inclusão' : '❌ Exclusão'}</td>
                    <td>${registro.observacoes || '-'}</td>
                    <td>
                        <button class="show-details-btn" onclick="mostrarDetalhes(this)">Mostrar Detalhes</button>
                    </td>
                `;
                tbody.appendChild(tr);
            });
        }

        // Função para mostrar detalhes (nomes)
        function mostrarDetalhes(btn) {
            const tr = btn.closest('tr');
            tr.querySelectorAll('.hidden').forEach(el => {
                el.classList.toggle('hidden');
            });
            btn.textContent = btn.textContent === 'Mostrar Detalhes' ? 'Ocultar Detalhes' : 'Mostrar Detalhes';
        }

        // Função auxiliar para traduzir tipos
        function traduzirTipo(tipo) {
            switch (tipo) {
                case 'conv_medico': return 'Convênio Médico';
                case 'conv_odontologico': return 'Convênio Odontológico';
                case 'vt': return 'Vale Transporte';
                case 'fretado': return 'Transporte Fretado';
                default: return 'Desconhecido';
            }
        }

        // Função para formatar data
        function formatarData(dataString) {
            const data = new Date(dataString);
            const dia = String(data.getDate()).padStart(2, '0');
            const mes = String(data.getMonth() + 1).padStart(2, '0');
            const ano = data.getFullYear();
            return `${dia}/${mes}/${ano}`;
        }

        // Função para limpar formulário
        function limparFormulario() {
            document.getElementById('colaborador').value = '';
            document.getElementById('beneficiario').value = '';
            document.getElementById('benefitType').value = '';
            document.getElementById('dataRegistro').value = '';
            document.getElementById('observacoes').value = '';
            document.querySelector('input[name="operacao"][value="inclusao"]').checked = true;
        }

        // Função para atualizar o dashboard
        function atualizarDashboard() {
            const ctx1 = document.getElementById('graficoBeneficios').getContext('2d');
            const ctx2 = document.getElementById('graficoTiposBeneficios').getContext('2d');

            // Agrupar dados por tipo de benefício
            const tipos = ['conv_medico', 'conv_odontologico', 'vt', 'fretado'];
            const contagem = tipos.map(tipo => registros.filter(d => d.tipo === tipo).length);

            console.log("Contagem de tipos:", contagem);

            if (window.graficoBeneficios) {
                window.graficoBeneficios.destroy();
            }

            window.graficoBeneficios = new Chart(ctx1, {
                type: 'doughnut',
                data: {
                    labels: tipos.map(traduzirTipo),
                    datasets: [{
                        data: contagem,
                        backgroundColor: ["#36A2EB", "#FF6384", "#FFCE56", "#4BC0C0"]
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: { position: 'bottom' }
                    }
                }
            });

            if (window.graficoTiposBeneficios) {
                window.graficoTiposBeneficios.destroy();
            }

            window.graficoTiposBeneficios = new Chart(ctx2, {
                type: 'bar',
                data: {
                    labels: tipos.map(traduzirTipo),
                    datasets: [{
                        label: 'Benefícios',
                        data: contagem,
                        backgroundColor: "#4BC0C0"
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        y: { beginAtZero: true }
                    }
                }
            });
        }

        // Carregar histórico ao iniciar
        atualizarHistorico();
        atualizarDashboard(); // Atualizar dashboard ao carregar a página

        // Adicionar event listeners para atualizar o dashboard em tempo real
        document.getElementById('colaborador').addEventListener('input', atualizarDashboard);
        document.getElementById('beneficiario').addEventListener('input', atualizarDashboard);
        document.getElementById('benefitType').addEventListener('change', atualizarDashboard);
        document.getElementById('dataRegistro').addEventListener('input', atualizarDashboard);
        document.querySelectorAll('input[name="operacao"]').forEach(radio => {
            radio.addEventListener('change', atualizarDashboard);
        });
        document.getElementById('observacoes').addEventListener('input', atualizarDashboard);
    </script>
</body>
</html>
