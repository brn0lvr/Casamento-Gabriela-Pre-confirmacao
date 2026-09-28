# Pré-confirmação | Gabriela & Mateus

Site estático independente para pré-confirmação de presença. Os arquivos `convidados.js`, `styles.css`, `Images/` e `Fonts/` foram copiados do projeto original para que a lista de famílias, recursos visuais e identidade permaneçam iguais sem dependência de caminhos externos ao repositório.

## Publicar no GitHub Pages

1. Crie um repositório separado no GitHub e envie o conteúdo desta pasta para a raiz dele.
2. Em **Settings > Pages**, selecione **Deploy from a branch**, a branch principal e a pasta `/ (root)`.
3. Aguarde a publicação e acesse a URL do GitHub Pages.

## Configurar o recebimento

O frontend envia `action=preconfirmation` a uma implantação própria do Apps Script. O arquivo `apps-script-rsvp.gs` desta pasta preserva as rotas existentes e acrescenta a gravação na guia `Pré-confirmações`, com os mesmos cabeçalhos da aba `Confirmacoes`.

Para ativar o recebimento, atualize o código no projeto Google Apps Script vinculado à planilha existente usando esta versão e crie uma **nova implantação** como aplicativo da web, executando como o proprietário e permitindo acesso conforme a configuração atual. Copie a URL dessa nova implantação para `appsScriptUrl` em `pre-confirmacao.js`. Não altere nem substitua a implantação já usada pelo site original: a nova implantação compartilha a planilha vinculada, enquanto o endpoint original continua atendendo às confirmações definitivas como antes. Somente pedidos com `action=preconfirmation` são direcionados à nova guia. O primeiro envio cria a aba e seus cabeçalhos automaticamente. Também é possível chamar `?action=setup` na nova implantação para preparar as abas.

Até configurar essa URL, o formulário não envia respostas e informa que a integração ainda não está configurada. Não é necessário colocar credenciais no frontend. A URL pública da implantação identifica o endpoint, mas não concede acesso direto à planilha.

## Dados registrados

`familyId`, `familyName`, `confirmedMembers`, `absentMembers`, `totalConfirmed`, `phone`, `alcoholCount`, `dietaryRestriction`, `notes`, `confirmedAt` e `updatedAt`. O registro é atualizado por família, como no fluxo existente.

> A nova implantação usa o projeto Apps Script vinculado à planilha; mantenha a implantação existente e publique a nova URL apenas no site de pré-confirmação. As alterações do site podem ser publicadas separadamente neste repositório.