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
| `editar` | Texto final completo e uma seção curta `O que mudou` |
| `detectar` | Padrão, trecho exato e correção sugerida |
| `calibrar voz` | Edição guiada por uma amostra do autor |
| `arquivo` | Alteração gravada no arquivo e resumo breve |
| `embutido` | Apenas o texto final, para uso dentro de outra tarefa |

## Critérios de edição

As referências em [`references/`](references/) são obrigatórias durante o
trabalho:

- [`padroes-ptbr.md`](references/padroes-ptbr.md) lista padrões e ressalvas.
- [`avaliacao.md`](references/avaliacao.md) valida fidelidade, voz, clareza,
  padrões e fricção da entrega.

A regra principal é simples: especificidade deve vir do original ou do
usuário. Se faltar um detalhe, corte, sinalize a lacuna ou pergunte; nunca
invente nomes, números, datas, fontes, exemplos ou resultados.

## Instalação

Em um ambiente que carrega skills a partir de um diretório compartilhado:

```bash
git clone git@github.com:forge-z/texto-natural-ptbr.git \
  /workspace/.agents/skills/texto-natural-ptbr
```

O arquivo [`SKILL.md`](SKILL.md) é o ponto de entrada. Não há dependências de
runtime.

## Licença e fontes

Distribuída sob MIT. As fontes e atribuições estão em
[`SOURCES.md`](SOURCES.md).
