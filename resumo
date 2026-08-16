<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>Gestão Financeira - Operação</title>
<style>
* { box-sizing: border-box; -webkit-tap-highlight-color: transparent; }
body { font-family: 'Inter', system-ui, -apple-system, sans-serif; margin: 0; padding: 0; background: #f1f5f9; color: #0f172a; }
#app { max-width: 100%; margin: 0 auto; padding: 10px; min-height: 100vh; }
h1 { text-align: center; color: #1e293b; margin: 4px 0 8px; font-size: 1.3rem; font-weight: 700; }
.quadro { background: white; border-radius: 16px; padding: 16px; box-shadow: 0 2px 8px rgba(0,0,0,0.08); border: 1px solid #e2e8f0; border-bottom: 4px solid #0f172a; margin-bottom: 24px; position: relative; }
.quadro::before { content: attr(data-label); position: absolute; top: -10px; left: 14px; background: white; padding: 2px 10px; font-size: 0.7rem; font-weight: 700; color: #94a3b8; text-transform: uppercase; letter-spacing: 1px; border: 1px solid #e2e8f0; border-radius: 20px; }
.quadro-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 14px; margin-top: 4px; }
.quadro-header h2 { color: #0f172a; font-size: 1.05rem; margin: 0; display: flex; align-items: center; gap: 8px; }
.btn { border: none; border-radius: 10px; padding: 10px 16px; font-size: 0.95rem; cursor: pointer; font-weight: 700; color: white; box-shadow: 0 2px 4px rgba(0,0,0,0.1); }
.btn-blue { background: linear-gradient(135deg, #3b82f6, #2563eb); }
.btn-yellow { background: linear-gradient(135deg, #f59e0b, #d97706); }
.btn-green { background: linear-gradient(135deg, #10b981, #059669); }
.btn-red { background: #fee2e2; color: #dc2626; font-weight: 700; }
.btn-pdf { background: linear-gradient(135deg, #8b5cf6, #7c3aed); color: white; font-size: 0.85rem; padding: 8px 14px; }
.input { width: 100%; padding: 10px; border: 1px solid #cbd5e1; border-radius: 10px; font-size: 0.95rem; background: #f8fafc; }
.input-small { padding: 8px; font-size: 0.9rem; border-radius: 8px; }
.input:focus { outline: none; border-color: #3b82f6; background: white; }
.row-flex { display: flex; gap: 8px; align-items: center; }
.row-flex .num { width: 30px; height: 30px; background: linear-gradient(135deg, #e2e8f0, #cbd5e1); border-radius: 8px; display: flex; align-items: center; justify-content: center; font-size: 0.8rem; font-weight: 700; color: #475569; flex-shrink: 0; }
.row-flex input[type="text"] { flex: 1; min-width: 0; }
.row-flex input[type="number"] { width: 95px; flex-shrink: 0; }
.func-card { background: linear-gradient(135deg, #f8fafc, #f1f5f9); border-radius: 14px; padding: 14px; border: 2px solid #e2e8f0; margin-bottom: 12px; transition: all 0.3s; }
.func-card.pago { background: linear-gradient(135deg, #ecfdf5, #d1fae5); border-color: #10b981; }
.func-card.pago .pago-badge { display: inline-flex !important; }
.pago-badge { display: none; align-items: center; gap: 4px; background: #10b981; color: white; padding: 4px 10px; border-radius: 20px; font-size: 0.75rem; font-weight: 700; }
.func-grid-3 { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 8px; }
.func-grid-4 { display: grid; grid-template-columns: 1fr 1fr 1fr 1fr; gap: 6px; }
.func-grid label { font-size: 0.68rem; color: #94a3b8; font-weight: 600; }
.salario-box { background: white; border-radius: 10px; padding: 10px 12px; margin-top: 10px; border: 1px solid #e2e8f0; }
.salario-linha { display: flex; justify-content: space-between; font-size: 0.85rem; padding: 2px 0; }
.salario-linha .label { color: #64748b; }
.salario-linha .valor { font-weight: 600; }
.salario-linha.liquido { font-size: 1rem; padding-top: 6px; margin-top: 4px; border-top: 2px dashed #cbd5e1; }
.salario-linha.liquido .label { color: #0f172a; font-weight: 700; }
.salario-linha.liquido .valor { color: #059669; font-weight: 700; font-size: 1.1rem; }
.abas { display: flex; gap: 6px; margin-bottom: 10px; }
.aba { flex: 1; text-align: center; padding: 8px; border-radius: 10px; font-size: 0.85rem; font-weight: 700; cursor: pointer; background: #e2e8f0; color: #64748b; border: 2px solid transparent; }
.aba.active { background: white; color: #3b82f6; border-color: #3b82f6; }
.metro-obra { background: #eff6ff; border-radius: 10px; padding: 10px; margin-bottom: 8px; border: 1px solid #bfdbfe; }
.metro-obra label { font-size: 0.75rem; color: #3b82f6; font-weight: 700; }
.gasto-row { display: flex; justify-content: space-between; align-items: center; padding: 10px 12px; background: #f8fafc; border-radius: 10px; border-left: 4px solid; margin-bottom: 6px; }
.gasto-row.pago { background: #ecfdf5; }
.gasto-row .info { flex: 1; min-width: 0; }
.gasto-row .info .desc { font-size: 0.9rem; font-weight: 600; color: #0f172a; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
.gasto-row .info .meta { font-size: 0.75rem; color: #64748b; }
.gasto-row .valor { font-weight: 700; font-size: 0.95rem; color: #dc2626; flex-shrink: 0; margin-right: 8px; }
.gasto-row.pago .valor { color: #059669; }
.filtro { padding: 6px 12px; border-radius: 20px; font-size: 0.75rem; cursor: pointer; font-weight: 600; background: #e2e8f0; color: #475569; border: 1px solid transparent; }
.filtro.active { background: #1e293b; color: white; border-color: #1e293b; }
.resumo-card { background: linear-gradient(135deg, #0f172a 0%, #1e293b 100%); border-radius: 16px; padding: 20px; color: white; box-shadow: 0 8px 16px rgba(0,0,0,0.15); margin-bottom: 20px; border: 1px solid #334155; position: relative; }
.resumo-card::before { content: "RESULTADO"; position: absolute; top: -10px; left: 14px; background: #0f172a; padding: 2px 10px; font-size: 0.7rem; font-weight: 700; color: #94a3b8; text-transform: uppercase; letter-spacing: 1px; border: 1px solid #334155; border-radius: 20px; }
.resumo-item { background: rgba(255,255,255,0.06); border-radius: 12px; padding: 14px; display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px; border: 1px solid rgba(255,255,255,0.05); }
.resumo-item .label { font-size: 0.9rem; opacity: 0.9; }
.resumo-item .valor { font-size: 1.15rem; font-weight: 700; }
.resumo-destaque { background: rgba(255,255,255,0.1); border-radius: 12px; padding: 16px; display: flex; justify-content: space-between; align-items: center; border: 2px solid rgba(96,165,250,0.3); }
.resumo-destaque .label { font-size: 1.05rem; font-weight: 600; }
.resumo-destaque .valor { font-size: 1.4rem; font-weight: 700; color: #60a5fa; }
.modal-overlay { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.6); z-index: 1000; justify-content: center; align-items: flex-start; padding-top: 40px; backdrop-filter: blur(4px); }
.modal-box { background: white; border-radius: 18px; padding: 22px; width: 92%; max-width: 400px; box-shadow: 0 20px 40px rgba(0,0,0,0.2); margin: 0 auto; border: 1px solid #e2e8f0; }
.modal-box h3 { margin-bottom: 16px; color: #0f172a; font-size: 1.15rem; }
.modal-box label { font-size: 0.8rem; color: #64748b; font-weight: 600; }
.modal-box select, .modal-box input { width: 100%; padding: 12px; border: 1px solid #cbd5e1; border-radius: 12px; margin-top: 4px; font-size: 1rem; background: #f8fafc; }
.modal-actions { display: flex; gap: 10px; margin-top: 16px; }
.modal-actions button { flex: 1; border: none; border-radius: 12px; padding: 14px; font-weight: 700; cursor: pointer; font-size: 1rem; }
.total-line { display: flex; justify-content: space-between; font-weight: 700; color: #0f172a; font-size: 1.05rem; margin-top: 12px; padding-top: 12px; border-top: 2px solid #e2e8f0; }
.sub-line { display: flex; justify-content: space-between; font-size: 0.85rem; color: #64748b; margin-top: 4px; }
.inv-card { background: linear-gradient(135deg, #f8fafc, #f1f5f9); border-radius: 14px; padding: 14px; border: 1px solid #e2e8f0; margin-bottom: 10px; }
.inv-bar { margin-top: 8px; background: #e2e8f0; border-radius: 6px; height: 8px; overflow: hidden; }
.inv-bar-fill { background: linear-gradient(90deg, #ef4444, #f87171); height: 100%; border-radius: 6px; transition: width 0.3s; }
.vale-row { display: flex; justify-content: space-between; align-items: center; font-size: 0.85rem; padding: 4px 0; }
.vale-row label { display: flex; align-items: center; gap: 6px; cursor: pointer; }
.vale-row input[type="checkbox"] { width: 18px; height: 18px; cursor: pointer; accent-color: #059669; }
.pagamento-semana { display: flex; align-items: center; gap: 8px; margin-top: 10px; padding: 10px; background: #fff7ed; border-radius: 10px; border: 1px solid #fed7aa; }
.pagamento-semana input { width: 20px; height: 20px; accent-color: #10b981; cursor: pointer; }
.pagamento-semana label { font-size: 0.9rem; font-weight: 700; color: #c2410c; cursor: pointer; }
.aviso-box { background: linear-gradient(135deg, #fef3c7, #fde68a); border-radius: 12px; padding: 12px 14px; margin-top: 12px; border: 1px solid #f59e0b; font-size: 0.8rem; color: #92400e; line-height: 1.4; }
.cor-MATERIAL { border-left-color: #3b82f6 !important; }
.cor-VALE { border-left-color: #f59e0b !important; }
.cor-GASTO { border-left-color: #ef4444 !important; }
.cor-PESSOAL { border-left-color: #8b5cf6 !important; }
.cor-CUSTO { border-left-color: #64748b !important; }
.cor-DINHEIRO_EMPRESTADO { border-left-color: #f97316 !important; }
.service-card { background:#f8fafc; border:2px solid #e2e8f0; border-radius:14px; padding:12px; margin-bottom:10px; }
.service-card.recebida { background:#ecfdf5; border-color:#10b981; }
.service-card.antecipada { background:#fff7ed; border-color:#f97316; }
.service-status { display:inline-flex; align-items:center; gap:4px; padding:4px 9px; border-radius:20px; font-size:.72rem; font-weight:700; }
.status-recebida { background:#d1fae5; color:#047857; }
.status-antecipada { background:#ffedd5; color:#dc2626 !important; }
.status-pendente { background:#e2e8f0; color:#64748b; }
.service-actions { display:flex; flex-wrap:wrap; gap:6px; margin-top:8px; align-items:center; }
.btn-service { border:none; border-radius:8px; padding:7px 10px; font-size:.76rem; font-weight:700; cursor:pointer; }
.btn-receber { background:#d1fae5; color:#047857; }
.btn-desfazer { background:#e2e8f0; color:#475569; }
.btn-emprestado { background:#ffedd5; color:#c2410c; }
.service-card{background:#f8fafc;border:1px solid #e2e8f0;border-radius:12px;padding:10px;margin-bottom:8px;transition:.2s;}
.service-card.recebida{background:#ecfdf5;border-color:#86efac;}
.service-card.antecipada{background:#fff7ed;border-color:#fdba74;}
.service-actions{display:flex;gap:6px;flex-wrap:wrap;margin-top:7px;align-items:center;}
.service-status{font-size:.72rem;font-weight:800;padding:4px 8px;border-radius:999px;white-space:nowrap;}
.status-pendente{background:#e2e8f0;color:#475569}.status-recebida{background:#d1fae5;color:#047857}.status-antecipada{background:#ffedd5;color:#dc2626 !important}
.btn-service{border:none;border-radius:8px;padding:7px 10px;font-size:.76rem;font-weight:800;cursor:pointer;color:white;}
.btn-receber{background:#10b981}.btn-antecipar{background:#f59e0b}.btn-desfazer{background:#64748b}
.servicos-resumo{display:grid;grid-template-columns:repeat(3,1fr);gap:7px;margin-top:12px;}
.servicos-resumo .sr{padding:9px;border-radius:10px;background:#f8fafc;border:1px solid #e2e8f0;text-align:center;}
.servicos-resumo .sr b{display:block;font-size:.82rem}.servicos-resumo .sr span{font-size:.88rem;font-weight:800;}
.sr-green{background:#ecfdf5!important;border-color:#a7f3d0!important;color:#047857}.sr-orange{background:#fff7ed!important;border-color:#fed7aa!important;color:#c2410c}.sr-gray{background:#f8fafc!important;color:#475569}
.func-card{transition:box-shadow .15s ease,transform .15s ease}.func-card:hover{box-shadow:0 3px 12px rgba(15,23,42,.08)}
@media(max-width:600px){.servicos-resumo{grid-template-columns:1fr}.service-actions{align-items:stretch}.service-actions button{flex:1}}

</style>
<base target="_blank">

<style>
  #menu-principal-app{
    display:flex;
    flex-direction:column;
    gap:10px;
    margin-top:2px;
  }
  .menu-quadro{
    width:100%;
    display:flex;
    align-items:center;
    gap:12px;
    padding:15px 16px;
    border:1px solid #e2e8f0;
    border-radius:14px;
    background:#fff;
    box-shadow:0 2px 7px rgba(15,23,42,.06);
    cursor:pointer;
    text-align:left;
  }
  .menu-quadro:hover{background:#f8fafc;transform:translateY(-1px);}
  .menu-quadro .menu-icone{font-size:1.25rem;width:34px;text-align:center;}
  .menu-quadro .menu-titulo{flex:1;font-weight:800;color:#0f172a;font-size:.98rem;}
  .menu-quadro .menu-seta{font-size:1.35rem;color:#94a3b8;}
  #tela-quadro-app{display:none;}
  #tela-quadro-app.ativo{display:block;}
  #app-menu-home.escondido{display:none;}
  .voltar-quadro{
    display:inline-flex;
    align-items:center;
    gap:6px;
    border:0;
    background:#f1f5f9;
    color:#475569;
    padding:8px 12px;
    border-radius:9px;
    font-weight:700;
    cursor:pointer;
    margin-bottom:10px;
  }
  .voltar-quadro:hover{background:#e2e8f0;}
  .quadro.app-quadro{
    margin-bottom:0;
  }
  @media(max-width:600px){
    #app{padding:9px;}
    .menu-quadro{padding:14px;}
  }


  .menu-quadro.menu-aberto{
    background:#eff6ff;
    border-color:#bfdbfe;
  }
  .quadro-tela{
    margin-top:8px;
  }
</style>

<style>
.rascunho-wrap{overflow:auto;border:1px solid #cbd5e1;border-radius:9px;background:#fff;}
.rascunho-grid{border-collapse:collapse;min-width:720px;width:100%;table-layout:fixed;font-family:Arial,sans-serif;}
.rascunho-grid th,.rascunho-grid td{border:1px solid #dbe2ea;height:22px;padding:1px 5px;font-size:.76rem;}
.rascunho-grid th{background:#f1f5f9;color:#475569;text-align:center;font-weight:800;}
.rascunho-grid .row-num{width:38px;background:#f8fafc;color:#94a3b8;text-align:center;user-select:none;}
.rascunho-grid td{background:#fff;outline:none;vertical-align:middle;white-space:nowrap;overflow:visible;min-width:100px;}
.rascunho-grid td:focus{box-shadow:inset 0 0 0 2px #60a5fa;background:#eff6ff;}
.rascunho-toolbar{display:flex;gap:6px;flex-wrap:wrap;margin-bottom:8px;}
.rascunho-toolbar button{border:1px solid #cbd5e1;background:#fff;color:#334155;border-radius:7px;padding:5px 9px;font-weight:700;cursor:pointer;white-space:nowrap;}
.rascunho-toolbar button:hover{background:#f8fafc;}
.rascunho-total{display:flex;justify-content:space-between;margin-top:8px;padding:8px 10px;background:#f8fafc;border:1px solid #e2e8f0;border-radius:8px;font-size:.8rem;}
.rascunho-total b{color:#2563eb;}
</style>

<style>
#rascunho-grid td[contenteditable="true"]{position:relative;z-index:1;}
#rascunho-grid td[contenteditable="true"]:focus{
  z-index:20;
  overflow:visible;
  white-space:nowrap;
}
</style>
</head>
<body>
<div id="app">
  <h1>📊 Gestão Financeira</h1>
  <div id="app-menu-home"><div id="menu-principal-app"><button class="menu-quadro" data-quadro="1" type="button" onclick="abrirQuadroApp('1')">
      <span class="menu-icone">🔨</span>
      <span class="menu-titulo">Quadro 1 — Serviços em Andamento</span>
      <span class="menu-seta">›</span>
    </button><button class="menu-quadro" data-quadro="2" type="button" onclick="abrirQuadroApp('2')">
      <span class="menu-icone">👷</span>
      <span class="menu-titulo">Quadro 2 — Funcionários</span>
      <span class="menu-seta">›</span>
    </button><button class="menu-quadro" data-quadro="3" type="button" onclick="abrirQuadroApp('3')">
      <span class="menu-icone">📝</span>
      <span class="menu-titulo">Quadro 3 — Gastos da Semana</span>
      <span class="menu-seta">›</span>
    </button><button class="menu-quadro" data-quadro="4" type="button" onclick="abrirQuadroApp('4')">
      <span class="menu-icone">💰</span>
      <span class="menu-titulo">Quadro 4 — Capital de Giro</span>
      <span class="menu-seta">›</span>
    </button>
    <button class="menu-quadro" data-quadro="5" type="button" onclick="abrirQuadroApp('5')">
      <span class="menu-icone">🧮</span>
      <span class="menu-titulo">Quadro 5 — Rascunho / Anotações</span>
      <span class="menu-seta">›</span>
    </button></div>
  </div></div><div id="tela-quadro-app"><section id="quadro-app-1" class="quadro-tela" style="display:none;">
      <div style="display:flex;justify-content:flex-end;margin-bottom:7px;"><button class="voltar-quadro" type="button" onclick="fecharQuadroApp('1')">✕ Fechar quadro</button></div>
      <div class="quadro app-quadro" data-label="Quadro 1">
    <div class="quadro-header">
      <h2>🔨 Serviços em Andamento</h2>
      <button class="btn btn-blue" onclick="addServico()">+ Serviço</button>
    </div>
    <div id="servicos-list"></div>
    <div class="total-line"><span>Total Receita:</span><span id="total-servicos" style="color:#059669;">R$ 0,00</span></div>
    <div class="servicos-resumo">
      <div class="sr sr-green"><b>🟢 Recebido</b><span id="serv-total-recebido">R$ 0,00</span></div>
      <div class="sr sr-orange"><b>🟠 Antecipado pelo giro</b><span id="serv-total-antecipado">R$ 0,00</span></div>
      <div class="sr sr-gray"><b>⏳ Ainda a receber</b><span id="serv-total-pendente">R$ 0,00</span></div>
    </div>
  </div>
    </section><section id="quadro-app-2" class="quadro-tela" style="display:none;">
      <div style="display:flex;justify-content:flex-end;margin-bottom:7px;"><button class="voltar-quadro" type="button" onclick="fecharQuadroApp('2')">✕ Fechar quadro</button></div>
      <div class="quadro app-quadro" data-label="Quadro 2">
    <div class="quadro-header">
      <h2>👷 Funcionários</h2>
      <button class="btn btn-blue" onclick="addFuncionario()">+ Funcionário</button>
    </div>
    <div id="funcionarios-list"></div>
    <div class="total-line"><span>Total Folha (Bruto):</span><span id="total-folha" style="color:#dc2626;">R$ 0,00</span></div>
    <div class="sub-line"><span>Total Vales:</span><span id="total-vales-func">R$ 0,00</span></div>
    <div class="sub-line"><span>Total a Pagar (Líquido):</span><span id="total-liquido-func" style="color:#059669; font-weight:700;">R$ 0,00</span></div>
  </div>
    </section><section id="quadro-app-3" class="quadro-tela" style="display:none;">
      <div style="display:flex;justify-content:flex-end;margin-bottom:7px;"><button class="voltar-quadro" type="button" onclick="fecharQuadroApp('3')">✕ Fechar quadro</button></div>
      <div class="quadro app-quadro" data-label="Quadro 3">
    <div class="quadro-header">
      <h2>📝 Gastos da Semana</h2>
      <button class="btn btn-yellow" onclick="addGasto()">+ Gasto</button>
    </div>
    <div style="display:flex; gap:6px; margin-bottom:12px; flex-wrap:wrap;" id="filtros-gasto">
      <span class="filtro active" onclick="filtrarGastos('TODOS')" data-tipo="TODOS">Todos</span>
      <span class="filtro" onclick="filtrarGastos('MATERIAL')" data-tipo="MATERIAL">Mat.</span>
      <span class="filtro" onclick="filtrarGastos('VALE')" data-tipo="VALE">Vale</span>
      <span class="filtro" onclick="filtrarGastos('GASTO')" data-tipo="GASTO">Gasto</span>
      <span class="filtro" onclick="filtrarGastos('PESSOAL')" data-tipo="PESSOAL">Pess.</span>
      <span class="filtro" onclick="filtrarGastos('CUSTO')" data-tipo="CUSTO">Custo</span>
      <span class="filtro" onclick="filtrarGastos('DINHEIRO_EMPRESTADO')" data-tipo="DINHEIRO_EMPRESTADO">Empréstimo</span>
    </div>
    <div id="gastos-list"></div>
    <div class="total-line"><span>Total Gastos (todos):</span><span id="total-gastos" style="color:#dc2626;">R$ 0,00</span></div>
    <div class="sub-line"><span>Gastos Não Reembolsados:</span><span id="total-gastos-nao-pago" style="color:#f59e0b; font-weight:700;">R$ 0,00</span></div>
    <div class="sub-line"><span>Gastos Reembolsados:</span><span id="total-gastos-pago" style="color:#059669; font-weight:700;">R$ 0,00</span></div>
    <div style="display:flex; flex-wrap:wrap; gap:8px; font-size:0.75rem; color:#64748b; margin-top:6px;">
      <span>Mat: <b id="total-material">R$ 0</b></span>
      <span>Vale: <b id="total-vale">R$ 0</b></span>
      <span>Gasto: <b id="total-gasto">R$ 0</b></span>
      <span>Pess: <b id="total-pessoal">R$ 0</b></span>
      <span>Custo: <b id="total-custo">R$ 0</b></span>
      <span style="color:#c2410c;">Emprestado: <b id="total-emprestado">R$ 0</b></span>
    </div>
  </div>
    </section><section id="quadro-app-4" class="quadro-tela" style="display:none;">
      <div style="display:flex;justify-content:flex-end;margin-bottom:7px;"><button class="voltar-quadro" type="button" onclick="fecharQuadroApp('4')">✕ Fechar quadro</button></div>
      <div class="quadro app-quadro" data-label="Quadro 4">
    <div class="quadro-header">
      <h2>💰 Capital de Giro</h2>
      <button class="btn btn-green" onclick="addInvestidor()">+ Invest.</button>
    </div>
    <div id="investidores-list"></div>
    <div class="total-line" style="margin-top:12px;padding-top:12px;border-top:3px solid #e2e8f0;">
      <span style="color:#475569;">💼 Total Aplicado:</span>
      <span id="total-capital" style="color:#0f766e;font-weight:800;">R$ 0,00</span>
    </div>
    <div class="sub-line"><span>Total Usado (Não Reembolsado):</span><span id="total-aplicado" style="color:#dc2626;">R$ 0,00</span></div>
    <div class="sub-line"><span>Saldo Disponível:</span><span id="total-saldo" style="color:#3b82f6; font-weight:700;">R$ 0,00</span></div>
    <div style="margin-top:12px;padding:12px;border:2px solid #bbf7d0;border-radius:12px;background:#f0fdf4;box-shadow:0 2px 8px rgba(22,163,74,.08);">
      <div style="font-size:.78rem;font-weight:900;color:#15803d;margin-bottom:7px;">💵 CAIXA DAS OBRAS</div>
      <div class="sub-line"><span>🟢 Total Recebido:</span><span id="total-recebido-obras" style="color:#059669;font-weight:800;">R$ 0,00</span></div>
      <div class="sub-line"><span>🔴 Total Pago:</span><span id="total-pago-com-recebido" style="color:#dc2626;font-weight:800;">R$ 0,00</span></div>
      <div class="sub-line" style="border-top:1px solid #dbeafe;margin-top:5px;padding-top:7px;"><span>🔵 Saldo Disponível do Recebido:</span><span id="saldo-recebido-obras" style="color:#2563eb;font-weight:900;">R$ 0,00</span></div>
    </div>
  </div>

    </section>
    <section id="quadro-app-5" class="quadro-tela" style="display:none;">
      <div style="display:flex;justify-content:flex-end;margin-bottom:7px;"><button class="voltar-quadro" type="button" onclick="fecharQuadroApp('5')">✕ Fechar quadro</button></div>
      <div class="quadro app-quadro" data-label="Quadro 5">
        <div class="quadro-header">
          <h2>🧮 Rascunho / Anotações</h2>
          <button class="btn btn-red" onclick="limparRascunho()">Limpar</button>
        </div>
        
        <div class="rascunho-toolbar">
          <button type="button" onclick="rascunhoSomar()">Σ Somar</button>
          <button type="button" onclick="rascunhoNovaLinha()">＋ Linha</button>
          <button type="button" onclick="rascunhoApagarLinha()">− Linha</button>
          <button type="button" onclick="rascunhoNovaColuna()">＋ Coluna</button>
          <button type="button" onclick="rascunhoApagarColuna()">− Coluna</button>
        </div>
        <div class="rascunho-wrap">
          <table class="rascunho-grid" id="rascunho-grid">
            <thead><tr><th class="row-num"></th></tr></thead>
            <tbody></tbody>
          </table>
        </div>
        <div class="rascunho-total"><span>Resultado:</span><b id="rascunho-resultado">R$ 0,00</b></div>
        <div style="font-size:.72rem;color:#64748b;margin-top:6px;">Digite livremente, como uma planilha. As anotações ficam salvas neste computador.</div>
      </div>
    </section>
    </section></div>
  <div class="quadro resumo-card" data-label="Resultado">
    <h2 style="font-size:1.15rem; margin-bottom:16px; text-align:center; margin-top:4px;">📈 Resumo Financeiro</h2>
    <div class="resumo-item"><span class="label">Receita (Serviços)</span><span class="valor" style="color:#4ade80;" id="res-receita">R$ 0,00</span></div>
    <div class="resumo-item"><span class="label">(-) Folha Completa (Bruto)</span><span class="valor" style="color:#f87171;" id="res-folha">R$ 0,00</span></div>
    <div class="resumo-item"><span class="label">(-) Demais Gastos</span><span class="valor" style="color:#f87171;" id="res-gastos">R$ 0,00</span></div>
    <div class="resumo-item"><span class="label">(=) Lucro Bruto</span><span class="valor" style="color:#fbbf24;" id="res-lucro">R$ 0,00</span></div>
    <div class="resumo-destaque"><span class="label">(÷) Por Sócio (2)</span><span class="valor" id="res-socio">R$ 0,00</span></div>
    <div class="aviso-box">
      💡 <strong>Regras:</strong><br>
      • Criar gasto → debita do Capital de Giro selecionado<br>
      • DINHEIRO EMPRESTADO → fica ligado à obra e não entra como gasto do lucro<br>
      • Obras recebidas e pagamentos são controlados separadamente<br>
      • Funcionário com semana paga → card fica <strong>verde</strong>
    </div>
  </div>
</div>
<div class="modal-overlay" id="modal-gasto">
  <div class="modal-box">
    <h3>➕ Novo Gasto</h3>
    <div style="display:flex; flex-direction:column; gap:12px;">
      <div><label>Tipo de Gasto</label><select id="gasto-tipo"><option>MATERIAL</option><option>VALE</option><option>GASTO</option><option>PESSOAL</option><option>CUSTO</option><option>DINHEIRO_EMPRESTADO</option></select></div>
      <div><label>Descrição</label><input id="gasto-desc" type="text" placeholder="Ex: Material obra praia"></div>
      <div><label>Valor (R$)</label><input id="gasto-valor" type="number" step="0.01" placeholder="0,00"></div>
      <div id="gasto-funcionario-box" style="display:none;"><label>Funcionário (só para vale)</label><select id="gasto-funcionario"></select></div>
      <div id="gasto-servico-box" style="display:none;"><label>Obra / Serviço</label><select id="gasto-servico"></select></div>
      <div><label>Investidor (de onde sai o dinheiro)</label><select id="gasto-investidor"></select></div>
      <div class="modal-actions">
        <button style="background:linear-gradient(135deg,#f59e0b,#d97706); color:white;" onclick="salvarGasto()">💾 Salvar</button>
        <button style="background:#e2e8f0; color:#475569;" onclick="fecharModalGasto()">❌ Cancelar</button>
      </div>
    </div>
  </div>
</div>

<div class="modal-overlay" id="modal-investidor">
  <div class="modal-box">
    <h3 id="titulo-modal-investidor">➕ Novo Investidor</h3>
    <div style="display:flex; flex-direction:column; gap:12px;">
      <div><label>Nome do Investidor</label><input id="inv-nome" type="text" placeholder="Ex: Alexandre"></div>
      <div><label>Valor Aplicado (R$)</label><input id="inv-valor" type="number" step="0.01" placeholder="0,00"></div>
      <div class="modal-actions">
        <button style="background:linear-gradient(135deg,#10b981,#059669); color:white;" id="btn-salvar-investidor" onclick="salvarInvestidor()">💾 Salvar</button>
        <button style="background:#e2e8f0; color:#475569;" onclick="fecharModalInvestidor()">❌ Cancelar</button>
      </div>
    </div>
  </div>
</div>
<script>

let servicos = [];
let funcionarios = [];
let gastos = [];
let investidores = [];
let filtroAtual = 'TODOS';
let investidorEditandoId = null;
let acaoServicoAtual = null;
let servicoAtualIdx = null;

function init(){
  servicos.forEach(s=>{
    if(!s.status)s.status='pendente';
    if(s.antecipado==null)s.antecipado=0;
    if(s.antecipacaoInvestidorId==null)s.antecipacaoInvestidorId=null;
    if(s.antecipacaoInvestidorNome==null)s.antecipacaoInvestidorNome='';
    if(s.antecipacaoData==null)s.antecipacaoData='';
    if(s.recebimentoData==null)s.recebimentoData='';
    if(s.observacao==null)s.observacao='';
  });
  renderServicos();
  renderFuncionarios();
  renderGastos();
  renderInvestidores();
  atualizarResumo();
}

function formatarMoeda(v){
  return 'R$ '+(v||0).toLocaleString('pt-BR',{minimumFractionDigits:2,maximumFractionDigits:2});
}

function renderServicos(){
  const c = document.getElementById('servicos-list');
  c.innerHTML = '';
  let t = 0, totalRecebido = 0, totalPendente = 0;

  if(servicos.length===0){
    c.innerHTML=`<div style="padding:18px;text-align:center;color:#64748b;background:#f8fafc;border:1px dashed #cbd5e1;border-radius:10px;margin-bottom:8px;">
      Nenhum serviço cadastrado.<br><small>Clique em <b>+ Serviço</b> para adicionar somente as obras que você precisar.</small>
    </div>`;
  }

  servicos.forEach((s,idx)=>{
    const valor = parseFloat(s.valor)||0;
    t += valor;

    // SERVIÇOS EM ANDAMENTO é EXCLUSIVAMENTE o controle das obras.
    // Dinheiro Emprestado/Pago não interfere neste quadro.
    const status = s.status==='recebida' ? 'recebida' : 'pendente';
    const emprestimoPendente = gastos.find(g =>
      g.tipo==='DINHEIRO_EMPRESTADO' &&
      String(g.servicoId)===String(s.id) &&
      !g.pago
    );

    if(status==='recebida') totalRecebido += valor;
    else if(valor>0) totalPendente += valor;

    const d = document.createElement('div');
    d.className = 'service-card '+(status==='recebida'?'recebida':'');

    const badge = status==='recebida'
      ? '<span class="service-status status-recebida">🟢 RECEBIDA</span>'
      : '<span class="service-status status-pendente">⏳ A RECEBER</span>';

    // Apenas informação visual do empréstimo. Não é botão e não interfere
    // no status/recebimento da obra.
    const emprestimoBadge = emprestimoPendente
      ? '<span class="service-status status-antecipada" style="color:#dc2626 !important;">● DINHEIRO EMPRESTADO</span>'
      : '';

    let actions = '';
    if(status!=='recebida'){
      actions = `<button class="btn-service btn-receber" onclick="receberServico(${idx})">✅ Obra Recebida</button>`;
    } else {
      actions = `<button class="btn-service btn-desfazer" onclick="desfazerRecebimento(${idx})">↩ Desfazer Recebimento</button>`;
    }

    let extra = '';
    if(status==='recebida' && s.recebimentoData){
      extra = `<div style="font-size:.76rem;color:#047857;margin-top:6px;">📅 Recebida em ${s.recebimentoData}</div>`;
    }

    d.innerHTML = `
      <div class="row-flex">
        <span class="num">${idx+1}</span>
        <input type="text" class="input" placeholder="Descrição do serviço"
          value="${s.desc||''}" onchange="updateServico(${idx},'desc',this.value)">
        <input type="number" class="input" step="0.01" placeholder="R$ 0,00"
          value="${s.valor||''}" onchange="updateServico(${idx},'valor',this.value)">
        <button class="btn btn-red" onclick="removeServico(${idx})" title="Remover serviço">✕</button>
      </div>
      <div class="service-actions">${badge}${emprestimoBadge}${actions}</div>
      ${extra}`;
    c.appendChild(d);
  });

  document.getElementById('total-servicos').textContent = formatarMoeda(t);
  document.getElementById('serv-total-recebido').textContent = formatarMoeda(totalRecebido);
  document.getElementById('serv-total-antecipado').textContent = 'R$ 0,00';
  document.getElementById('serv-total-pendente').textContent = formatarMoeda(totalPendente);
  atualizarResumo();
}

function addServico(){
  servicos.push({
    id:Date.now()+Math.floor(Math.random()*1000),
    desc:'',
    valor:0,
    status:'pendente',
    recebimentoData:'',
    antecipado:0,
    antecipacaoInvestidorId:null,
    antecipacaoInvestidorNome:'',
    antecipacaoData:'',
    observacao:''
  });
  renderServicos();
  atualizarSelectsModal();
}

function removeServico(idx){
  const s=servicos[idx];
  if(!s)return;

  // Remove SOMENTE a obra do Quadro 1 (Serviços em Andamento).
  // Qualquer lançamento de DINHEIRO_EMPRESTADO continua intacto
  // nos Gastos da Semana (Quadro 3).
  servicos.splice(idx,1);

  renderServicos();
  atualizarSelectsModal();
  atualizarResumo();
}

function updateServico(idx,campo,valor){
  if(campo==='valor') servicos[idx][campo]=parseFloat(valor)||0;
  else servicos[idx][campo]=valor;
  renderServicos();
}

function receberServico(idx){
  const s=servicos[idx];
  if(!s)return;

  if(!s.desc || (parseFloat(s.valor)||0)<=0){
    alert('Preencha o nome e o valor da obra antes de marcar como recebida.');
    return;
  }

  // Somente o status da obra. Não toca em Gastos da Semana,
  // Dinheiro Emprestado ou Capital de Giro.
  s.status='recebida';
  s.recebimentoData=new Date().toLocaleDateString('pt-BR');

  renderServicos();
  atualizarResumo();
}


function desfazerRecebimento(idx){
  const s=servicos[idx];
  if(!s || s.status!=='recebida')return;

  // Somente o status da obra. Não toca em Gastos da Semana,
  // Dinheiro Emprestado ou Capital de Giro.
  s.status='pendente';
  s.recebimentoData='';

  renderServicos();
  atualizarResumo();
}


// ==================== GERAR PDF INDIVIDUAL DO FUNCIONÁRIO ====================
function gerarPDFFuncionario(funcId){
  const f = funcionarios.find(x=>x.id===funcId);
  if(!f) return;

  const salarioDiaria = (f.diaria*f.dias)+(f.diaria*f.sabados)+(f.horasExtra*f.valorHoraExtra);
  const metroForro = (f.metroForroM2Qtd*f.metroForroM2Valor);
  const metroLinear = (f.metroLinearQtd*f.metroLinearValor);
  const metroCaixa = (f.metroCaixaArQtd*f.metroCaixaArValor);
  const metroShaft = (f.metroShaftQtd*f.metroShaftValor);
  const salarioMetro = metroForro + metroLinear + metroCaixa + metroShaft;
  const salarioBruto = salarioDiaria + salarioMetro;
  const valesFunc = f.vales.reduce((sum,v)=>sum+(parseFloat(v.valor)||0),0);
  const salarioLiquido = salarioBruto - valesFunc;
  const dataHoje = new Date().toLocaleDateString('pt-BR');

  let htmlMetro = '';
  if(salarioMetro > 0 || f.metroObra){
    htmlMetro = `<div style="margin-top:20px; padding:15px; background:#eff6ff; border-radius:8px; border:1px solid #bfdbfe;">
      <h3 style="color:#1e40af; margin:0 0 10px; font-size:16px;">📏 PRODUÇÃO POR METRO — ${f.metroObra || 'Obra não informada'}</h3>
      <table style="width:100%; border-collapse:collapse; font-size:14px;">
        <tr style="background:#dbeafe;"><th style="padding:8px; text-align:left; border:1px solid #93c5fd;">Item</th><th style="padding:8px; text-align:center; border:1px solid #93c5fd;">Qtd</th><th style="padding:8px; text-align:right; border:1px solid #93c5fd;">Valor Unit.</th><th style="padding:8px; text-align:right; border:1px solid #93c5fd;">Total</th></tr>
        <tr><td style="padding:8px; border:1px solid #e2e8f0;">Forro M²</td><td style="padding:8px; text-align:center; border:1px solid #e2e8f0;">${f.metroForroM2Qtd || 0}</td><td style="padding:8px; text-align:right; border:1px solid #e2e8f0;">${formatarMoeda(f.metroForroM2Valor)}</td><td style="padding:8px; text-align:right; border:1px solid #e2e8f0; font-weight:700;">${formatarMoeda(metroForro)}</td></tr>
        <tr><td style="padding:8px; border:1px solid #e2e8f0;">Linear</td><td style="padding:8px; text-align:center; border:1px solid #e2e8f0;">${f.metroLinearQtd || 0}</td><td style="padding:8px; text-align:right; border:1px solid #e2e8f0;">${formatarMoeda(f.metroLinearValor)}</td><td style="padding:8px; text-align:right; border:1px solid #e2e8f0; font-weight:700;">${formatarMoeda(metroLinear)}</td></tr>
        <tr><td style="padding:8px; border:1px solid #e2e8f0;">Caixa de Ar</td><td style="padding:8px; text-align:center; border:1px solid #e2e8f0;">${f.metroCaixaArQtd || 0}</td><td style="padding:8px; text-align:right; border:1px solid #e2e8f0;">${formatarMoeda(f.metroCaixaArValor)}</td><td style="padding:8px; text-align:right; border:1px solid #e2e8f0; font-weight:700;">${formatarMoeda(metroCaixa)}</td></tr>
        <tr><td style="padding:8px; border:1px solid #e2e8f0;">Shaft</td><td style="padding:8px; text-align:center; border:1px solid #e2e8f0;">${f.metroShaftQtd || 0}</td><td style="padding:8px; text-align:right; border:1px solid #e2e8f0;">${formatarMoeda(f.metroShaftValor)}</td><td style="padding:8px; text-align:right; border:1px solid #e2e8f0; font-weight:700;">${formatarMoeda(metroShaft)}</td></tr>
        <tr style="background:#dbeafe; font-weight:700;"><td colspan="3" style="padding:8px; text-align:right; border:1px solid #93c5fd;">TOTAL METRO:</td><td style="padding:8px; text-align:right; border:1px solid #93c5fd; color:#1e40af;">${formatarMoeda(salarioMetro)}</td></tr>
      </table>
    </div>`;
  }

  let htmlVales = '';
  if(f.vales.length > 0){
    htmlVales = `<div style="margin-top:20px;"><h3 style="color:#dc2626; margin:0 0 10px; font-size:16px;">📉 VALES RECEBIDOS</h3>
      <table style="width:100%; border-collapse:collapse; font-size:14px;">
        <tr style="background:#fee2e2;"><th style="padding:8px; text-align:left; border:1px solid #fca5a5;">Descrição</th><th style="padding:8px; text-align:right; border:1px solid #fca5a5;">Valor</th><th style="padding:8px; text-align:center; border:1px solid #fca5a5;">Status</th></tr>
        ${f.vales.map(v=>`<tr><td style="padding:8px; border:1px solid #e2e8f0;">${v.desc}</td><td style="padding:8px; text-align:right; border:1px solid #e2e8f0; font-weight:700; color:#dc2626;">${formatarMoeda(v.valor)}</td><td style="padding:8px; text-align:center; border:1px solid #e2e8f0;">${v.pago?'✓ Reembolsado':'⏳ Pendente'}</td></tr>`).join('')}
        <tr style="background:#fee2e2; font-weight:700;"><td style="padding:8px; border:1px solid #fca5a5;">TOTAL VALES</td><td colspan="2" style="padding:8px; text-align:right; border:1px solid #fca5a5; color:#dc2626;">${formatarMoeda(valesFunc)}</td></tr>
      </table></div>`;
  } else {
    htmlVales = `<div style="margin-top:20px; padding:15px; background:#f0fdf4; border-radius:8px; text-align:center; color:#166534; font-size:14px;">✅ Nenhum vale registrado</div>`;
  }

  const win = window.open('', '_blank');
  win.document.write(`<!DOCTYPE html><html lang="pt-BR"><head><meta charset="UTF-8"><title>Folha de Pagamento — ${f.nome || 'Funcionário'}</title>
    <style>body{font-family:'Segoe UI',Arial,sans-serif;margin:0;padding:30px;background:#fff;color:#1e293b;}
    .header{text-align:center;border-bottom:3px solid #1e293b;padding-bottom:15px;margin-bottom:25px;}
    .header h1{margin:0;font-size:22px;color:#0f172a;}.header p{margin:5px 0 0;color:#64748b;font-size:13px;}
    .info-box{background:#f8fafc;border:1px solid #e2e8f0;border-radius:8px;padding:15px;margin-bottom:20px;}
    .info-row{display:flex;justify-content:space-between;margin:6px 0;font-size:14px;}
    .info-row .label{color:#64748b;font-weight:600;}.info-row .value{color:#0f172a;font-weight:700;}
    table{width:100%;border-collapse:collapse;margin-top:10px;}th,td{padding:10px;border:1px solid #cbd5e1;}
    th{background:#1e293b;color:white;font-size:13px;text-align:left;}
    .total-row{background:#f1f5f9;font-weight:700;font-size:15px;}
    .total-final{background:#0f172a;color:white;font-size:18px;font-weight:700;}
    .assinatura{margin-top:60px;display:flex;justify-content:space-between;}
    .assinatura-box{width:45%;text-align:center;}.linha{border-top:1px solid #0f172a;margin-top:40px;padding-top:8px;font-size:12px;color:#64748b;}
    @media print{body{padding:20px;}.no-print{display:none;}}</style></head><body>
    <div class="header"><h1>📄 FOLHA DE PAGAMENTO</h1><p>Emitido em ${dataHoje}</p></div>
    <div class="info-box">
      <div class="info-row"><span class="label">Funcionário:</span><span class="value" style="font-size:18px;">${f.nome || 'Não informado'}</span></div>
      <div class="info-row"><span class="label">Status da Semana:</span><span class="value" style="color:${f.semanaPaga?'#059669':'#dc2626'};">${f.semanaPaga?'✅ SEMANA PAGA':'⏳ SEMANA PENDENTE'}</span></div>
    </div>
    <h2 style="font-size:16px;color:#0f172a;margin:25px 0 10px;">📅 REMUNERAÇÃO POR DIÁRIA</h2>
    <table>
      <tr><th style="width:50%;">Descrição</th><th style="text-align:center;">Qtd / Info</th><th style="text-align:right;">Valor Unit.</th><th style="text-align:right;">Total</th></tr>
      <tr><td>Diária normal</td><td style="text-align:center;">${f.dias || 0} dias</td><td style="text-align:right;">${formatarMoeda(f.diaria)}</td><td style="text-align:right;font-weight:700;">${formatarMoeda(f.diaria * f.dias)}</td></tr>
      <tr><td>Sábados</td><td style="text-align:center;">${f.sabados || 0} dias</td><td style="text-align:right;">${formatarMoeda(f.diaria)}</td><td style="text-align:right;font-weight:700;">${formatarMoeda(f.diaria * f.sabados)}</td></tr>
      <tr><td>Horas Extras</td><td style="text-align:center;">${f.horasExtra || 0} h</td><td style="text-align:right;">${formatarMoeda(f.valorHoraExtra)}</td><td style="text-align:right;font-weight:700;">${formatarMoeda(f.horasExtra * f.valorHoraExtra)}</td></tr>
      <tr class="total-row"><td colspan="3" style="text-align:right;">TOTAL DIÁRIA:</td><td style="text-align:right;color:#3b82f6;">${formatarMoeda(salarioDiaria)}</td></tr>
    </table>
    ${htmlMetro}
    <div style="margin-top:25px;padding:20px;background:#f8fafc;border-radius:10px;border:2px solid #e2e8f0;">
      <div class="info-row" style="font-size:16px;"><span class="label">TOTAL BRUTO (Diária + Metro):</span><span class="value" style="font-size:18px;color:#0f172a;">${formatarMoeda(salarioBruto)}</span></div>
    </div>
    ${htmlVales}
    <div style="margin-top:25px;padding:20px;background:#0f172a;border-radius:10px;color:white;">
      <div style="display:flex;justify-content:space-between;align-items:center;">
        <span style="font-size:16px;">💵 SALÁRIO LÍQUIDO A RECEBER:</span>
        <span style="font-size:28px;font-weight:700;color:#4ade80;">${formatarMoeda(salarioLiquido)}</span>
      </div>
    </div>
    <div class="assinatura">
      <div class="assinatura-box"><div class="linha">ASSINATURA DO FUNCIONÁRIO</div></div>
      <div class="assinatura-box"><div class="linha">ASSINATURA DO EMPREGADOR</div></div>
    </div>
    <div style="margin-top:40px;text-align:center;font-size:11px;color:#94a3b8;">Documento gerado automaticamente pelo sistema de gestão financeira.</div>
    <div class="no-print" style="margin-top:30px;text-align:center;">
      <button onclick="window.print()" style="background:#3b82f6;color:white;border:none;padding:14px 30px;border-radius:10px;font-size:16px;font-weight:700;cursor:pointer;">🖨️ IMPRIMIR / SALVAR PDF</button>
    </div>
    </body></html>`);
  win.document.close();
}

function addFuncionario(){
  funcionarios.push({id:Date.now(),nome:'',diaria:0,dias:0,sabados:0,horasExtra:0,valorHoraExtra:0,metroObra:'',metroForroM2Qtd:0,metroForroM2Valor:0,metroLinearQtd:0,metroLinearValor:0,metroCaixaArQtd:0,metroCaixaArValor:0,metroShaftQtd:0,metroShaftValor:0,vales:[],semanaPaga:false,aberto:false});
  renderFuncionarios();
}
function removeFuncionario(id){funcionarios=funcionarios.filter(f=>f.id!==id);renderFuncionarios();}

function updateMetroLive(id,campo,valor){
  const f=funcionarios.find(x=>x.id===id);
  if(!f)return;
  f[campo]=parseFloat(String(valor).replace(',','.'))||0;

  const forro=(f.metroForroM2Qtd||0)*(f.metroForroM2Valor||0);
  const linear=(f.metroLinearQtd||0)*(f.metroLinearValor||0);
  const caixa=(f.metroCaixaArQtd||0)*(f.metroCaixaArValor||0);
  const shaft=(f.metroShaftQtd||0)*(f.metroShaftValor||0);
  const metro=forro+linear+caixa+shaft;
  const diaria=(f.diaria||0)*(f.dias||0)+(f.diaria||0)*(f.sabados||0)+(f.horasExtra||0)*(f.valorHoraExtra||0);
  const bruto=diaria+metro;
  const vales=(f.vales||[]).reduce((s,v)=>s+(parseFloat(v.valor)||0),0);
  const set=(id,v)=>{const e=document.getElementById(id);if(e)e.textContent=formatarMoeda(v);};
  set('metro-forro-total-'+id,forro); set('metro-linear-total-'+id,linear);
  set('metro-caixa-total-'+id,caixa); set('metro-shaft-total-'+id,shaft);
  set('metro-total-'+id,metro); set('salario-metro-'+id,metro);
  set('salario-bruto-'+id,bruto); set('salario-liquido-'+id,bruto-vales);
  atualizarResumo();
}
function updateFuncionarioField(id,campo,valor){
  const f=funcionarios.find(x=>x.id===id);
  if(!f)return;
  const numericFields=['diaria','dias','sabados','horasExtra','valorHoraExtra',
    'metroForroM2Qtd','metroForroM2Valor','metroLinearQtd','metroLinearValor',
    'metroCaixaArQtd','metroCaixaArValor','metroShaftQtd','metroShaftValor'];
  f[campo]=numericFields.includes(campo)?(parseFloat(valor)||0):valor;

  // Recalcula e atualiza imediatamente os totais do funcionário e da folha.
  // O onchange só acontece quando o usuário termina o campo, evitando
  // que a tabela fique pulando enquanto ele está digitando.
  renderFuncionarios();
}
function updateFuncionario(id,campo,valor){
  const f=funcionarios.find(x=>x.id===id);if(!f)return;
  if(['diaria','dias','sabados','horasExtra','valorHoraExtra','metroForroM2Qtd','metroForroM2Valor','metroLinearQtd','metroLinearValor','metroCaixaArQtd','metroCaixaArValor','metroShaftQtd','metroShaftValor'].includes(campo))f[campo]=parseFloat(valor)||0;else f[campo]=valor;
  renderFuncionarios();
  atualizarResumo();
}
function toggleSemanaPaga(id){const f=funcionarios.find(x=>x.id===id);if(!f)return;f.semanaPaga=!f.semanaPaga;renderFuncionarios();atualizarFinanceiroRecebido();}
function toggleValePago(funcId,valeIdx){
  const f=funcionarios.find(x=>x.id===funcId);
  if(!f || !f.vales[valeIdx]) return;

  const vale=f.vales[valeIdx];
  const g=gastos.find(x=>x.id===vale.gastoId);

  // O vale e o seu status visual são sincronizados com o gasto correspondente.
  // Assim, ao marcar no quadro do funcionário, ele fica verde imediatamente.
  if(g){
    toggleGastoPago(g.id);
    // toggleGastoPago já atualiza o objeto do vale pelo gastoId.
  }else{
    // Compatibilidade com vales antigos que não tenham gasto vinculado.
    vale.pago=!vale.pago;
    renderFuncionarios();
    atualizarFinanceiroRecebido();
    atualizarResumo();
  }
}

function toggleFuncionario(id){
  const f=funcionarios.find(x=>x.id===id);
  if(!f)return;
  f.aberto=!f.aberto;
  renderFuncionarios();
}

function addValeRapido(funcId){
  atualizarSelectsModal();
  document.getElementById('modal-gasto').style.display='flex';
  document.getElementById('gasto-tipo').value='VALE';
  document.getElementById('gasto-desc').value='';
  document.getElementById('gasto-valor').value='';
  const sf=document.getElementById('gasto-funcionario');
  sf.value=String(funcId);
  toggleCamposGasto();
  document.getElementById('gasto-desc').focus();
}

function renderFuncionarios(){
  const c=document.getElementById('funcionarios-list');
  c.innerHTML='';
  let totalFolhaBruto=0,totalVales=0,totalLiquido=0;

  funcionarios.forEach(f=>{
    const salarioDiaria=(f.diaria*f.dias)+(f.diaria*f.sabados)+(f.horasExtra*f.valorHoraExtra);
    const metroForro=(f.metroForroM2Qtd*f.metroForroM2Valor);
    const metroLinear=(f.metroLinearQtd*f.metroLinearValor);
    const metroCaixa=(f.metroCaixaArQtd*f.metroCaixaArValor);
    const metroShaft=(f.metroShaftQtd*f.metroShaftValor);
    const salarioMetro=metroForro+metroLinear+metroCaixa+metroShaft;
    const salarioBruto=salarioDiaria+salarioMetro;
    const valesFunc=f.vales.reduce((sum,v)=>sum+(parseFloat(v.valor)||0),0);
    const salarioLiquido=salarioBruto-valesFunc;

    totalFolhaBruto+=salarioBruto;
    totalVales+=valesFunc;
    totalLiquido+=salarioLiquido;

    const card=document.createElement('div');
    card.className='func-card'+(f.semanaPaga?' pago':'');
    const aberto=!!f.aberto;

    let valesResumo=f.vales.length
      ? `🎟️ ${f.vales.length} vale${f.vales.length>1?'s':''} • ${formatarMoeda(valesFunc)}`
      : '🎟️ Nenhum vale';

    let valesHtml='';
    if(f.vales.length>0){
      valesHtml=`<div style="margin-top:10px;padding-top:10px;border-top:1px dashed #cbd5e1;">
        <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:6px;">
          <div style="font-size:0.8rem;color:#64748b;font-weight:600;">📋 Vales (descontam do salário):</div>
          <button class="btn btn-yellow" style="padding:5px 9px;font-size:.72rem;" onclick="event.stopPropagation();addValeRapido(${f.id})">+ Vale</button>
        </div>
        ${f.vales.map((v,vi)=>`<div class="vale-row">
          <span>${v.desc} — <b style="color:#dc2626;">${formatarMoeda(v.valor)}</b></span>
          <label style="display:flex;align-items:center;gap:4px;padding:3px 7px;border-radius:7px;background:${v.pago?'#dcfce7':'#fff7ed'};cursor:pointer;">
            <input type="checkbox" ${v.pago?'checked':''} onchange="toggleValePago(${f.id},${vi})">
            <span style="color:${v.pago?'#059669':'#f59e0b'};font-weight:800;">${v.pago?'✓ PAGO':'⏳ NÃO PAGO'}</span>
          </label>
        </div>`).join('')}</div>`;
    }else{
      valesHtml=`<div style="margin-top:10px;text-align:right;">
        <button class="btn btn-yellow" style="padding:6px 10px;font-size:.75rem;" onclick="event.stopPropagation();addValeRapido(${f.id})">+ Adicionar Vale</button>
      </div>`;
    }

    const pagamentoTexto=f.semanaPaga?'✓ PAGO':'⏳ NÃO PAGO';
    const pagamentoCor=f.semanaPaga?'#059669':'#f59e0b';

    card.innerHTML=`
      <div onclick="toggleFuncionario(${f.id})" style="cursor:pointer;">
        <div class="row-flex" style="margin-bottom:6px;align-items:center;">
          <span style="font-size:1.05rem;">${aberto?'▼':'▶'}</span>
          <input type="text" class="input" placeholder="Nome do funcionário" value="${f.nome}"
            onclick="event.stopPropagation()" onchange="updateFuncionario(${f.id},'nome',this.value)"
            style="flex:1;min-width:0;font-weight:800;">
          <span style="font-size:.72rem;color:#64748b;white-space:nowrap;">${valesResumo}</span>
          <button class="btn btn-blue" style="padding:6px 9px;font-size:.72rem;" onclick="event.stopPropagation();addValeRapido(${f.id})">+ Vale</button>
          <button class="btn btn-red" style="padding:6px 9px;" onclick="event.stopPropagation();removeFuncionario(${f.id})">✕</button>
        </div>

        <div style="display:flex;align-items:center;justify-content:space-between;gap:8px;flex-wrap:wrap;">
          <div>
            <span style="font-size:.75rem;color:#64748b;">💵 Sobra da semana:</span>
            <b style="font-size:.95rem;color:#059669;">${formatarMoeda(salarioLiquido)}</b>
          </div>
          <label onclick="event.stopPropagation()" style="display:flex;align-items:center;gap:5px;padding:5px 9px;border-radius:8px;background:${f.semanaPaga?'#dcfce7':'#fff7ed'};color:${pagamentoCor};font-size:.75rem;font-weight:800;cursor:pointer;">
            <input type="checkbox" ${f.semanaPaga?'checked':''} onchange="toggleSemanaPaga(${f.id})">
            ${pagamentoTexto}
          </label>
        </div>
      </div>

      <div id="detalhes-func-${f.id}" style="display:${aberto?'block':'none'};margin-top:12px;">
        <div class="abas">
          <div class="aba active" id="aba-diaria-${f.id}" onclick="mostrarAba(${f.id},'diaria')">📅 Diária</div>
          <div class="aba" id="aba-metro-${f.id}" onclick="mostrarAba(${f.id},'metro')">📏 Metro</div>
        </div>

        <div id="sec-diaria-${f.id}">
          <div class="func-grid-3">
            <div><label>💵 Diária R$</label><input type="number" class="input input-small" step="0.01" value="${f.diaria||''}" onchange="updateFuncionario(${f.id},'diaria',this.value)"></div>
            <div><label>📅 Dias</label><input type="number" class="input input-small" value="${f.dias||''}" onchange="updateFuncionario(${f.id},'dias',this.value)"></div>
            <div><label>📅 Sábados</label><input type="number" class="input input-small" value="${f.sabados||''}" onchange="updateFuncionario(${f.id},'sabados',this.value)"></div>
            <div><label>⏰ H.Extra Qtd</label><input type="number" class="input input-small" step="0.5" value="${f.horasExtra||''}" onchange="updateFuncionario(${f.id},'horasExtra',this.value)"></div>
            <div><label>⏰ H.Extra R$</label><input type="number" class="input input-small" step="0.01" value="${f.valorHoraExtra||''}" onchange="updateFuncionario(${f.id},'valorHoraExtra',this.value)"></div>
            <div style="display:flex;align-items:flex-end;justify-content:center;padding-bottom:4px;"><span style="font-size:0.9rem;font-weight:700;color:#3b82f6;">${formatarMoeda(salarioDiaria)}</span></div>
          </div>
        </div>

        <div id="sec-metro-${f.id}" style="display:none;">
          <div class="metro-obra"><label>🏗️ NOME DA OBRA</label><input type="text" class="input" placeholder="Ex: Obra Praia" value="${f.metroObra}" onchange="updateFuncionario(${f.id},'metroObra',this.value)" style="margin-top:4px;"></div>
          <div style="font-size:0.8rem;color:#64748b;font-weight:600;margin-bottom:6px;">Preencha Qtd e Valor unitário:</div>
          <div class="func-grid-4">
            <div><label style="font-size:0.65rem;">FORRO M² Qtd</label><input type="number" class="input input-small" step="0.1" value="${f.metroForroM2Qtd||''}" oninput="updateMetroLive(${f.id},'metroForroM2Qtd',this.value)"></div>
            <div><label style="font-size:0.65rem;">FORRO M² R$</label><input type="number" class="input input-small" step="0.01" value="${f.metroForroM2Valor||''}" oninput="updateMetroLive(${f.id},'metroForroM2Valor',this.value)"></div>
            <div style="grid-column:span 2;display:flex;align-items:flex-end;justify-content:flex-end;padding-bottom:4px;"><span id="metro-forro-total-${f.id}" style="font-size:0.85rem;color:#3b82f6;font-weight:700;">${formatarMoeda(metroForro)}</span></div>
            <div><label style="font-size:0.65rem;">LINEAR Qtd</label><input type="number" class="input input-small" step="0.1" value="${f.metroLinearQtd||''}" oninput="updateMetroLive(${f.id},'metroLinearQtd',this.value)"></div>
            <div><label style="font-size:0.65rem;">LINEAR R$</label><input type="number" class="input input-small" step="0.01" value="${f.metroLinearValor||''}" oninput="updateMetroLive(${f.id},'metroLinearValor',this.value)"></div>
            <div style="grid-column:span 2;display:flex;align-items:flex-end;justify-content:flex-end;padding-bottom:4px;"><span id="metro-linear-total-${f.id}" style="font-size:0.85rem;color:#3b82f6;font-weight:700;">${formatarMoeda(metroLinear)}</span></div>
            <div><label style="font-size:0.65rem;">CAIXA AR Qtd</label><input type="number" class="input input-small" value="${f.metroCaixaArQtd||''}" oninput="updateMetroLive(${f.id},'metroCaixaArQtd',this.value)"></div>
            <div><label style="font-size:0.65rem;">CAIXA AR R$</label><input type="number" class="input input-small" step="0.01" value="${f.metroCaixaArValor||''}" oninput="updateMetroLive(${f.id},'metroCaixaArValor',this.value)"></div>
            <div style="grid-column:span 2;display:flex;align-items:flex-end;justify-content:flex-end;padding-bottom:4px;"><span id="metro-caixa-total-${f.id}" style="font-size:0.85rem;color:#3b82f6;font-weight:700;">${formatarMoeda(metroCaixa)}</span></div>
            <div><label style="font-size:0.65rem;">SHAFT Qtd</label><input type="number" class="input input-small" value="${f.metroShaftQtd||''}" oninput="updateMetroLive(${f.id},'metroShaftQtd',this.value)"></div>
            <div><label style="font-size:0.65rem;">SHAFT R$</label><input type="number" class="input input-small" step="0.01" value="${f.metroShaftValor||''}" oninput="updateMetroLive(${f.id},'metroShaftValor',this.value)"></div>
            <div style="grid-column:span 2;display:flex;align-items:flex-end;justify-content:flex-end;padding-bottom:4px;"><span id="metro-shaft-total-${f.id}" style="font-size:0.85rem;color:#3b82f6;font-weight:700;">${formatarMoeda(metroShaft)}</span></div>
          </div>
          <div style="text-align:right;padding:8px;background:#eff6ff;border-radius:8px;margin-top:8px;"><span style="font-size:0.85rem;color:#3b82f6;font-weight:600;">Total Metro: </span><span id="metro-total-${f.id}" style="font-size:1rem;color:#1e40af;font-weight:700;">${formatarMoeda(salarioMetro)}</span></div>
        </div>

        <div class="salario-box">
          <div class="salario-linha"><span class="label">📅 Diária:</span><span class="valor" style="color:#3b82f6;">${formatarMoeda(salarioDiaria)}</span></div>
          <div class="salario-linha"><span class="label">📏 Metro:</span><span id="salario-metro-${f.id}" class="valor" style="color:#3b82f6;">${formatarMoeda(salarioMetro)}</span></div>
          <div class="salario-linha" style="border-top:1px solid #e2e8f0;padding-top:4px;margin-top:4px;"><span class="label">💰 Total Bruto:</span><span id="salario-bruto-${f.id}" class="valor" style="color:#0f172a;font-weight:700;">${formatarMoeda(salarioBruto)}</span></div>
          <div class="salario-linha"><span class="label">📉 Total Vales:</span><span class="valor" style="color:#dc2626;">- ${formatarMoeda(valesFunc)}</span></div>
          <div class="salario-linha liquido"><span class="label">💵 A Receber:</span><span id="salario-liquido-${f.id}" class="valor">${formatarMoeda(salarioLiquido)}</span></div>
        </div>

        ${valesHtml}

        <div style="margin-top:10px;text-align:right;">
          <button class="btn btn-pdf" onclick="event.stopPropagation();gerarPDFFuncionario(${f.id})">📄 PDF</button>
        </div>
      </div>`;
    c.appendChild(card);
  });

  document.getElementById('total-folha').textContent=formatarMoeda(totalFolhaBruto);
  document.getElementById('total-vales-func').textContent=formatarMoeda(totalVales);
  document.getElementById('total-liquido-func').textContent=formatarMoeda(totalLiquido);
  atualizarResumo();
}


function mostrarAba(funcId,aba){
  document.getElementById('aba-diaria-'+funcId).classList.toggle('active',aba==='diaria');
  document.getElementById('aba-metro-'+funcId).classList.toggle('active',aba==='metro');
  document.getElementById('sec-diaria-'+funcId).style.display=aba==='diaria'?'block':'none';
  document.getElementById('sec-metro-'+funcId).style.display=aba==='metro'?'block':'none';
}

function addGasto(){
  document.getElementById('modal-gasto').style.display='flex';
  document.getElementById('gasto-tipo').value='MATERIAL';
  document.getElementById('gasto-desc').value='';
  document.getElementById('gasto-valor').value='';
  atualizarSelectsModal();
  toggleCamposGasto();
}
function fecharModalGasto(){ document.getElementById('modal-gasto').style.display='none'; }

function atualizarSelectsModal(){
  const sf=document.getElementById('gasto-funcionario');
  sf.innerHTML=funcionarios.map(f=>`<option value="${f.id}">${f.nome||'Sem nome'}</option>`).join('');

  const si=document.getElementById('gasto-investidor');
  si.innerHTML=investidores.map(inv=>`<option value="${inv.id}">${inv.nome} (${formatarMoeda(inv.saldo)})</option>`).join('');
  if(investidores.length===0) si.innerHTML='<option value="">Cadastre um investidor primeiro</option>';

  const ss=document.getElementById('gasto-servico');
  ss.innerHTML=servicos
    .filter(s=>(s.desc||'').trim() && (parseFloat(s.valor)||0)>0)
    .map(s=>`<option value="${s.id}">${s.desc} — ${formatarMoeda(s.valor)}</option>`)
    .join('');
  if(!ss.innerHTML) ss.innerHTML='<option value="">Cadastre uma obra primeiro</option>';
}

function toggleCamposGasto(){
  const tipo=document.getElementById('gasto-tipo').value;
  document.getElementById('gasto-funcionario-box').style.display=tipo==='VALE'?'block':'none';
  document.getElementById('gasto-servico-box').style.display=tipo==='DINHEIRO_EMPRESTADO'?'block':'none';

  if(tipo==='DINHEIRO_EMPRESTADO'){
    document.getElementById('gasto-desc').placeholder='Ex: Cliente vai pagar semana que vem';
  } else {
    document.getElementById('gasto-desc').placeholder='Ex: Material obra praia';
  }
}
document.getElementById('gasto-tipo').addEventListener('change',toggleCamposGasto);

function salvarGasto(){
  const tipo=document.getElementById('gasto-tipo').value;
  const desc=document.getElementById('gasto-desc').value.trim();
  const valor=parseFloat(document.getElementById('gasto-valor').value)||0;
  const funcId=document.getElementById('gasto-funcionario').value;
  const invId=document.getElementById('gasto-investidor').value;
  const servicoId=document.getElementById('gasto-servico').value;

  if(!desc||valor<=0){alert('Preencha descrição e valor!');return;}
  if(!invId){alert('Cadastre um investidor primeiro!');return;}

  const investidor=investidores.find(i=>i.id==invId);
  if(!investidor){alert('Investidor inválido!');return;}
  if(investidor.saldo<valor){alert('Saldo insuficiente no investidor '+investidor.nome+'!');return;}

  if(tipo==='DINHEIRO_EMPRESTADO'){
    if(!servicoId){alert('Selecione a obra que receberá o dinheiro emprestado.');return;}
    const servico=servicos.find(s=>s.id==servicoId);
    if(!servico){alert('Obra inválida!');return;}

    const jaExiste=gastos.find(g=>g.tipo==='DINHEIRO_EMPRESTADO' && g.servicoId===servico.id && !g.pago);
    if(jaExiste){alert('Esta obra já possui dinheiro emprestado aguardando recebimento.');return;}

    investidor.saldo-=valor;

    const gasto={
      id:Date.now(),
      tipo,
      desc,
      valor,
      investidorId:invId,
      investidorNome:investidor.nome,
      servicoId:servico.id,
      servicoNome:servico.desc,
      pago:false,
      data:new Date().toLocaleDateString('pt-BR'),
      observacao:desc,
      reembolsadoAutomaticamente:false
    };

    gastos.push(gasto);
    // O empréstimo é apenas um destaque visual; não altera o status da obra.

    fecharModalGasto();
    renderGastos();
    renderServicos();
    renderInvestidores();
    atualizarResumo();
    return;
  }

  investidor.saldo-=valor;

  const gasto={id:Date.now(),tipo,desc,valor,investidorId:invId,investidorNome:investidor.nome,pago:false};

  if(tipo==='VALE'&&funcId){
    const func=funcionarios.find(f=>f.id==funcId);
    if(func){
      func.vales.push({desc,valor,pago:false,gastoId:gasto.id});
      gasto.funcionarioId=funcId;
      gasto.funcionarioNome=func.nome;
    }
  }

  gastos.push(gasto);
  fecharModalGasto();
  renderGastos();
  renderFuncionarios();
  renderInvestidores();
  atualizarResumo();
}

function removeGasto(id){
  const idx=gastos.findIndex(g=>g.id===id);
  if(idx===-1)return;
  const g=gastos[idx];
  const inv=investidores.find(i=>i.id==g.investidorId);

  if(g.tipo==='DINHEIRO_EMPRESTADO'){
    if(!g.pago && inv) inv.saldo+=g.valor;
    const s=servicos.find(x=>x.id===g.servicoId);
    if(s && s.status!=='recebida') s.status='pendente';
  } else {
    if(!g.pago&&inv)inv.saldo+=g.valor;
    if(g.funcionarioId){
      const func=funcionarios.find(f=>f.id==g.funcionarioId);
      if(func)func.vales=func.vales.filter(v=>v.gastoId!==g.id);
    }
  }

  gastos.splice(idx,1);
  renderGastos();
  renderServicos();
  renderFuncionarios();
  renderInvestidores();
  atualizarResumo();
}

function toggleGastoPago(id){
  const g=gastos.find(x=>x.id===id);
  if(!g)return;

  const inv=investidores.find(i=>i.id==g.investidorId);
  if(!inv)return;

  const novoStatus=!g.pago;

  // MATERIAL é neutro para o Caixa das Obras, mas o valor volta ao INVESTIDOR
  // quando marcado como pago, exatamente como o Vale.
  if(g.tipo==='MATERIAL'){
    const valor=parseFloat(g.valor)||0;

    if(novoStatus){
      inv.saldo += valor;
      g.pago=true;
    }else{
      if(inv.saldo < valor){
        alert('Saldo insuficiente no investidor '+inv.nome+' para desfazer o pagamento!');
        return;
      }
      inv.saldo -= valor;
      g.pago=false;
    }

    renderGastos();
    renderInvestidores();
    atualizarResumo();
    return;
  }

  if(g.tipo==='DINHEIRO_EMPRESTADO'){
    const valor=parseFloat(g.valor)||0;

    if(novoStatus){
      inv.saldo += valor;
      g.pago=true;
      g.reembolsadoAutomaticamente=true;
      g.recebimentoObraData=new Date().toLocaleDateString('pt-BR');
    }else{
      if(inv.saldo < valor){
        alert('Não é possível desfazer: esse dinheiro já foi usado novamente no Capital de Giro.');
        return;
      }
      inv.saldo -= valor;
      g.pago=false;
      g.reembolsadoAutomaticamente=false;
      g.recebimentoObraData='';
    }

    // NÃO altera o status da obra.
    renderGastos();
    renderInvestidores();
    atualizarResumo();
    return;
  }

  if(novoStatus){
    inv.saldo += g.valor;
  }else{
    if(inv.saldo < g.valor){
      alert('Saldo insuficiente no investidor '+inv.nome+' para desfazer reembolso!');
      return;
    }
    inv.saldo -= g.valor;
  }

  g.pago=novoStatus;

  if(g.funcionarioId&&g.tipo==='VALE'){
    const func=funcionarios.find(f=>f.id===g.funcionarioId);
    if(func){
      const v=func.vales.find(v=>v.gastoId===g.id);
      if(v)v.pago=novoStatus;
    }
  }

  renderGastos();
  renderFuncionarios();
  renderInvestidores();
  atualizarResumo();
}

function filtrarGastos(tipo){
  filtroAtual=tipo;
  document.querySelectorAll('.filtro').forEach(el=>{
    if(el.dataset.tipo===tipo)el.classList.add('active');
    else el.classList.remove('active');
  });
  renderGastos();
}

function renderGastos(){
  const c=document.getElementById('gastos-list');
  c.innerHTML='';
  const filtrados=filtroAtual==='TODOS'?gastos:gastos.filter(g=>g.tipo===filtroAtual);
  const totais={MATERIAL:0,VALE:0,GASTO:0,PESSOAL:0,CUSTO:0,DINHEIRO_EMPRESTADO:0};
  let totalGeral=0,totalNaoPago=0,totalPago=0;

  const cores={
    MATERIAL:'#3b82f6',
    VALE:'#f59e0b',
    GASTO:'#ef4444',
    PESSOAL:'#8b5cf6',
    CUSTO:'#64748b',
    DINHEIRO_EMPRESTADO:'#f97316'
  };

  filtrados.forEach(g=>{
    totais[g.tipo]=(totais[g.tipo]||0)+g.valor;
    totalGeral+=g.valor;

    if(g.pago)totalPago+=g.valor;
    else totalNaoPago+=g.valor;

    const d=document.createElement('div');
    d.className=`gasto-row cor-${g.tipo} ${g.pago?'pago':''}`;
    d.style.borderLeft=`4px solid ${g.pago?'#10b981':cores[g.tipo]}`;

    let statusHtml='';
    if(g.tipo==='DINHEIRO_EMPRESTADO'){
      statusHtml = `<label style="display:flex;align-items:center;gap:4px;cursor:pointer;background:${g.pago?'#d1fae5':'#ffedd5'};padding:4px 8px;border-radius:6px;font-size:.75rem;font-weight:700;color:${g.pago?'#059669':'#c2410c'};white-space:nowrap;">
        <input type="checkbox" ${g.pago?'checked':''} onchange="toggleGastoPago(${g.id})" style="width:16px;height:16px;cursor:pointer;">
        ${g.pago?'✓ Pago / Recebido':'⏳ Não pago / Aguardando'}
      </label>`;
    } else {
      statusHtml = `<label style="display:flex;align-items:center;gap:4px;cursor:pointer;background:${g.pago?'#d1fae5':'#fef3c7'};padding:4px 8px;border-radius:6px;font-size:0.75rem;font-weight:700;color:${g.pago?'#059669':'#d97706'};white-space:nowrap;">
        <input type="checkbox" ${g.pago?'checked':''} onchange="toggleGastoPago(${g.id})" style="width:16px;height:16px;cursor:pointer;accent-color:${g.pago?'#059669':'#d97706'};">
        ${g.pago?'✓ Reembolsado':'⏳ Reembolsar'}
      </label>`;
    }

    d.innerHTML=`<div class="info">
      <div class="desc">${g.tipo==='DINHEIRO_EMPRESTADO'?'🟠 '+(g.servicoNome||g.desc):g.desc}</div>
      <div class="meta">${g.tipo==='DINHEIRO_EMPRESTADO'?'DINHEIRO EMPRESTADO • '+(g.investidorNome||'')+(g.data?' • '+g.data:''):(g.tipo+' • '+g.investidorNome+(g.funcionarioNome?' • '+g.funcionarioNome:''))}</div>
    </div>
    <div style="display:flex;align-items:center;gap:8px;flex-shrink:0;">
      <span class="valor" style="color:${g.pago?'#059669':(g.tipo==='DINHEIRO_EMPRESTADO'?'#f97316':'#dc2626')};">${formatarMoeda(g.valor)}</span>
      ${statusHtml}
      <button class="btn btn-red" style="padding:6px 10px;font-size:0.8rem;" onclick="removeGasto(${g.id})">✕</button>
    </div>`;

    c.appendChild(d);
  });

  document.getElementById('total-gastos').textContent=formatarMoeda(totalGeral);
  document.getElementById('total-gastos-nao-pago').textContent=formatarMoeda(totalNaoPago);
  document.getElementById('total-gastos-pago').textContent=formatarMoeda(totalPago);
  document.getElementById('total-material').textContent=formatarMoeda(totais.MATERIAL);
  document.getElementById('total-vale').textContent=formatarMoeda(totais.VALE);
  document.getElementById('total-gasto').textContent=formatarMoeda(totais.GASTO);
  document.getElementById('total-pessoal').textContent=formatarMoeda(totais.PESSOAL);
  document.getElementById('total-custo').textContent=formatarMoeda(totais.CUSTO);

  const elEmprestado=document.getElementById('total-emprestado');
  if(elEmprestado)elEmprestado.textContent=formatarMoeda(totais.DINHEIRO_EMPRESTADO);

  atualizarResumo();
}

function addInvestidor(){
  investidorEditandoId=null;
  document.getElementById('modal-investidor').style.display='flex';
  document.getElementById('titulo-modal-investidor').textContent='➕ Novo Investidor';
  document.getElementById('btn-salvar-investidor').textContent='💾 Salvar';
  document.getElementById('inv-nome').value='';
  document.getElementById('inv-valor').value='';
}
function editarInvestidor(id){
  const inv=investidores.find(i=>i.id===id);
  if(!inv)return;
  investidorEditandoId=id;
  document.getElementById('modal-investidor').style.display='flex';
  document.getElementById('titulo-modal-investidor').textContent='✏️ Editar Capital de Giro';
  document.getElementById('btn-salvar-investidor').textContent='💾 Salvar Alterações';
  document.getElementById('inv-nome').value=inv.nome||'';
  document.getElementById('inv-valor').value=inv.aplicado||0;
}
function fecharModalInvestidor(){
  document.getElementById('modal-investidor').style.display='none';
  investidorEditandoId=null;
}
function salvarInvestidor(){
  const nome=document.getElementById('inv-nome').value.trim();
  const valor=parseFloat(String(document.getElementById('inv-valor').value).replace(',','.'))||0;
  if(!nome||valor<=0){alert('Preencha nome e valor!');return;}
  if(investidorEditandoId!==null){
    const inv=investidores.find(i=>i.id===investidorEditandoId);
    if(!inv)return;
    const usado=Math.max(0,(parseFloat(inv.aplicado)||0)-(parseFloat(inv.saldo)||0));
    if(valor<usado){alert('O valor total não pode ser menor que o valor já utilizado: '+formatarMoeda(usado));return;}
    inv.nome=nome; inv.aplicado=valor; inv.saldo=valor-usado;
  }else{
    investidores.push({id:Date.now(),nome,aplicado:valor,saldo:valor});
  }
  fecharModalInvestidor(); renderInvestidores(); renderGastos(); atualizarResumo();
}
function removeInvestidor(id){
  investidores=investidores.filter(i=>i.id!==id);
  renderInvestidores();
  atualizarResumo();
}
function atualizarFinanceiroRecebido(){
  // 1) Total que efetivamente entrou pelas obras marcadas como recebidas.
  const totalRecebido = servicos.reduce((total,obra)=>{
    return total + (obra.status==='recebida' ? (parseFloat(obra.valor)||0) : 0);
  },0);

  // 2) Tudo que já foi efetivamente pago com o caixa das obras.
  // Empréstimos ficam fora: são movimentação do Capital de Giro.
  const gastosPagos = gastos.reduce((total,g)=>{
    if(g.tipo==='DINHEIRO_EMPRESTADO' || g.tipo==='MATERIAL') return total;
    return total + (g.pago ? (parseFloat(g.valor)||0) : 0);
  },0);

  // 3) Funcionários: quando "SEMANA PAGA" é marcado, desconta o salário líquido.
  // O vale já está incluído em gastosPagos, então aqui usamos o salário líquido
  // para não descontar o vale duas vezes.
  const funcionariosPagos = funcionarios.reduce((total,f)=>{
    if(!f.semanaPaga) return total;

    const diaria=(f.diaria||0)*(f.dias||0)+(f.diaria||0)*(f.sabados||0);
    const extras=(f.horasExtra||0)*(f.valorHoraExtra||0);
    const metro=(f.metroForroM2Qtd||0)*(f.metroForroM2Valor||0)
      +(f.metroLinearQtd||0)*(f.metroLinearQtd?f.metroLinearValor||0:0)
      +(f.metroCaixaArQtd||0)*(f.metroCaixaArValor||0)
      +(f.metroShaftQtd||0)*(f.metroShaftValor||0);
    const bruto=diaria+extras+metro;
    const vales=(f.vales||[]).reduce((s,v)=>s+(parseFloat(v.valor)||0),0);
    return total + Math.max(0,bruto-vales);
  },0);

  const totalPago=gastosPagos+funcionariosPagos;
  const saldo=totalRecebido-totalPago;

  const a=document.getElementById('total-recebido-obras');
  const p=document.getElementById('total-pago-com-recebido');
  const s=document.getElementById('saldo-recebido-obras');

  if(a)a.textContent=formatarMoeda(totalRecebido);
  if(p)p.textContent=formatarMoeda(totalPago);
  if(s){
    s.textContent=formatarMoeda(saldo);
    s.style.color=saldo<0?'#dc2626':'#2563eb';
  }
}


function renderInvestidores(){
  const c=document.getElementById('investidores-list');
  c.innerHTML='';
  let totalCap=0,totalUsado=0,totalSaldo=0;
  investidores.forEach(inv=>{
    totalCap+=inv.aplicado;
    const usado=inv.aplicado-inv.saldo;
    totalUsado+=usado;
    totalSaldo+=inv.saldo;
    const card=document.createElement('div');
    card.className='inv-card';
    const pct=inv.aplicado>0?(usado/inv.aplicado*100):0;
    card.innerHTML=`<div style="display:flex;justify-content:space-between;align-items:center;">
      <div><div style="font-weight:700;color:#0f172a;font-size:1rem;">${inv.nome}</div><div style="font-size:0.8rem;color:#64748b;">💰 Aplicado: ${formatarMoeda(inv.aplicado)}</div></div>
      <div style="text-align:right;"><div style="font-weight:700;color:${inv.saldo>0?'#059669':'#dc2626'};font-size:1.15rem;">${formatarMoeda(inv.saldo)}</div><div style="font-size:0.75rem;color:#94a3b8;">saldo disponível</div></div>
      <div style="display:flex;gap:6px;margin-left:10px;">
        <button class="btn btn-blue" style="padding:6px 9px;cursor:pointer;" onclick="editarInvestidor(${inv.id})">✏️ Editar</button>
        <button class="btn btn-red" style="padding:6px 9px;" onclick="removeInvestidor(${inv.id})">✕</button>
      </div>
    </div>
    <div class="inv-bar"><div class="inv-bar-fill" style="width:${pct}%"></div></div>
    <div style="display:flex;justify-content:space-between;margin-top:6px;font-size:0.8rem;">
      <span style="color:#64748b;">Usado (não reembolsado): <b style="color:#dc2626;">${formatarMoeda(usado)}</b></span>
      <span style="color:#64748b;">Livre: <b style="color:#059669;">${formatarMoeda(inv.saldo)}</b></span>
    </div>`;
    c.appendChild(card);
  });
  document.getElementById('total-capital').textContent=formatarMoeda(totalCap);
  document.getElementById('total-aplicado').textContent=formatarMoeda(totalUsado);
  document.getElementById('total-saldo').textContent=formatarMoeda(totalSaldo);
}

function atualizarResumo(){
  atualizarFinanceiroRecebido();
  const receita=servicos.reduce((sum,s)=>sum+(parseFloat(s.valor)||0),0);
  const folhaBruto=funcionarios.reduce((sum,f)=>{
    const diaria=(f.diaria*f.dias)+(f.diaria*f.sabados)+(f.horasExtra*f.valorHoraExtra);
    const metro=(f.metroForroM2Qtd*f.metroForroM2Valor)+(f.metroLinearQtd*f.metroLinearValor)+(f.metroCaixaArQtd*f.metroCaixaArValor)+(f.metroShaftQtd*f.metroShaftValor);
    return sum+diaria+metro;
  },0);
  const demaisGastos=gastos.filter(g=>g.tipo!=='VALE'&&g.tipo!=='MATERIAL'&&g.tipo!=='DINHEIRO_EMPRESTADO').reduce((sum,g)=>sum+g.valor,0);
  const lucro=receita-folhaBruto-demaisGastos;
  const porSocio=lucro/2;
  document.getElementById('res-receita').textContent=formatarMoeda(receita);
  document.getElementById('res-folha').textContent=formatarMoeda(folhaBruto);
  document.getElementById('res-gastos').textContent=formatarMoeda(demaisGastos);
  document.getElementById('res-lucro').textContent=formatarMoeda(lucro);
  document.getElementById('res-socio').textContent=formatarMoeda(porSocio);
}


function abrirQuadroApp(numero){
  const alvo=document.getElementById('quadro-app-'+numero);
  if(!alvo)return;

  // Mostra a área dos quadros; cada quadro é aberto/fechado de forma independente.
  document.getElementById('tela-quadro-app').classList.add('ativo');

  const aberto=alvo.style.display==='block';
  alvo.style.display=aberto?'none':'block';

  const menu=document.querySelector(`.menu-quadro[data-quadro="${numero}"]`);
  if(menu){
    menu.classList.toggle('menu-aberto',!aberto);
    const seta=menu.querySelector('.menu-seta');
    if(seta)seta.textContent=aberto?'›':'⌄';
  }
}

function fecharQuadroApp(numero){
  const alvo=document.getElementById('quadro-app-'+numero);
  if(alvo)alvo.style.display='none';

  const menu=document.querySelector(`.menu-quadro[data-quadro="${numero}"]`);
  if(menu){
    menu.classList.remove('menu-aberto');
    const seta=menu.querySelector('.menu-seta');
    if(seta)seta.textContent='›';
  }
}

function voltarMenuApp(){
  document.querySelectorAll('.quadro-tela').forEach(el=>el.style.display='none');
  document.querySelectorAll('.menu-quadro[data-quadro]').forEach(menu=>{
    menu.classList.remove('menu-aberto');
    const seta=menu.querySelector('.menu-seta');
    if(seta)seta.textContent='›';
  });
  window.scrollTo({top:0,behavior:'smooth'});
}



const RASCUNHO_STORAGE='gestao_financeira_rascunho';
let rLinhas=12,rColunas=6;

function renderRascunho(celulas){
  const table=document.getElementById('rascunho-grid'); if(!table)return;
  table.querySelector('thead tr').innerHTML='<th class="row-num"></th>'+
    Array.from({length:rColunas},(_,i)=>`<th>${String.fromCharCode(65+i)}</th>`).join('');
  const body=table.querySelector('tbody'); body.innerHTML='';

  for(let r=0;r<rLinhas;r++){
    const tr=document.createElement('tr');
    tr.innerHTML=`<td class="row-num">${r+1}</td>`;
    for(let c=0;c<rColunas;c++){
      const td=document.createElement('td');
      td.contentEditable='true'; td.spellcheck=false;
      td.dataset.r=r; td.dataset.c=c;
      td.dataset.formula=celulas?.[r]?.[c] || '';
      td.textContent=rascunhoExibir(td.dataset.formula);
      td.title=td.dataset.formula;

      td.addEventListener('focus',()=>{
        if(td.dataset.formula.startsWith('=')){
          td.textContent=td.dataset.formula;
          placeCaretEnd(td);
        }
      });
      td.addEventListener('blur',()=>{
        td.dataset.formula=td.textContent.trim();
        td.title=td.dataset.formula;
        td.textContent=rascunhoExibir(td.dataset.formula);
        salvarRascunho();
      });
      td.addEventListener('keydown',e=>{
        const r0=+td.dataset.r,c0=+td.dataset.c;
        let nr=r0,nc=c0;
        if(e.key==='Enter'){e.preventDefault();nr=Math.min(rLinhas-1,r0+1);}
        else if(e.key==='Tab'){e.preventDefault();nc=Math.min(rColunas-1,c0+1);}
        else if(e.key==='ArrowDown'){e.preventDefault();nr=Math.min(rLinhas-1,r0+1);}
        else if(e.key==='ArrowUp'){e.preventDefault();nr=Math.max(0,r0-1);}
        else return;
        td.blur();
        const next=document.querySelector(`#rascunho-grid td[data-r="${nr}"][data-c="${nc}"]`);
        if(next){next.focus();placeCaretEnd(next);}
      });
      tr.appendChild(td);
    }
    body.appendChild(tr);
  }
}
function placeCaretEnd(el){
  try{const range=document.createRange(),sel=window.getSelection();range.selectNodeContents(el);range.collapse(false);sel.removeAllRanges();sel.addRange(range);}catch(e){}
}

function dadosRascunho(){
  return Array.from({length:rLinhas},(_,r)=>Array.from({length:rColunas},(_,c)=>{
    const td=document.querySelector(`#rascunho-grid td[data-r="${r}"][data-c="${c}"]`);
    return td?td.textContent:'';
  }));
}
function salvarRascunho(){
  localStorage.setItem(RASCUNHO_STORAGE,JSON.stringify({linhas:rLinhas,colunas:rColunas,celulas:dadosRascunho()}));
}
function carregarRascunho(){
  try{
    const x=JSON.parse(localStorage.getItem(RASCUNHO_STORAGE)||'null');
    if(x){rLinhas=x.linhas||12;rColunas=x.colunas||6;renderRascunho(x.celulas);return;}
  }catch(e){}
  renderRascunho();
}
function rascunhoNovaLinha(){
  const d=dadosRascunho();
  d.push(Array(rColunas).fill(''));
  rLinhas++;
  renderRascunho(d);
  salvarRascunho();
}
function rascunhoApagarLinha(){
  if(rLinhas<=1){ alert('O rascunho precisa ter pelo menos 1 linha.'); return; }
  const d=dadosRascunho();
  d.pop();
  rLinhas--;
  renderRascunho(d);
  salvarRascunho();
}
function rascunhoNovaColuna(){
  const d=dadosRascunho();
  d.forEach(row=>row.push(''));
  rColunas++;
  renderRascunho(d);
  salvarRascunho();
}
function rascunhoApagarColuna(){
  if(rColunas<=1){ alert('O rascunho precisa ter pelo menos 1 coluna.'); return; }
  const d=dadosRascunho();
  d.forEach(row=>row.pop());
  rColunas--;
  renderRascunho(d);
  salvarRascunho();
}
function rascunhoSomar(){
  const n=dadosRascunho().flat().map(v=>Number(String(v).replace(/\./g,'').replace(',','.').replace(/[^\d.-]/g,''))).filter(Number.isFinite);
  document.getElementById('rascunho-resultado').textContent=formatarMoeda(n.reduce((a,b)=>a+b,0));
}
function limparRascunho(){
  if(!confirm('Limpar todas as anotações?'))return;
  localStorage.removeItem(RASCUNHO_STORAGE);rLinhas=12;rColunas=6;renderRascunho();
}

function rascunhoNumero(v){
  const s=String(v||'').trim().replace(/^R\$\s*/,'');
  if(!s)return 0;
  if(s.includes(',')&&s.includes('.'))return Number(s.replace(/\./g,'').replace(',','.'))||0;
  return Number(s.replace(',','.'))||0;
}
function rascunhoRaw(ref){
  const m=String(ref).toUpperCase().match(/^([A-Z]+)(\d+)$/); if(!m)return '';
  let col=0; for(const ch of m[1])col=col*26+(ch.charCodeAt(0)-64); col--;
  const row=+m[2]-1;
  const td=document.querySelector(`#rascunho-grid td[data-r="${row}"][data-c="${col}"]`);
  return td?(td.dataset.formula||''):'';
}
function rascunhoCalcFormula(raw,stack=[]){
  if(!String(raw).startsWith('='))return rascunhoNumero(raw);
  if(stack.length>30)return 0;
  let f=raw.slice(1).trim();
  const sm=f.match(/^SUM\(([A-Z]+\d+):([A-Z]+\d+)\)$/i);
  if(sm){
    const a=sm[1].match(/^([A-Z]+)(\d+)$/i),b=sm[2].match(/^([A-Z]+)(\d+)$/i);
    const col=x=>{let n=0;for(const ch of x)n=n*26+(ch.toUpperCase().charCodeAt(0)-64);return n-1;};
    if(!a||!b)return 0;
    let total=0;
    for(let r=+a[2]-1;r<=+b[2]-1;r++)for(let c=col(a[1]);c<=col(b[1]);c++){
      let n=c+1,s='';while(n){let rem=(n-1)%26;s=String.fromCharCode(65+rem)+s;n=Math.floor((n-1)/26);}
      const ref=s+(r+1); if(!stack.includes(ref))total+=rascunhoCalcFormula(rascunhoRaw(ref),[...stack,ref]);
    }
    return total;
  }
  f=f.replace(/\b[A-Z]{1,3}\d+\b/gi,m=>String(rascunhoCalcFormula(rascunhoRaw(m),[...stack,m])));
  if(!/^[0-9+\-*/().\s]+$/.test(f))return 0;
  try{const x=Function('"use strict";return ('+f+')')();return Number.isFinite(x)?x:0;}catch(e){return 0;}
}
function rascunhoExibir(raw){
  if(!raw)return '';
  return raw.startsWith('=')?formatarMoeda(rascunhoCalcFormula(raw)):raw;
}
function rascunhoSomar(){
  const total=dadosRascunho().flat().reduce((s,v)=>s+(String(v).startsWith('=')?rascunhoCalcFormula(v):rascunhoNumero(v)),0);
  document.getElementById('rascunho-resultado').textContent=formatarMoeda(total);
}

function rascunhoPrepararCelulas(){
  document.querySelectorAll('#rascunho-grid td[contenteditable="true"]').forEach(td=>{
    td.addEventListener('keydown',e=>{
      const r=+td.dataset.r,c=+td.dataset.c;
      let nr=r,nc=c;
      if(e.key==='Enter'){e.preventDefault();nr=Math.min(rLinhas-1,r+1);}
      else if(e.key==='Tab'){e.preventDefault();nc=Math.min(rColunas-1,c+1);}
      else if(e.key==='ArrowDown'){e.preventDefault();nr=Math.min(rLinhas-1,r+1);}
      else if(e.key==='ArrowUp'){e.preventDefault();nr=Math.max(0,r-1);}
      else if(e.key==='ArrowRight'){e.preventDefault();nc=Math.min(rColunas-1,c+1);}
      else if(e.key==='ArrowLeft'){e.preventDefault();nc=Math.max(0,c-1);}
      else return;
      const next=document.querySelector(`#rascunho-grid td[data-r="${nr}"][data-c="${nc}"]`);
      if(next){next.focus();document.execCommand('selectAll',false,null);}
    });
  });
}

init();
carregarRascunho();
</script>
</body>
</html>
