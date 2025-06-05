<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>PE sem Fome</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 20px;
      background: #f4f4f4;
      line-height: 1.6;
    }
    .card-container {
      display: flex;
      gap: 20px;
      margin-bottom: 20px;
      justify-content: center;
      align-items: center;
      flex-direction: column;
    }
    .title-area {
      text-align: center;
      margin-bottom: 20px;
    }
    .title-area img {
      width: 120px;
      height: auto;
    }
    .title-area h1 {
      margin-top: 10px;
      font-size: 24px;
      color: #333;
    }
    .card-buttons {
      display: flex;
      gap: 20px;
      flex-wrap: wrap;
      justify-content: center;
    }
    .card {
      flex: 1;
      min-width: 160px;
      max-width: 200px;
      padding: 20px;
      background: #fff;
      border: 1px solid #ddd;
      text-align: center;
      cursor: pointer;
      transition: 0.3s;
      border-radius: 10px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }
    .card img {
      width: 40px;
      height: 40px;
      margin-bottom: 10px;
    }
    .card:hover {
      background: #eef;
      transform: translateY(-2px);
      box-shadow: 0 4px 8px rgba(0,0,0,0.15);
    }
    .hidden {
      display: none !important; /* Ensure it overrides other display properties */
    }
    .form-section, .mensagem-section {
      background: #fff;
      padding: 20px;
      border-radius: 10px;
      max-width: 600px;
      margin: 20px auto;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }
    fieldset {
      border: 1px solid #ddd;
      border-radius: 5px;
      padding: 15px;
      margin-bottom: 15px;
    }
    legend {
      padding: 0 10px;
      font-weight: bold;
      color: #333;
    }
    label {
      display: block;
      margin-top: 15px;
      font-weight: bold;
      color: #555;
    }
    label.required:after {
      content: " *";
      color: red;
    }
    input, select, button, textarea {
      width: 100%;
      padding: 10px;
      margin-top: 5px;
      border: 1px solid #ddd;
      border-radius: 4px;
      box-sizing: border-box;
    }
    input:focus, select:focus {
      outline: none;
      border-color: #007BFF;
      box-shadow: 0 0 0 2px rgba(0,123,255,0.25);
    }
    .button-group {
      display: flex;
      gap: 10px;
      margin-top: 20px;
    }
    .button-blue {
      background-color: #007BFF;
      color: white;
      border: none;
      padding: 10px;
      cursor: pointer;
      flex: 1;
      border-radius: 4px;
      font-weight: bold;
      transition: background-color 0.3s;
    }
    .button-blue:hover {
      background-color: #0069d9;
    }
    .button-red {
      background-color: #dc3545;
      color: white;
      border: none;
      padding: 10px;
      cursor: pointer;
      flex: 1;
      border-radius: 4px;
      font-weight: bold;
      transition: background-color 0.3s;
    }
    .button-red:hover {
      background-color: #c82333;
    }
    .radio-group {
      display: flex;
      align-items: center;
      gap: 20px;
      margin-top: 10px;
      flex-wrap: wrap;
    }
    .radio-group label {
      display: flex;
      align-items: center;
      gap: 5px;
      font-weight: normal;
      margin-top: 0;
    }
    .error-message {
      color: red;
      font-size: 0.8em;
      margin-top: 5px;
      display: none;
    }
    .input-error {
      border-color: red !important;
    }

    /* Estilos para o Modal */
    .modal {
      position: fixed;
      z-index: 1000;
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
      overflow: auto;
      background-color: rgba(0,0,0,0.5); /* Dim background */
      display: flex; /* Used with .hidden to toggle visibility */
      align-items: center;
      justify-content: center;
    }

    .modal-content {
      background-color: #fefefe;
      padding: 25px;
      border: 1px solid #ddd;
      width: 90%;
      max-width: 550px;
      border-radius: 10px;
      box-shadow: 0 5px 15px rgba(0,0,0,0.3);
      text-align: left;
    }

    .modal-content h2 { /* Title: AVISO DE PRIVACIDADE */
      font-weight: bold;
      font-size: 18px; /* As requested */
      text-align: center;
      margin-top: 0;
      margin-bottom: 15px;
      color: #333;
    }

    .modal-content p {
      margin-bottom: 12px;
      font-size: 14px;
      line-height: 1.6;
      color: #555;
    }
     .modal-content p.privacy-notice-subtitle { /* "Aviso de Privacidade" text */
        font-weight: normal;
        font-size: 16px;
        color: #333;
        margin-bottom: 10px;
    }

    .modal-buttons-docs {
      display: flex;
      gap: 15px;
      margin-top: 20px;
      margin-bottom: 25px;
      justify-content: center;
    }

    .modal-buttons-docs button { /* Policy and Terms buttons */
      flex: 1;
      background-color: #6c757d; /* A neutral color */
      border-color: #6c757d;
      color: white; /* Ensure text is visible */
    }
    .modal-buttons-docs button:hover {
      background-color: #5a6268;
    }


    .aceite-termos-popup {
      display: flex;
      align-items: center;
      gap: 10px;
      margin: 25px 0;
      justify-content: center;
    }

    .aceite-termos-popup input[type="checkbox"] {
      width: auto;
      margin-top: 0;
      transform: scale(1.2);
    }

    .aceite-termos-popup label {
      font-weight: normal;
      margin-top: 0;
      font-size: 15px;
      color: #333;
    }

    .arrow {
      margin-left: 8px;
    }


    @media (max-width: 600px) {
      .card-buttons {
        flex-direction: column;
        align-items: center;
      }
      .card {
        width: 100%;
        max-width: 100%;
      }
      .button-group {
        flex-direction: column;
      }
      .modal-content {
        width: 95%;
        padding: 20px;
      }
      .modal-buttons-docs {
        flex-direction: column;
      }
    }
  </style>
</head>
<body>

  <header class="title-area">
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/59/Bandeira_de_Pernambuco.svg/640px-Bandeira_de_Pernambuco.svg.png" alt="Bandeira de Pernambuco">
    <h1>PE sem Fome</h1>
  </header>

  <main>
    <section class="card-container">
      <div class="card-buttons">
        <button class="card" onclick="selecionarOpcao('mim')" aria-label="Ajuda para mim">
          <img src="https://img.icons8.com/ios-filled/50/user.png" alt="Ícone de pessoa">
          Para mim
        </button>
        <button class="card" onclick="selecionarOpcao('alguem')" aria-label="Ajudar alguém">
          <img src="https://img.icons8.com/ios-filled/50/group-foreground-selected.png" alt="Ícone de grupo de pessoas">
          Ajudar alguém
        </button>
      </div>
    </section>

    <div id="avisoPrivacidadeModal" class="modal hidden">
      <div class="modal-content">
        <h2>AVISO DE PRIVACIDADE</h2>
        <p>A SECRETARIA DE ASSISTÊNCIA SOCIAL, COMBATE À FOME E POLÍTICAS SOBRE DROGAS (SAS) de Pernambuco, no âmbito do programa "PE sem Fome", está adotando todas as medidas de segurança necessárias, incluindo a devida adaptação às normativas internas para o pleno atendimento da legislação vigente no que concerne à Lei Geral de Proteção de Dados (LGPD) – Lei nº 13.709/2018.</p>
        <div class="modal-buttons-docs">
          <button type="button" class="button-blue" onclick="abrirPdf('https://resourceitsolutions.sharepoint.com/:b:/r/sites/ATI-ProjetoCidadoAmigo/Documentos%20Compartilhados/ATI%20-%20Projeto%20Pernambuco%20sem%20Fome/Levantamento%20de%20Requisitos/LGPD_POL%C3%8DTICA%20DE%20PRIVACIDADE.pdf?csf=1&web=1&e=mWMJ1m')">Política de Privacidade</button>
          <button type="button" class="button-blue" onclick="abrirPdf('https://resourceitsolutions.sharepoint.com/:b:/r/sites/ATI-ProjetoCidadoAmigo/Documentos%20Compartilhados/ATI%20-%20Projeto%20Pernambuco%20sem%20Fome/Levantamento%20de%20Requisitos/LGPD_TERMO%20DE%20USO.pdf?csf=1&web=1&e=EcAAT4')">Termo de Uso</button>
        </div>
        <div class="button-group">
          <button type="button" class="button-blue" onclick="mostrarPopupConfirmacao()">Continuar <span class="arrow">&#8594;</span></button>
          <button type="button" class="button-red" onclick="fecharAvisoPrivacidadeModalESair()">Sair</button>
        </div>
      </div>
    </div>

    <div id="confirmacaoModal" class="modal hidden">
      <div class="modal-content">
        <p>Conforme os termos acima li e estou ciente.</p>
        <div class="aceite-termos-popup">
          <input type="checkbox" id="checkboxConfirmacao">
          <label for="checkboxConfirmacao">Li e concordo</label>
        </div>
        <div class="button-group">
          <button type="button" class="button-blue" onclick="prosseguirParaConsulta()">OK</button>
          <button type="button" class="button-red" onclick="voltarParaAvisoPrivacidade()">Cancelar</button>
        </div>
      </div>
    </div>

    <section id="consulta" class="form-section hidden">
      <h2>Consulta</h2>
      <label for="cpf">CPF:</label>
      <input type="text" id="cpf" maxlength="11" placeholder="Digite o CPF (apenas números)" pattern="\d{11}" title="Digite 11 números">

      <label for="nis">NIS:</label>
      <input type="text" id="nis" maxlength="11" placeholder="Digite o NIS (apenas números)" pattern="\d{11}" title="Digite 11 números">

      <button id="getLocationBtnConsulta" class="button-blue" type="button" onclick="getLocation('consulta')" style="margin-top: 15px; margin-bottom:10px;">📍 Usar minha localização</button>

      <label for="municipioConsulta">Município:</label>
      <input list="municipios" id="municipioConsulta" name="municipioConsulta" placeholder="Digite ou selecione um município">
      <div class="button-group">
        <button type="button" class="button-blue" onclick="consultarAPI()">Consultar</button>
        <button type="button" class="button-red" onclick="cancelarConsulta()">Cancelar</button>
      </div>
    </section>

    <div id="mensagem" class="mensagem-section hidden" role="alert"></div>

    <section id="formulario-mim" class="form-section hidden">
      <form id="formMim" onsubmit="event.preventDefault(); salvarFormulario();">
        <fieldset>
          <legend>Fale mais sobre você</legend>

          <label for="nome1" class="required">Nome:</label>
          <input id="nome1" type="text" required>
          <div id="erro-nome1" class="error-message">Campo obrigatório</div>

          <label for="social1">Nome Social:</label>
          <input id="social1" type="text">

          <label for="genero1">Gênero:</label>
          <select id="genero1">
            <option value="">Selecione</option>
            <option>Masculino</option>
            <option>Feminino</option>
            <option>Outro</option>
          </select>

          <label for="nasc1">Data de Nascimento:</label>
          <input type="date" id="nasc1">

          <button type="button" class="button-blue" style="margin-top:15px; margin-bottom:10px;" onclick="getLocation('mim')">📍 Usar minha localização</button>

          <label for="municipio1" class="required">Município:</label>
          <input list="municipios" id="municipio1" name="municipio1" placeholder="Digite ou selecione um município" required>
          <datalist id="municipios">
            <option value="Recife">
            <option value="Olinda">
            <option value="Caruaru">
            <option value="Jaboatão dos Guararapes">
            <option value="Petrolina">
            <option value="Paulista">
            <option value="Cabo de Santo Agostinho">
            <option value="Camaragibe">
            <option value="Garanhuns">
            <option value="Vitória de Santo Antão">
            </datalist>
          <div id="erro-municipio1" class="error-message">Campo obrigatório</div>

          <label for="endereco1">Endereço:</label>
          <input type="text" id="endereco1">

          <label class="required">Situação de Rua?</label>
          <div class="radio-group">
            <label><input type="radio" name="situacaoRua" value="sim"> Sim</label>
            <label><input type="radio"name="situacaoRua" value="nao"> Não</label>
          </div>
          <div id="erro-situacaoRua" class="error-message">Campo obrigatório</div>

          <label class="required">Você é brasileiro(a)?</label>
          <div class="radio-group">
            <label><input type="radio" name="brasileiroMim" value="sim"> Sim</label>
            <label><input type="radio" name="brasileiroMim" value="nao"> Não</label>
          </div>
           <div id="erro-brasileiroMim" class="error-message">Campo obrigatório</div>
        </fieldset>

        <div class="button-group">
          <button type="submit" class="button-blue">Salvar</button>
          <button type="button" class="button-red" onclick="cancelarFormulario()">Cancelar</button>
        </div>
      </form>
    </section>

    <section id="formulario-alguem" class="form-section hidden">
      <form id="formAlguem" onsubmit="event.preventDefault(); salvarFormulario();">
        <fieldset>
          <legend class="required">Você está ajudando como:</legend>
          <div class="radio-group">
            <label><input type="radio" name="tipoPerfil" value="cidadao_amigo"> Cidadão Amigo</label>
            <label><input type="radio" name="tipoPerfil" value="profissional"> Profissional</label>
          </div>
           <div id="erro-tipoPerfil" class="error-message">Campo obrigatório</div>
        </fieldset>

        <fieldset>
          <legend>Fale mais sobre quem você está ajudando</legend>

          <label for="nome2" class="required">Nome completo de quem você está ajudando:</label>
          <input id="nome2" type="text" required>
          <div id="erro-nome2" class="error-message">Campo obrigatório</div>

          <label for="social2">Nome Social de quem você está ajudando:</label>
          <input id="social2" type="text">

          <label for="genero2">Gênero de quem você está ajudando:</label>
          <select id="genero2">
            <option value="">Selecione</option>
            <option>Masculino</option>
            <option>Feminino</option>
            <option>Outro</option>
          </select>

          <label for="nasc2">Data de Nascimento de quem você está ajudando:</label>
          <input type="date" id="nasc2">

          <button type="button" class="button-blue" style="margin-top:15px; margin-bottom:10px;" onclick="getLocation('alguem')">📍 Usar minha localização</button>

          <label for="municipio2" class="required">Município de quem você está ajudando:</label>
          <input list="municipios" id="municipio2" name="municipio2" placeholder="Digite ou selecione um município" required>
          <div id="erro-municipio2" class="error-message">Campo obrigatório</div>

          <label for="endereco2">Endereço de quem você está ajudando:</label>
          <input type="text" id="endereco2">

          <label class="required">Situação de Rua?</label>
          <div class="radio-group">
            <label><input type="radio" name="situacaoRua2" value="sim"> Sim</label>
            <label><input type="radio" name="situacaoRua2" value="nao"> Não</label>
          </div>
          <div id="erro-situacaoRua2" class="error-message">Campo obrigatório</div>

          <label class="required">A pessoa que você está ajudando é brasileira?</label>
          <div class="radio-group">
            <label><input type="radio" name="brasileiroAlguem" value="sim"> Sim</label>
            <label><input type="radio" name="brasileiroAlguem" value="nao"> Não</label>
          </div>
          <div id="erro-brasileiroAlguem" class="error-message">Campo obrigatório</div>
        </fieldset>

        <div class="button-group">
          <button type="submit" class="button-blue">Salvar</button>
          <button type="button" class="button-red" onclick="cancelarFormulario()">Cancelar</button>
        </div>
      </form>
    </section>
  </main>

  <script>
    let perfilSelecionado = '';
    let currentForm = null;

    const avisoPrivacidadeModal = document.getElementById('avisoPrivacidadeModal');
    const confirmacaoModal = document.getElementById('confirmacaoModal');
    const consultaSection = document.getElementById('consulta');
    const mensagemDiv = document.getElementById('mensagem');
    const formMim = document.getElementById('formulario-mim');
    const formAlguem = document.getElementById('formulario-alguem');
    const checkboxConfirmacao = document.getElementById('checkboxConfirmacao');


    function selecionarOpcao(opcao) {
      perfilSelecionado = opcao;
      consultaSection.classList.add('hidden');
      mensagemDiv.classList.add('hidden');
      formMim.classList.add('hidden');
      formAlguem.classList.add('hidden');
      confirmacaoModal.classList.add('hidden');
      avisoPrivacidadeModal.classList.remove('hidden');
    }

    function abrirPdf(url) {
      // Certifique-se de que os arquivos PDF estejam no mesmo diretório do arquivo HTML,
      // ou forneça o caminho completo para eles.
      window.open(url, '_blank');
    }

    function fecharAvisoPrivacidadeModalESair() {
      cancelarFormulario();
    }

    function mostrarPopupConfirmacao() {
      avisoPrivacidadeModal.classList.add('hidden');
      checkboxConfirmacao.checked = false;
      confirmacaoModal.classList.remove('hidden');
    }

    function voltarParaAvisoPrivacidade() {
        confirmacaoModal.classList.add('hidden');
        avisoPrivacidadeModal.classList.remove('hidden');
    }

    function prosseguirParaConsulta() {
      if (checkboxConfirmacao.checked) {
        confirmacaoModal.classList.add('hidden');
        consultaSection.classList.remove('hidden');
        document.getElementById('cpf').value = '';
        document.getElementById('nis').value = '';
        document.getElementById('municipioConsulta').value = '';
        console.log('Usuário aceitou os termos e prosseguiu para consulta.');
      } else {
        alert("Você precisa marcar 'Li e concordo' para continuar.");
      }
    }

    function cancelarConsulta() {
      consultaSection.classList.add('hidden');
      // Para voltar à tela inicial de seleção de perfil:
      // cancelarFormulario();
    }
    
    function getLocation(formType) {
      alert("Simulação: Localização obtida! O campo de município será preenchido com 'Recife'.");
      let municipioField;
      if (formType === 'mim') {
          municipioField = document.getElementById('municipio1');
      } else if (formType === 'alguem') {
          municipioField = document.getElementById('municipio2');
      } else if (formType === 'consulta') {
          municipioField = document.getElementById('municipioConsulta');
      }
      if (municipioField) {
          municipioField.value = "Recife";
      }
    }

    function consultarAPI() {
      const cpf = document.getElementById('cpf').value.trim();
      const nis = document.getElementById('nis').value.trim();
      
      esconderFormularios();
      mensagemDiv.classList.add('hidden');

      if ((cpf && (cpf.length !== 11 || !/^\d{11}$/.test(cpf))) || (nis && (nis.length !== 11 || !/^\d{11}$/.test(nis)))) {
        mensagemDiv.innerHTML = '<p style="color:red;">CPF ou NIS inválido. Deve conter 11 números.</p>';
        mensagemDiv.classList.remove('hidden');
        return;
      }
      
      if (cpf || nis) {
        mensagemDiv.innerHTML = `
          <p><strong>Vá também ao CRAS* mais próximo para realizar o seu acompanhamento na rede de Assistência Social.</strong></p>
          <p>📍 CRAS - BONGI<br>Av. Gen San Martin, nº 1083 – Jiquiá<br>Fone: 3225.9440/9446<br>E-mail: crasbongi@gmail.com<br>(Compaz Escritor Ariano Suassuna - Cordeiro)</p>
          <p><strong>Essas são as cozinhas comunitárias** mais próximas à sua localização.</strong></p>
          <p>📍 Cozinha Comunitária: Gurupé<br>Telefone: (81) 99362-9916<br>Profissional Responsável: Nivea Gouveia<br>Endereço: Rua Gurupé nº 253, Afogados, Recife - PE, CEP: 50.830-170</p>
          <p><small>* CRAS é a principal porta de entrada para a proteção social básica.</small></p>
          <p><small>** Cozinhas Comunitárias são espaços públicos onde são preparadas e oferecidas refeições saudáveis, de graça ou a baixo custo.</small></p>
        `;
        mensagemDiv.classList.remove('hidden');
      } else {
        if (perfilSelecionado === 'mim') {
          formMim.classList.remove('hidden');
          currentForm = 'formMim';
        } else if (perfilSelecionado === 'alguem') {
          formAlguem.classList.remove('hidden');
          currentForm = 'formAlguem';
        } else {
            alert("Por favor, selecione uma opção inicial ('Para mim' ou 'Ajudar alguém').");
            cancelarFormulario();
        }
      }
    }

    function esconderFormularios() {
      formMim.classList.add('hidden');
      formAlguem.classList.add('hidden');
      currentForm = null;
    }

    function validarCampo(campoId, erroId, isRadio = false, radioName = '') {
      const campoElement = document.getElementById(campoId); // Pode ser null para radios
      const erroElement = document.getElementById(erroId);
      let valorValido = false;

      if (isRadio) {
        const radioChecked = document.querySelector(`input[name="${radioName}"]:checked`);
        if (radioChecked) {
            valorValido = true;
        }
      } else {
        if (campoElement.value.trim() !== '') {
            valorValido = true;
        }
      }

      if (!valorValido) {
        if (!isRadio && campoElement) campoElement.classList.add('input-error');
        erroElement.style.display = 'block';
        erroElement.textContent = "Este campo é obrigatório.";
        return false;
      } else {
        if (!isRadio && campoElement) campoElement.classList.remove('input-error');
        erroElement.style.display = 'none';
        return true;
      }
    }

    function salvarFormulario() {
      let formValido = true;
      let situacaoRuaValue = null;

      if (perfilSelecionado === 'mim') {
        // A ordem da validação importa para o '&&'
        formValido = validarCampo('nome1', 'erro-nome1') && formValido;
        formValido = validarCampo('municipio1', 'erro-municipio1') && formValido;
        formValido = validarCampo(null, 'erro-situacaoRua', true, 'situacaoRua') && formValido;
        formValido = validarCampo(null, 'erro-brasileiroMim', true, 'brasileiroMim') && formValido;
        
        if (document.querySelector('input[name="situacaoRua"]:checked')) {
            situacaoRuaValue = document.querySelector('input[name="situacaoRua"]:checked').value;
        }

      } else if (perfilSelecionado === 'alguem') {
        formValido = validarCampo(null, 'erro-tipoPerfil', true, 'tipoPerfil') && formValido;
        formValido = validarCampo('nome2', 'erro-nome2') && formValido;
        formValido = validarCampo('municipio2', 'erro-municipio2') && formValido;
        formValido = validarCampo(null, 'erro-situacaoRua2', true, 'situacaoRua2') && formValido;
        formValido = validarCampo(null, 'erro-brasileiroAlguem', true, 'brasileiroAlguem') && formValido;

        if (document.querySelector('input[name="situacaoRua2"]:checked')) {
            situacaoRuaValue = document.querySelector('input[name="situacaoRua2"]:checked').value;
        }
      }

      if (!formValido) {
          alert("Por favor, preencha todos os campos obrigatórios.");
          return;
      }

      let texto = '';
      if (situacaoRuaValue === 'sim') {
        texto = `
          <strong>Essas são as cozinhas comunitárias* mais próximas à sua localização.</strong><br><br>
          📍 Cozinha Comunitária: Gurupé<br>Telefone: (81) 99362-9916<br>Profissional Responsável: Nivea Gouveia<br>Endereço: Rua Gurupé nº 253, Afogados, Recife - PE, CEP: 50.830-170<br><br>
          Para lhe incluir na rede de Assistência Social vá também ao CREAS** mais próximo para realizar o seu acompanhamento.<br><br>
          📍 CREAS AFOGADOS<br>
          End.: Rua 21 de Abril, nº 1092 - Afogados<br>
          Fone: 3355.3671 / 3355.3673<br>
          E-mail: creasafogados@recife.pe.gov.br<br>
          Horário de Funcionamento: 2ª a 6ª feira, das 8h às 17h <br><br>
          <small>* Cozinhas Comunitárias são espaços públicos onde são preparadas e oferecidas refeições saudáveis...</small><br>
          <small>** CREAS é uma unidade pública responsável por ofertar serviços especializados...</small>
        `;
      } else if (situacaoRuaValue === 'nao') {
        texto = `
          <strong>Essas são as cozinhas comunitárias* mais próximas à sua localização.</strong><br><br>
          📍 Cozinha Comunitária mais próxima: Cozinha Comunitária: Gurupé<br>Telefone: (81) 99362-9916<br>Profissional Responsável: Nivea Gouveia<br>Endereço: Rua Gurupé nº 253, Afogados, Recife - PE, CEP: 50.830-170<br><br>
          Para lhe incluir na rede de Assistência Social vá também ao CRAS** mais próximo para realizar o seu acompanhamento.<br><br>
          📍 CRAS mais próximo: CRAS - BONGI<br>Av. Gen San Martin, nº 1083 – Jiquiá<br>Fone: 3225.9440/9446<br>E-mail: crasbongi@gmail.com<br>(Compaz Escritor Ariano Suassuna - Cordeiro)<br><br>
          <small>* Cozinhas Comunitárias são espaços públicas onde são preparadas e oferecidas refeições saudáveis.</small><br>
          <small>** CRAS é uma unidade pública no seu município que atua como a principal porta de entrada...</small>
        `;
      }

      mensagemDiv.innerHTML = texto;
      mensagemDiv.classList.remove('hidden');
      esconderFormularios();
    }

    function cancelarFormulario() {
      esconderFormularios();
      mensagemDiv.classList.add('hidden');
      consultaSection.classList.add('hidden');
      avisoPrivacidadeModal.classList.add('hidden');
      confirmacaoModal.classList.add('hidden');
      perfilSelecionado = '';
      // Limpar campos dos formulários se necessário
      // Ex: document.getElementById('formMim').reset(); document.getElementById('formAlguem').reset();
    }
  </script>
</body>
</html>
