

# Loja Black Friday em C#

Projeto de estudo em C# para praticar **Programação Orientada a Objetos**, simulando uma loja de produtos **novos** e **seminovos** com compras de estoque, vendas e uma campanha de **Black Friday**.

> ⚠️ Projeto de estudo. Os produtos, preços e custos usados no código são **fictícios** e não têm ligação com sistemas ou valores reais de nenhuma empresa.

## O que o sistema faz

- Cadastra produtos novos e seminovos, cada tipo com seus valores fixos (desconto de Black Friday e garantia)
- Registra **compras** de estoque, pagando o preço de custo
- Registra **vendas** com validação de estoque (se algum item não tiver estoque, nada é baixado)
- Ativa e encerra a campanha de Black Friday, mudando o preço de todos os produtos de uma vez
- Guarda o preço de cada item **no momento da venda**, então encerrar a campanha não altera vendas passadas
- Gera um relatório com faturamento, custo dos itens vendidos, lucro bruto e total gasto em compras

## Valores fixos por condição do produto

| Condição | Desconto na Black Friday | Garantia |
|---|---|---|
| Novo | 20% | 365 dias |
| Seminovo | 10% | 90 dias |

## Onde cada pilar da POO aparece

| Pilar | Onde |
|---|---|
| Abstração | `Produto` é uma classe abstrata que define o que todo produto tem e faz |
| Encapsulamento | O estoque só muda por `AdicionarEstoque` e `BaixarEstoque`, que validam a operação |
| Herança | `ProdutoNovo` e `ProdutoSeminovo` herdam de `Produto` |
| Polimorfismo | `IPoliticaDesconto` tem duas implementações (`SemDesconto` e `CampanhaBlackFriday`), e cada produto informa o seu próprio percentual |

## Classes

| Classe | Papel |
|---|---|
| `Produto` | Classe base abstrata, com validações e controle de estoque |
| `ProdutoNovo` / `ProdutoSeminovo` | Definem os valores fixos de cada condição |
| `IPoliticaDesconto` | Contrato para calcular o preço final de um produto |
| `SemDesconto` / `CampanhaBlackFriday` | Políticas de preço (normal e Black Friday) |
| `ItemVenda` | Produto, quantidade e preço unitário no momento da venda |
| `Venda` | Conjunto de itens, com total e custo |
| `Loja` | Compras, vendas, catálogo e relatório |
| `Fmt` | Formata valores em reais (R$ 1.500,00) |
| `Program` | Demonstração do sistema |

## Como rodar

**Sem instalar nada:** cole o código em um compilador online de C#, como o [OneCompiler](https://onecompiler.com/), e clique em Run.

**Na sua máquina:** com o [.NET 8 SDK](https://dotnet.microsoft.com/download) instalado, use:

```bash
dotnet run
```

## Ideias para evoluir

- Parte 2: modelar o mesmo cenário em **SQL**, com tabelas de produtos, categorias, campanhas e vendas, e consultas de faturamento, lucro e estoque
- Cupons de desconto e frete
- Compra de seminovos direto de clientes (trade-in)
- Testes unitários com xUnit
- Persistência em arquivo ou banco de dados

## Exemplo de saída

![Saída do programa](<img width="1912" height="914" alt="Resultado do Projeto" src="https://github.com/user-attachments/assets/b154107f-22d3-4776-82ae-8045933a2b1b" />
)

