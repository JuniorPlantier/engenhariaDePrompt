# Prompt: Gerar scripts SQL de UPDATE a partir de arquivo CSV usando Java

## Objetivo
Criar um programa em Java que leia um arquivo `.csv` contendo dados de pedidos e variáveis, e gere arquivos de script SQL com comandos `UPDATE`, organizados em blocos de 100 comandos por arquivo, prontos para execução.

## Prompt
> Crie um script em Java com as seguintes características:
>
> - Recebe como **parâmetro de entrada** um arquivo CSV.
> - O CSV possui duas colunas:
>   - Primeira coluna: `idpedido`
>   - Segunda coluna: `variavel`
> - A primeira linha do CSV é um cabeçalho e **deve ser ignorada**.
> - Para cada linha, deve ser gerado um comando SQL no formato:
>
>   ```sql
>   update nome_tabela set valor_variavel = 'variavel' where pedido = idpedido;
>   ```
>
> - Os comandos devem ser agrupados em **arquivos com no máximo 100 `UPDATEs` cada**.
> - Cada arquivo gerado deve:
>   - Começar com `START TRANSACTION;`
>   - Conter até 100 comandos `UPDATE`
>   - Finalizar com `COMMIT;`
> - O programa deve:
>   - Criar uma subpasta chamada `saida` na **mesma pasta onde está o CSV de entrada**
>   - Salvar os arquivos SQL gerados nessa subpasta
>   - Nomear os arquivos como `update_1.sql`, `update_2.sql`, etc.

## Dicas de uso
- Ideal para atualizar registros em lote com segurança (transações)
- Útil para DBAs, analistas de dados ou desenvolvedores que precisam transformar dados tabulares em scripts de banco

## Extensões possíveis (caso queira evoluir)
- Validar o conteúdo do CSV antes de gerar os arquivos
- Permitir personalização do nome da tabela ou da coluna via argumentos
- Compatibilidade com outros delimitadores (como `;` ou `|`)
