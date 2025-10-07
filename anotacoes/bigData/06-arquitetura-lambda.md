# Arquitetura Lambda

A arquitetura Lambda é uma forma de organizar sistemas de Big Data para lidar com dois tipos de processamento de dados Batch e Stream.

A ideia é juntar os dois:
- O batch layer: cuida da visão “correta e completa” dos dados.
- O speed/streaming layer: cuida da visão “rápida e imediata” dos dados.
- O serving layer: combina os resultados dos dois para o usuário final ter uma resposta rápida, mas também confiável.

### Exemplo
Imagine um app de previsão do tempo. O batch pega todos os dados históricos de clima (dos últimos anos) e calcula padrões complexos → demora, mas é preciso.
O streaming pega os sensores de temperatura e chuva em tempo real e mostra mudanças imediatas → é rápido, mas pode ser ruidoso.

O serving junta os dois: você vê a previsão atualizada em tempo real, mas também apoiada pelos cálculos históricos.

