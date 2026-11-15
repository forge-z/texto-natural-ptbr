# texto-natural-ptbr

Skill para editar, reescrever ou auditar textos em português brasileiro sem
apagar a voz do autor.

A edição começa pela entrega e respeita o pedido de tom, extensão e formato.
Os exemplos mostram como reduzir excessos sem inventar fatos, apagar ressalvas
ou transformar informação limitada em certeza.

Versão atual da skill: **1.7.0** (campo `version` em [`SKILL.md`](SKILL.md)).

## Estrutura do repositório

| Caminho | Função |
| --- | --- |
| [`SKILL.md`](SKILL.md) | Instruções do agente (fluxo, modos, critérios) |
| [`references/padroes-ptbr.md`](references/padroes-ptbr.md) | Padrões de escrita artificial em pt-BR (leitura obrigatória antes de editar) |
| [`references/avaliacao.md`](references/avaliacao.md) | Checklist e regressões por modo |
| [`references/exemplos.md`](references/exemplos.md) | Entradas e saídas de calibração |
| [`references/livros/`](references/livros/) | Fichas do Domínio Público (consulta opcional; ver [`README`](references/livros/README.md)) |
| [`SOURCES.md`](SOURCES.md) | Atribuição e URLs das fontes |

## O que faz

- Remove linguagem genérica, inflada, promocional ou mecânica.
- Preserva fatos, intenção, público, registro, regionalismos e humor.
- Detecta padrões sem alegar que um texto foi escrito por IA.
- Calibra a edição a partir de uma amostra da voz do autor.
- Preserva frontmatter, código, dados, links e sintaxe estrutural em arquivos.

## Como usar

Peça a ação e cole o texto, ou indique o arquivo:

```text
Edite este email para ficar mais direto, mantendo o tom informal:
[texto]
```

```text
Detecte os padrões de escrita artificial neste artigo, sem reescrevê-lo:
[texto]
```

```text
Edite `docs/guia.md`, preserve o Markdown e não altere código nem links.
```

O modo padrão é `editar`. Os modos disponíveis são:

| Modo | Entrega |
| --- | --- |
| `editar` | Texto final com a menor intervenção possível; `O que mudou` quando houver alterações e o formato permitir |
| `reescrever` | Estrutura e frases refeitas conforme o pedido; mesmos limites de fidelidade |
| `detectar` | Padrão, trecho exato e correção sugerida |
| `calibrar voz` | Edição guiada por uma amostra do autor |
| `arquivo` | Edição gravada quando pedida; auditoria apenas lê e relata |
| `embutido` | Segue o contrato da tarefa principal; na edição, apenas o texto final |

## Critérios de edição

As referências em [`references/`](references/) fazem parte do trabalho:

- [`padroes-ptbr.md`](references/padroes-ptbr.md) lista 41 padrões com
  exemplos de antes e depois, as ressalvas para não marcar falso positivo e
  os sinais de voz que devem sobreviver. Leitura obrigatória antes de editar.
- [`avaliacao.md`](references/avaliacao.md) valida fidelidade, voz, clareza,
  escopo e entrega conforme o modo. Inclui vinte e quatro casos de regressão para revisar
  a skill. Confira os critérios aplicáveis antes de entregar.
- [`exemplos.md`](references/exemplos.md) traz entradas e saídas completas
  nos modos editar, reescrever e detectar. Consulta opcional.
- [`livros/`](references/livros/) reúne seis obras clássicas com regras adaptadas
  à prosa atual (gênero, fechamento, unidade, descrição). Consulta opcional após
  `padroes-ptbr.md`.

A regra principal é simples: especificidade deve vir do original ou do
contexto fornecido pelo usuário. Se faltar um detalhe, preserve uma versão
simples ou sinalize a lacuna; nunca invente fatos. Amostras de voz orientam
estilo, sem transferir experiências ou informações para o texto editado.

Sem pedido explícito, a skill preserva citações de terceiros, código, dados,
links, termos técnicos, voz e quantidade de informação. Pedidos como “mais
formal”, “resuma” e “só o texto” prevalecem sobre esses padrões de edição.
Revisão de estilo não confirma a veracidade do texto nem determina autoria.

Em respostas numa conversa, a skill retira recapitulações apenas quando o
contexto compartilhado está disponível. Fatos novos, razões decisivas e
explicações pedidas permanecem. Também distingue moral redundante após um
exemplo, título de efeito e narração da montagem do documento de informações
que ajudam o leitor a interpretar ou agir. Quando a fonte só emoldura um fato
já dito (“o perfil o identifica como”), declara o fato e mantém a atribuição,
sem completar cargo ou dado que a frase não trouxe. Comentário e roteiro
deixados para o autor saem, sem serem executados.

## Instalação

Clone o repositório dentro do diretório de skills do seu agente. O nome da
pasta precisa ser `texto-natural-ptbr`, igual ao campo `name` do
[`SKILL.md`](SKILL.md).

```bash
# Codex e outros agentes que leem .agents/skills
git clone https://github.com/forge-z/texto-natural-ptbr.git \
  .agents/skills/texto-natural-ptbr

# Claude Code
git clone https://github.com/forge-z/texto-natural-ptbr.git \
  ~/.claude/skills/texto-natural-ptbr

# Cursor
git clone https://github.com/forge-z/texto-natural-ptbr.git \
  .cursor/skills/texto-natural-ptbr
```

Para atualizar, rode `git pull` dentro da pasta. Não há dependências de
runtime.

## Licença e fontes

Distribuída sob MIT. As fontes e atribuições estão em
[`SOURCES.md`](SOURCES.md).

### Livros do Domínio Público

Seis fichas em [`references/livros/`](references/livros/), com citações conferidas nos PDFs do Wayback e exemplos Antes/Depois em pt-BR atual:

- [Ao correr da pena](references/livros/alencar-ao-correr-da-pena.md) (José de Alencar)
- [Camões](references/livros/nabuco-camoes.md) (Joaquim Nabuco)
- [Críticas teatrais](references/livros/machado-criticas-teatrais.md) (Machado de Assis)
- [Sermão da Sexagésima](references/livros/vieira-sermao-da-sexagesima.md) (Padre António Vieira; oratória barroca só como contexto)
- [Páginas críticas e comemorativas](references/livros/machado-paginas-criticas-e-comemorativas.md) (Machado de Assis)
- [Arte Poética](references/livros/aristoteles-arte-poetica.md) (Aristóteles; adaptação à prosa, não prescrição literária)

URLs e atribuição em [`SOURCES.md`](SOURCES.md).

### Referências do lote B2 — livros do Domínio Público (agy)

Fichas adicionais em [`references/livros/`](references/livros/), baseadas em autores brasileiros com obras disponíveis no Domínio Público, com citações verificadas nos textos originais e exemplos Antes/Depois para prosa em pt-BR contemporânea:

- [Como e por que sou romancista](references/livros/alencar-como-e-por-que-sou-romancista.md) (José de Alencar; urdidura factual, corte de digressão, recusa a moldes pré-fabricados, poda da exuberância, laconismo do fato e revisão rigorosa).
- [História da literatura brasileira: Fatores da literatura brasileira](references/livros/romero-historia-da-literatura-brasileira-fatores.md) (Sílvio Romero; legitimidade orgânica do português brasileiro, desuso de tempos verbais arcaicos, precisão lexical concreta, recusa a pastiches e ao copismo estrangeiro servil).

