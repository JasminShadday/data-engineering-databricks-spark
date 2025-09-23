# Slowly Changing Dimension (SCD)

SCD é uma técnica para lidar com o problema de mudanças em tempo real.
é uma forma de lidar com mudanças em dados históricos dentro de um Data Warehouse.
A ideia é: quando uma informação de um cliente, produto ou funcionário muda (ex: endereço, cargo), como manter isso salvo?
- Você descarta o valor antigo?
- Ou guarda a versão antiga junto com a nova?

## Tipos principais de SCD

### Tipo 1:
Não guarda histórico.
Você sobrescreve o dado antigo com o novo.
#### Exemplo
Cliente mudou de cidade de "São Paulo" para "Rio". A tabela passa a ter só "Rio", e "São Paulo" é perdido.
Serve quando o histórico não é importante.

### Tipo 2:
Mantém histórico completo.
Cada vez que há uma alteração, é criada uma nova linha com o valor atualizado.
Para controlar qual é o dado válido atualmente, usa-se:
Uma flag (ativo/inativo, 1/0),
Ou datas de vigência (data_início, data_fim).

#### Exemplo:

Cliente 1 | Cidade = São Paulo | Vigência = 2019–2023  | Ativo = 0  
Cliente 1 | Cidade = Rio       | Vigência = 2023–atual | Ativo = 1


### Tipo 3: (não é tão usado)
Guarda só uma versão anterior além da atual (não todo o histórico).

#### Exemplo
colunas "cidade_atual" e "cidade_anterior".

Por isso é pouco usado, já que perde histórico mais antigo.

### Híbrido: (não é tão usado)
Combina estratégias de Tipo 1 e Tipo 2 dependendo da coluna.

#### Exemplo

endereço usa Tipo 2 (guardar histórico), telefone usa Tipo 1 (só manter o último).