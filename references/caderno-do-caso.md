# Caderno do caso

O caderno do caso é a memória do trabalho: um conjunto de notas Markdown, compatível com o Obsidian (links `[[...]]`), que guarda o que foi coletado, de onde veio cada fato, o que falta e as decisões tomadas. Ele vale mais que a memória da conversa e que qualquer resumo no `CLAUDE.md`. Quando os dois divergirem, prevalece o caderno.

Este protocolo é comum às skills `advogado-geral` e `perito-computacao-forense`. As duas usam **o mesmo caderno**, na mesma pasta. Nunca crie um segundo caderno para o mesmo caso.

## 1. Ao iniciar a skill: verificar se o caderno existe

1. Considere como **pasta do caso** o diretório de trabalho do projeto (onde está ou estaria o `CLAUDE.md`).
2. Procure a pasta `Caderno do caso/` com o arquivo `00 Índice.md`. Aceite variações de grafia (`caderno do caso`, `Caderno do Caso`, `00 Indice.md`) e não crie outra se encontrar uma delas.
3. Se o caderno **existir**, siga a seção 3.
4. Se **não existir**, siga a seção 2.

Exceção: se o diretório de trabalho não for a pasta de um caso (a pasta do usuário, a raiz de um disco, uma pasta de modelos, um repositório de software) ou se o pedido for uma consulta conceitual sem caso concreto, não crie nada. Pergunte ao usuário, em uma linha, se quer abrir um caderno e em qual pasta.

## 2. Se o caderno não existe: criar e registrar no CLAUDE.md

### 2.1 Criar a estrutura

```
Caderno do caso/
  00 Índice.md
  Fatos.md
  Pendências.md
  Linha do tempo.md
  Pessoas e papéis.md
  Documentos.md
  Objetivo e método.md
  Reuniões/
```

Conteúdo inicial de cada nota:

- **`00 Índice.md`**: título com o nome do caso; uma ou duas linhas com o processo (número, órgão ou juízo), o objeto da disputa e o papel do usuário (advogado de quem, perito judicial, assistente técnico de quem); a linha `Última atualização: DD/MM/AAAA`; a tabela **Mapa** com um link e uma linha de descrição para cada nota; e a seção **Convenções** (copie a seção 4 deste arquivo, adaptada ao caso).
- **`Fatos.md`**: registro numerado (`F-001`, `F-002`...), agrupado por tema (processo, partes, contratos, documentos, operação, valores). Formato de cada fato:

  ```
  **F-001** · Enunciado do fato, curto e verificável.
  Fonte: Documento · `arquivo.pdf`, p. 3, cláusula 2ª · confirmado
  ```

- **`Pendências.md`**: listas de tarefas `- [ ] **P-01** ...`, separadas em *Documentos* (o que pedir e a quem) e *Esclarecimentos e decisões*. Cada pendência indica quem deve resolver.
- **`Linha do tempo.md`**: tabela `| Data | Evento | Ref. |`, com o fato de origem na coluna Ref. Separe os fatos do caso do andamento do próprio trabalho (contratação, reuniões, prazos de entrega).
- **`Pessoas e papéis.md`**: tabelas por grupo (cliente, escritório, parte contrária, juízo ou órgão, terceiros) com papel, contato e o que cada pessoa sabe ou pode fornecer.
- **`Documentos.md`**: inventário dos documentos recebidos e dos que faltam (arquivo, o que é, quem forneceu, data, hash quando houver), mais a tabela dos objetos em disputa (contratos, notas, mensagens, dispositivos) quando o caso tiver. Se o caso pedir um nome mais preciso (por exemplo, `Contratos e notas.md`), use-o e ajuste o Mapa.
- **`Objetivo e método.md`**: o objetivo do trabalho (redação aprovada, quando houver), o papel e a postura, os critérios de análise ou de classificação, as teses em estudo e cada decisão de método com a data e quem decidiu.
- **`Reuniões/`**: uma nota por reunião, nomeada `AAAA-MM-DD Título.md`, com participantes, pauta, o que foi dito (quem disse), decisões, fatos gerados (`F-xxx`) e pendências geradas (`P-xx`).

### 2.2 Popular com o que já existe

Leia os arquivos da pasta do caso (PDFs, transcrições, e-mails, contratos) e registre os fatos que eles sustentam, cada um com a fonte precisa. Transcrições de reunião viram notas em `Reuniões/`. O que faltar vira pendência. Não invente nem complete lacunas por suposição: o que não estiver em fonte fica em `Pendências.md` ou com a situação `a confirmar`.

Se a pasta tiver muitos documentos, registre primeiro o inventário em `Documentos.md` e os fatos centrais (partes, processo, objeto, prazos, valores) e diga ao usuário o que ainda não foi lido.

### 2.3 Criar ou atualizar o CLAUDE.md

Para que as próximas sessões, com ou sem a skill, continuem o registro, o `CLAUDE.md` da pasta do caso precisa da instrução abaixo.

- Se o `CLAUDE.md` **não existir**, crie-o com um título, uma seção curta sobre o caso (o que é a pasta, as partes, o papel do usuário, os arquivos principais) e o bloco abaixo.
- Se **existir** e não tiver seção sobre o caderno, acrescente o bloco sem alterar o resto.
- Se já tiver a seção, não a duplique. Apenas corrija o que estiver desatualizado (nomes de notas, por exemplo).
- Escreva o bloco no mesmo idioma do restante do `CLAUDE.md`. O modelo abaixo está em português.

```markdown
## Caderno do caso (ler primeiro, atualizar sempre)

`Caderno do caso/` é a memória do caso: notas Markdown compatíveis com o Obsidian (links `[[...]]`). É a fonte de verdade sobre o que foi coletado e prevalece sobre o resumo deste arquivo quando os dois divergirem.

- **No início de toda sessão**, leia `Caderno do caso/00 Índice.md`, `Fatos.md` e `Pendências.md` antes de responder sobre o caso.
- **Durante e ao final de toda sessão**, registre o que foi aprendido:
  - Fatos novos entram em `Fatos.md` como o próximo `F-NNN`, com o tipo de fonte (**Documento**, **Declaração** ou **Exame**), a referência precisa (arquivo e página ou cláusula; quem disse e quando; ou o registro da diligência e o hash) e a situação (`confirmado`, `a confirmar`, `contraditado (ver F-xxx)`). Fato conhecido só pelo resumo de outra pessoa é marcado "Documento (via ...)".
  - Nunca apague um fato. Marque-o como contraditado e registre o novo.
  - Atualize `Pendências.md` (P-NN, marcando as resolvidas com a data), `Linha do tempo.md`, `Documentos.md` e `Pessoas e papéis.md` quando forem afetados.
  - Cada reunião ganha uma nota em `Reuniões/` com o nome `AAAA-MM-DD Título.md`.
  - Decisões de método e de estratégia vão para `Objetivo e método.md`.
  - Atualize a data de "Última atualização" em `00 Índice.md`.
- Laudos, pareceres e peças citam fatos do caderno, nunca só da memória.
```

Ao terminar, informe ao usuário, em duas ou três linhas, que o caderno foi criado, quantos fatos e pendências foram registrados e que o `CLAUDE.md` foi criado ou atualizado.

## 3. Se o caderno existe: ler e atualizar a cada interação

### 3.1 Ler antes de responder

No início da sessão (ou na primeira vez que a skill for acionada nela), leia `00 Índice.md`, `Fatos.md` e `Pendências.md`. Leia as demais notas quando o pedido tocar nelas (`Objetivo e método.md` antes de redigir; a nota da reunião antes de tratar do que foi dito nela). Se o caderno contradisser o que você lembra ou o que está no `CLAUDE.md`, siga o caderno e aponte a divergência.

Confira também se o `CLAUDE.md` tem a seção do caderno. Se não tiver, acrescente-a (seção 2.3).

### 3.2 Atualizar a cada interação

Ao fim de cada interação em que algo novo surgir, atualize o caderno **antes de encerrar a resposta**. Não deixe para o fim da sessão, que pode não acontecer. Gera registro:

| O que surgiu | Onde registrar |
|---|---|
| Fato novo, de documento lido, de declaração ou de exame | `Fatos.md`, próximo `F-NNN` |
| Fato que corrige outro | Novo `F-NNN`; o antigo recebe `contraditado (ver F-NNN)` |
| Documento pedido, dúvida, contradição a esclarecer | `Pendências.md`, próximo `P-NN` |
| Pendência resolvida | `[x]`, data e o fato gerado |
| Data relevante (do caso ou do trabalho) | `Linha do tempo.md` |
| Documento recebido ou analisado | `Documentos.md` |
| Pessoa nova, papel ou contato | `Pessoas e papéis.md` |
| Reunião, ligação, transcrição | Nota em `Reuniões/` e link no Mapa do índice |
| Decisão de método, critério, tese, redação de objetivo | `Objetivo e método.md`, com data e quem decidiu |
| Entrega produzida (laudo, parecer, peça, proposta) | `Linha do tempo.md` e `Documentos.md`, com o nome do arquivo |

Depois de qualquer alteração, atualize `Última atualização` em `00 Índice.md`. Se uma nota nova for criada, inclua-a no Mapa.

Interações que não trazem nada novo (uma pergunta conceitual, uma revisão de estilo) não exigem registro. Na dúvida, registre.

Ao final da resposta, diga em uma linha o que foi registrado (por exemplo: "Caderno: F-031 a F-034, P-19 resolvida, nota da reunião de 03/11").

## 4. Convenções

- **Fonte de cada fato** (obrigatória), uma de três:
  - **Documento**: contrato, nota fiscal, auto, petição, decisão, e-mail etc. Indicar arquivo e página ou cláusula.
  - **Declaração**: dito pelo cliente, pela parte, pelo escritório ou por terceiro. Indicar quem, quando e onde (reunião, e-mail, ligação).
  - **Exame**: verificado diretamente pelo perito ou assistente técnico. Indicar o registro da diligência e o hash.
- **Fonte secundária**: documento conhecido só pela descrição de outra pessoa é marcado "Documento (via Fulano)" até a leitura do original.
- **Situação**: `confirmado`, `a confirmar`, `contraditado (ver F-xxx)`.
- Fatos não se apagam. Fato errado é marcado como contraditado e o fato correto entra com novo número.
- IDs sequenciais e nunca reaproveitados: `F-001` para fatos, `P-01` para pendências.
- Datas no formato DD/MM/AAAA no texto e AAAA-MM-DD no nome das notas de reunião.
- Valores com a fonte do cálculo. Não arredonde nem some sem dizer como.
- Separe sempre o que é fato, o que é declaração de parte e o que é opinião técnica ou tese jurídica.
- Não use travessão nem meia-risca em texto que vá para a peça ou para o laudo.

## 5. Ajustes por skill

- **`perito-computacao-forense`**: os fatos de **Exame** citam o registro da diligência (planilha ou ata), a ferramenta e versão, e o hash do material examinado. `Objetivo e método.md` guarda os quesitos, o objetivo do laudo ou parecer, os critérios técnicos e a metodologia. A cadeia de custódia de cada evidência fica em `Documentos.md` ou em nota própria (`Cadeia de custódia.md`), ligada ao índice.
- **`advogado-geral`**: `Objetivo e método.md` guarda as teses, os pedidos, a estratégia e os riscos. Prazos processuais entram em `Linha do tempo.md` e, se ainda correm, também em `Pendências.md`, com a data-limite em destaque. Precedentes e dispositivos legais confirmados podem ganhar a nota `Fontes jurídicas.md`, com o link oficial de cada um; precedente não confirmado não entra no caderno como fato.
