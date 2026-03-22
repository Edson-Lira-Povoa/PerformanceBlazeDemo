# 🚀 Desafio Técnico: Performance Test - BlazeDemo

Este repositório contém a automação de testes de performance para o cenário de compra de passagens aéreas no site [BlazeDemo](https://www.blazedemo.com). O objetivo é validar a estabilidade e o tempo de resposta do sistema sob uma carga específica.

## 📋 Cenário de Teste
Simulação do fluxo de compra ponta a ponta:
1.  **Home:** Acesso à página inicial.
2.  **Reserva:** Seleção de cidades de origem e destino.
3.  **Escolha de Voo:** Seleção da companhia aérea e preço.
4.  **Compra:** Preenchimento dos dados do passageiro.
5.  **Confirmação:** Validação da mensagem de sucesso ("Thank you for your purchase today!").

## 📈 Critérios de Aceitação
De acordo com os requisitos técnicos:
* **Vazão Alvo:** 250 requisições por segundo (RPS).
* **Performance:** 90th Percentile (P90) inferior a **2 segundos**.
* **Cenários:** Teste de Carga (estabilidade) e Teste de Pico (Spike).

---

## 🛠️ Tecnologias Utilizadas
* **Apache JMeter 5.x**
* **Precise Throughput Timer** (para controle preciso de RPS)
* **HTML Dashboard Report** (para análise de métricas)

---

## 🚀 Como Executar o Script

Para evitar o pop-up de "arquivo já existente" e garantir a melhor performance da máquina injetora, utilize o comando abaixo. A flag `-f` força o JMeter a deletar resultados anteriores antes de iniciar.

### Via Terminal (CLI Mode):
```bash
jmeter -n -t ./scripts/BlazeDemo_Performance.jmx -l ./results/log_execucao.jtl -e -o ./results/dashboard -f