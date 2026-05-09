# Análise de Sobrevivência: Registros de falhas no Ar Condicionado da Frota de Ônibus (Rio de Janeiro)

## 📋 Visão Geral
Este projeto investiga os fatores associados à velocidade de ocorrência de falhas no sistema de ar condicionado da frota de ônibus do Rio de Janeiro, com foco particular na "Operação Verão". O estudo cruza dados operacionais e de licenciamento para compreender o panorama de avarias térmicas nos transportes públicos da cidade.

## 🎯 Motivação
Durante os meses de maior calor, o desempenho da climatização é um fator crítico, sendo alvo de monitorização e fiscalização contínua por parte do poder público. Como nem todos os veículos apresentam falhas ao longo do período de observação, ocorre um fenómeno estatístico conhecido como **censura**. Métodos estatísticos tradicionais baseados em médias ou classificação direta não conseguem lidar adequadamente com este cenário. A aplicação da **Análise de Sobrevivência** justifica-se para modelar corretamente o tempo até ao registo da falha, permitindo identificar que características da frota mitigam ou agravam o risco de inoperância.

## 🛠️ Escopo e Metodologia
O escopo do trabalho contempla a integração, limpeza e análise de bases de dados abertas provenientes do portal **Data.Rio**:
- **Licenciamento (`licenciamento.csv`):** Dados cadastrais e estruturais da frota (ano de fabrico, chassi, fabricante, lotação máxima, etc.).
- **Registo Agente Verão (`sppo_registro_agente_verao.csv`):** Histórico das notificações de veículos com a climatização avariada.
- **Veículo Dia (`sppo_veiculo_dia.csv`):** Registos do histórico de operação diária dos veículos.

A unidade de análise é o veículo individual. Foram aplicadas técnicas de exploração de dados e **Curvas de Sobrevivência (Kaplan-Meier)** para comparar diferentes grupos de viaturas na janela temporal selecionada (janeiro a agosto de 2024).

## ⚠️ Limitações
- **Análise do Primeiro Evento:** O modelo contempla estritamente a primeira notificação de falha de cada veículo. Avarias reincidentes não são contabilizadas.
- **Recorte Temporal Restrito:** A janela de análise teve de ser limitada (janeiro a 10 de agosto de 2024). A inclusão de dados posteriores em que houve lacunas de registos (apagão de dados) iria distorcer e inflacionar artificialmente a "sobrevivência" da frota.
- **Exclusões Específicas:** O estudo foca-se apenas nos veículos equipados com ar condicionado de origem. Registos anómalos (por exemplo, veículos com a primeira data de operação igual ou superior à última) foram removidos da amostra.
- **Forte Censura à Direita:** Uma grande percentagem da frota não obteve qualquer registo de falha até ao fim da observação, limitando a precisão exata do tempo médio de avaria para a totalidade do sistema.

## 💻 Tecnologias e Ferramentas
- **Linguagem:** Python
- **Bibliotecas Principais:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `lifelines`
- **Ambiente:** Quarto / Jupyter Notebook

## 👥 Autores
- Kaio Alvim

