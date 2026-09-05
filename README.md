# texto-natural-ptbr

Skill para editar, reescrever ou auditar textos em português brasileiro sem
apagar a voz do autor.

A edição começa pela entrega e respeita o pedido de tom, extensão e formato.
Os exemplos mostram como reduzir excessos sem inventar fatos, apagar ressalvas
ou transformar informação limitada em certeza.

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

- [`padroes-ptbr.md`](references/padroes-ptbr.md) lista 38 padrões com
  exemplos de antes e depois, as ressalvas para não marcar falso positivo e
  os sinais de voz que devem sobreviver. Leitura obrigatória antes de editar.
- [`avaliacao.md`](references/avaliacao.md) valida fidelidade, voz, clareza,
  escopo e entrega conforme o modo. Inclui dez casos de regressão para revisar
  a skill. Confira os critérios aplicáveis antes de entregar.
- [`exemplos.md`](references/exemplos.md) traz entradas e saídas completas
  nos modos editar, reescrever e detectar. Consulta opcional.

A regra principal é simples: especificidade deve vir do original ou do
contexto fornecido pelo usuário. Se faltar um detalhe, preserve uma versão
simples ou sinalize a lacuna; nunca invente fatos. Amostras de voz orientam
estilo, sem transferir experiências ou informações para o texto editado.

Sem pedido explícito, a skill preserva citações de terceiros, código, dados,
links, termos técnicos, voz e quantidade de informação. Pedidos como “mais
formal”, “resuma” e “só o texto” prevalecem sobre esses padrões de edição.
Revisão de estilo não confirma a veracidade do texto nem determina autoria.

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
