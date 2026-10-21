# Perito em Computação Forense (skill)

Skill para o Claude Code (e Claude) que atua como perito em computação forense e engenharia de software. Ela ajuda a elaborar laudos, pareceres técnicos, quesitos, respostas a quesitos, esclarecimentos e análises críticas de laudos adversos.

O texto produzido é minuta de apoio. O perito que assina responde pelo conteúdo, por isso a skill lembra de conferir fatos, números e fundamentos antes da assinatura.

## Quando é acionada

A skill é usada em pedidos que envolvam:

- perícia digital e evidência eletrônica;
- cadeia de custódia;
- autenticidade de mensagens (WhatsApp, e-mail, redes sociais);
- análise de dispositivos, software e código-fonte;
- fraudes eletrônicas;
- assinaturas digitais;
- logs e trilhas de auditoria.

## Papéis que a skill assume

1. **Perito judicial**, nomeado pelo juízo, com dever de imparcialidade e de auxílio à justiça.
2. **Assistente técnico**, indicado por uma das partes, com liberdade para sustentar a tese técnica que os fatos comportam, sem criar fatos.
3. **Perícia extrajudicial ou privada**, com relatórios, auditorias e pareceres que podem servir como prova pré-constituída.

Antes de começar, a skill identifica em qual papel o pedido se enquadra. A postura e o tom mudam conforme o papel.

## Princípios

- A conclusão decorre da evidência, nunca o contrário.
- Nenhum dado é inventado. Informações ausentes ficam marcadas como `[PREENCHER: descrição]`.
- Fato, método e inferência aparecem separados no texto.
- Todo achado deve ser reproduzível (ferramenta, versão, parâmetros e hash registrados).
- Limites da análise são declarados.

## Fluxo de trabalho

1. **Triagem:** papel, processo, objeto da perícia, quesitos, evidências recebidas, diligências já feitas e ponto controvertido.
2. **Plano de análise:** método específico para dispositivos, mensagens e redes sociais, software e código-fonte, ou fraudes e assinaturas digitais.
3. **Cadeia de custódia:** origem, recebimento, manuseio, armazenamento, hashes e quebras registradas.
4. **Redação:** estrutura do art. 473 do CPC, com introdução, objeto, metodologia, análise técnica, resposta aos quesitos, conclusão e anexos.
5. **Checklist final** antes da entrega.

## Referências citadas

A skill cita normas e leis relevantes, como o CPC (arts. 156 a 158, 369, 370, 384, 422, 439 a 441, 464 a 480), o CPP (arts. 158-A a 158-F, sobre cadeia de custódia), o Marco Civil da Internet, a LGPD, a ICP-Brasil, a Lei 14.063/2020, as Leis 12.737/2012 e 14.155/2021, a Resolução CNJ 233/2016, as normas ABNT NBR ISO/IEC 27037, 27041, 27042 e 27043, a ISO/IEC 27050, e guias do NIST.

A skill manda verificar a vigência e a redação atual antes de qualquer citação, porque normas e leis podem mudar.

## Instalação

Copie o arquivo `SKILL.md` para a pasta de skills do Claude:

```bash
mkdir -p ~/.claude/skills/perito-computacao-forense
cp SKILL.md ~/.claude/skills/perito-computacao-forense/
```

No Windows (Git Bash), o caminho equivalente é `~/.claude/skills/perito-computacao-forense/`, dentro da pasta do seu usuário.

## Uso

Basta descrever o pedido em linguagem natural, por exemplo:

> Preciso responder aos quesitos do juízo sobre a autenticidade de conversas de WhatsApp apresentadas pela parte autora.

A skill faz perguntas objetivas quando faltam informações essenciais e não preenche lacunas com suposições.

## Limitações

- Não substitui a formação, a assinatura nem a responsabilidade técnica do perito.
- Não dá aconselhamento jurídico. Questões de mérito cabem ao juízo.
- Não verifica a vigência das normas por conta própria. Confira antes de citar.

## Autor

Fabio Cranchi
