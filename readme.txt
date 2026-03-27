Case 1 — Otimização de Controle de Almoxarifado com Excel / BI
Descrição
Projeto didático-prático que replica um cenário realista de almoxarifado em pequenas e médias estruturas. O objetivo foi estruturar dados e construir uma solução em Excel e ferramentas de BI para transformar processos operacionais reativos em decisões orientadas por indicadores confiáveis.

Contexto
Durante o estágio no setor de almoxarifado identificou-se um conjunto de problemas típicos:

Controle de estoque parcialmente manual e descentralizado;
Baixa confiabilidade entre estoque físico e registros;
Falta de indicadores claros de consumo e reposição;
Decisões de compra baseadas em percepção, não em dados;
Tempo elevado para localizar e separar materiais.
Consequências observadas:

Rupturas pontuais;
Excesso de itens de baixa rotatividade ocupando capital e espaço;
Retrabalho em conferências e inventários.
Nota: os dados utilizados neste case são simulados para fins didáticos, mas o fluxo e as decisões reproduzem problemas e soluções aplicáveis em operações reais.

Diagnóstico
Antes de qualquer construção técnica, o trabalho focou no entendimento estrutural do problema. Perguntas centrais:

Quais itens têm maior giro?
Onde estão as divergências entre estoque físico e sistema?
Existe padrão de consumo por período?
Qual o tempo médio entre requisição e entrega?
Há estoque parado ocupando espaço e capital?
Principais lacunas identificadas:

Falta de padronização no cadastro de materiais;
Ausência de histórico estruturado de movimentações;
Inexistência de classificação (ex.: curva ABC);
Nenhum controle confiável de estoque mínimo;
Dados descentralizados em planilhas isoladas.
Insight central: o problema não era a “falta de controle”, e sim a falta de uma estrutura lógica e consistente dos dados.

Solução implementada
Arquitetura da solução (Excel / BI)

Base de dados estruturada em 3 camadas:
Cadastro de materiais
Código único, descrição padronizada, categoria.
Movimentações
Data, tipo (entrada/saída), quantidade, setor solicitante.
Parâmetros de controle
Estoque mínimo, lead time estimado, classificação ABC.
Lógica das métricas (diferenciais)

Saldo atual de estoque (a partir do estoque inicial + entradas - saídas).
Consumo médio mensal por item.
Cobertura de estoque (dias).
Identificação de itens abaixo do estoque mínimo.
Giro de estoque (período definido).
Classificação ABC automática (por valor ou consumo).
Decisões de visualização (dashboard)

Cards principais: total de itens em estoque, % abaixo do mínimo, itens críticos.
Gráficos: consumo por período, top itens por saída, curva ABC.
Tabela dinâmica: itens com risco de ruptura, histórico de divergências físico × sistema.
Diferencial técnico do case

Separação clara entre dado bruto (camada de entrada) e camada analítica (cálculos e indicadores).
Métricas orientadas à decisão (ex.: itens para compra imediata, itens para revisão de cadastro).
Estrutura replicável para qualquer operação de almoxarifado com pequenos ajustes de parâmetros.
Como está organizado o repositório
Sugestão de estrutura (ajuste conforme seus arquivos reais):

/data
movimentos_simulados.csv — dados de movimentações (entradas/saídas)
cadastro_materiais.csv — cadastro padronizado
parametros_controle.csv — estoques mínimos e lead times
/excel
modelo_base.xlsx — arquivo com camadas separadas (dados brutos, camada analítica, dashboard)
instrucoes_uso.md — instruções para atualização e manutenção
/bi
dashboard.pbix (ou arquivo exportado) — modelo de BI exemplo (Power BI / similar)
consultas.pq — consultas / ETL exemplificadas
/docs
metodologia.md — descrição técnica da modelagem e métricas
resultados.md — resumo dos resultados simulados e aprendizados
README.md — (este arquivo)
Principais telas / relatórios (sugestões para incluir como imagens)

Dashboard principal (cards + gráficos de consumo)
Tabela de itens críticos (abaixo do mínimo)
Curva ABC (pizza / barra acumulada)
Relatório de divergências (físico × sistema)
Resultados e impacto
O que passou a ser possível:

Identificar rapidamente itens críticos e com risco de ruptura;
Reduzir divergências entre estoque físico e registros por meio de padronização e histórico;
Antecipar compras com base em consumo médio e lead time;
Visualizar concentração de consumo por curva ABC e priorizar ações;
Melhorar o tempo de separação e organização com nova lógica de cadastro.
Métricas de impacto (exemplos simulados)

Redução estimada de rupturas: X% (simulado)
Diminuição de itens de baixa rotatividade em estoque: Y% (simulado)
Tempo médio de localização/requisição reduzido: Z%
Aprendizados técnicos e operacionais
Estrutura de dados bem definida resolve mais problemas do que dashboards complexos.
A qualidade da decisão depende mais da modelagem e dos parâmetros do que da ferramenta escolhida.
Processos simples, quando padronizados e documentados, geram alto impacto operacional.
Importância de separar dados brutos das métricas derivadas para permitir auditoria e rastreabilidade.
Como replicar / instruções rápidas
Padronize o cadastro de materiais (código único + descrição limpa).
Centralize movimentações em um único arquivo ou fonte (data, tipo, quantidade, setor).
Defina parâmetros de controle por item (estoque mínimo, lead time).
Calcule métricas básicas: saldo atual, consumo médio, cobertura (dias), giro.
Classifique itens por curva ABC para priorização.
Monte um dashboard simples com cards e gráficos-chave; revise semanalmente.
Estabeleça rotinas de conferência e atualização (ex.: inventário cíclico).
Observações e limitações
Dados do projeto são simulados para fins didáticos; resultados reais variam conforme qualidade e granularidade dos dados operacionais.
Implementações em larga escala podem demandar integração com ERP, códigos de barras/RFID e processos de recebimento/expedição mais robustos.
Este case foca em modelagem e indicadores; automações (alertas de compra automáticos) podem ser adicionadas conforme demanda.
Contribuições / Contato
Se quiser testar com seus dados, adaptar o modelo ou sugerir melhorias, abra uma issue ou envie um pull request. Para contato direto:

Email: lucianopaivaadm@gmail.com
LinkedIn: linkedin.com/in/luciano-paiva-b0b01a19b