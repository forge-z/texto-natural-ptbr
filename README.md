# texto-natural-ptbr

Skill para editar, reescrever ou auditar textos em português brasileiro sem
apagar a voz do autor.

Ela combina critérios de edição linguística com um fluxo de trabalho de baixa
fricção: começa pela entrega, usa passos curtos quando necessário, mantém o
estado visível entre rodadas e termina em uma ação concreta ou no fim real da
tarefa.

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
| `editar` | Texto final completo e uma seção curta `O que mudou`, com a menor intervenção possível |
| `reescrever` | Texto refeito quando a edição mínima não resolve; mesmos limites de fatos e voz |
| `detectar` | Padrão, trecho exato e correção sugerida |
| `calibrar voz` | Edição guiada por uma amostra do autor |
| `arquivo` | Alteração gravada no arquivo e resumo breve |
| `embutido` | Apenas o texto final, para uso dentro de outra tarefa |

## Critérios de edição

As referências em [`references/`](references/) fazem parte do trabalho:

- [`padroes-ptbr.md`](references/padroes-ptbr.md) lista 38 padrões com
  exemplos de antes e depois, as ressalvas para não marcar falso positivo e
  os sinais de voz que devem sobreviver. Leitura obrigatória antes de editar.
- [`avaliacao.md`](references/avaliacao.md) valida fidelidade, voz, clareza,
  padrões e fricção da entrega. Leitura obrigatória depois de editar.
- [`exemplos.md`](references/exemplos.md) traz entradas e saídas completas
  nos modos editar, reescrever e detectar. Consulta opcional.

A regra principal é simples: especificidade deve vir do original ou do
usuário. Se faltar um detalhe, corte, sinalize a lacuna ou pergunte; nunca
invente nomes, números, datas, fontes, exemplos ou resultados.

O que a skill não altera: citações de terceiros, código, dados, links,
termos técnicos corretos, a ortografia e a forma de tratamento do autor e a
quantidade de informação. Editar não é resumir.

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
