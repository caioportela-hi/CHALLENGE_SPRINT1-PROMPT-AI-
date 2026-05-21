# ChargeGrid Intelligence Bot
### Chatbot operacional para gerenciamento de eletropostos GoodWe — EV Challenge 2026 | FIAP

---

## Integrantes do Projeto

| Nome | RM |
|------|-----|
| *Caio César Portela França* | *573127* |

---

##  Sobre o Desafio

O **EV Challenge 2026** proposto pela **GoodWe** apresenta um problema real enfrentado por operadores de eletropostos comerciais: a ausência de mecanismos integrados para **orquestrar potência**, **registrar ciclos de recarga**, **processar faturamento** e **comunicar status** dos equipamentos — o que a GoodWe denomina **ChargeGrid Intelligence**.

Atualmente, operadores precisam acessar múltiplos painéis e ferramentas desconexas para obter informações básicas sobre seus postos. Não há um ponto único de consulta inteligente que contextualize os dados operacionais.

---

##  Proposta do Chatbot

O **ChargeGrid Intelligence Bot** é um assistente conversacional com IA destinado ao **operador comercial de eletropostos**, com o objetivo de centralizar, contextualizar e responder a demandas operacionais em linguagem natural.

### Persona atendida
**Operador comercial** — responsável pela gestão diária do eletroposto, que precisa de respostas rápidas sobre consumo, faturamento, status dos conectores e alertas de falha, sem depender de suporte técnico para dúvidas rotineiras.

### O que o chatbot resolve
- Consultas sobre **status de conectores** em tempo real
- Dúvidas sobre **orquestração de potência** e balanceamento de carga
- Informações sobre **ciclos de recarga** realizados e histórico
- Questões de **faturamento** e consumo por período
- Interpretação de **alertas e códigos de erro** dos equipamentos GoodWe
- Guias de **procedimentos operacionais padrão**

### O que o chatbot NÃO faz (fora de escopo)
- Controle direto dos equipamentos (sem atuação física)
- Suporte técnico de manutenção preventiva/corretiva aprofundado
- Gestão financeira ou ERP

---

##  Tecnologia Selecionada

| Componente | Tecnologia | Justificativa |
|-----------|-----------|---------------|
| Modelo de IA | OpenAI GPT-4o | Melhor relação custo-desempenho para compreensão de linguagem técnica em português; suporte nativo a function calling para consultas de API |

### Justificativa técnica da escolha do GPT-4o
- **Compreensão técnica**: o modelo interpreta termos de energia elétrica e protocolos de recarga  sem fine-tuning
- **Function calling**: permite ao chatbot decidir autonomamente quando consultar o SEMS+ vs. responder com contexto base
- **Multilingue**: responde em português com qualidade nativa
- **API madura**: documentação sólida, SLA estabelecido, adequado para MVP em prazo de Sprint

---

##  Fluxo de Funcionamento (resumo)

```
Operador envia pergunta
        ↓
Injeção de contexto (system prompt + dados do posto)
        ↓
Classificação de intenção (operacional / técnica / faturamento)
        ↓
┌─────────────────┐    ┌──────────────────────┐
│ Requer dados    │    │ Contexto base        │
│ em tempo real?  │    │ é suficiente?        │
│ → Consulta o    │    │ → Responde direto    │
│   SEMS+         │    │   com system prompt  │
└─────────────────┘    └──────────────────────┘
        ↓
Geração de resposta pelo GPT-4o
        ↓
Resposta exibida na interface do operador
```

---


*Projeto desenvolvido para o EV Challenge 2026 — GoodWe × FIAP*
