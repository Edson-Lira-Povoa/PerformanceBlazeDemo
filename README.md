Blaze Demo – Teste de Performance JMeter

Este repositório contém a automação de testes de performance que eu desenvolvi para o fluxo de compra de passagens aéreas no site BlazeDemo
.
O objetivo é validar estabilidade, throughput e tempo de resposta do sistema sob uma carga simulada de usuários reais.

🛠 Tecnologias que usei
Apache JMeter 5.x – Criação e execução dos testes de carga
Java 11+ – Ambiente de execução
HTML Dashboard Report – Visualização gráfica dos resultados

🚀 Como rodar meu Test Plan
Clone meu repositório:
git clone https://github.com/Edson-Lira-Povoa/PerformanceBlazeDemo

Execute o teste pelo terminal:
jmeter -n -t ./scripts/script.jmx -l ./results/log_execucao.jtl -e -o ./results/dashboard -f

O relatório HTML será gerado automaticamente na pasta ./results/dashboard.

📋 Cenário que testei

O Test Plan simula todo o fluxo de compra de passagens:

Home: Acesso à página inicial do BlazeDemo
Reserva: Seleção das cidades de origem e destino
Escolha de Voo: Seleção da companhia aérea e preço
Compra: Preenchimento dos dados do passageiro
Confirmação: Validação da mensagem de sucesso (“Thank you for your purchase today!”)


📈 Critérios que considerei
Vazão alvo: 250 requisições por segundo (RPS)
Performance: 90th Percentile (P90) abaixo de 2 segundos


📊 Resultados que obtive
Métrica	Valor	Status
Throughput Médio	46,4 req/s	❌ NOK
90th Percentile (P90)	7.224 ms	❌ NOK
Taxa de Erro	0,00%	✅ OK

O sistema se mostrou funcionalmente estável, mas não atingiu os requisitos de performance.

🚨 Minha análise
1. Vazão (Throughput)
Exigido: 250 req/s
Obtido: 46,4 req/s
Observação: A aplicação não conseguiu processar a carga esperada. Isso indica limitação no sistema ou na infraestrutura usada para o teste.

2. Tempo de Resposta (P90)
Exigido: < 2s
Obtido: 7,2s
Observação: A experiência do usuário é impactada, pois o tempo de resposta ficou 3,6x acima do limite.

3. Taxa de Erro
Obtido: 0%
Observação: Nenhum erro funcional, a aplicação se manteve estável.
Possíveis motivos do resultado
Gargalo de infraestrutura: O servidor BlazeDemo pode ter limitações de CPU/Memória.
Latência de rede: Ambiente público pode impactar o tempo de resposta.


