# ⚡ Lumora Bank — Analytics Engineering & Tracking Sandbox

![Version](https://img.shields.io/badge/version-1.0.1-gold)
![Architecture](https://img.shields.io/badge/architecture-Event--Driven-blue)
![GA4](https://img.shields.io/badge/GA4-Standard_Schema-green)

O **Lumora Bank** é uma aplicação web interativa (SPA) desenvolvida para simular jornadas bancárias complexas e servir como um ambiente de testes de alta precisão (*sandbox*) para **Web Analytics**, **Google Tag Manager (GTM)** e **Firebase Analytics**.

O objetivo do projeto é demonstrar a implementação de uma camada de dados (*Data Layer*) robusta, nativa e resiliente, pronta para ingestão no GA4 e expansão para Server-Side Tagging (sGTM).

---

## 📌 Principais Recursos Técnicos

* **Arquitetura Event-Driven Nativa:** Os eventos analíticos nascem direto do código-fonte, eliminando dependências frágeis de scraping via DOM no GTM.
* **Função Centralizadora (`pushGTM`):** Padronização da emissão de payloads para o `window.dataLayer`.
* **Tratamento de Estado em Single Page Application (SPA):** Execução automática de `dataLayer.push({ ecommerce: null })` antes de novos envios para prevenir contaminação de variáveis entre visões.
* **Console de Debug Visual:** Interface integrada à aplicação que simula o comportamento do GTM Preview e do Firebase DebugView em tempo real.

---

## 🎯 Mapeamento de Eventos e Data Layer

A aplicação implementa os principais eventos de conversão e produto no padrão do **GA4 Ecommerce**:

| Evento (`event`) | Categoria / Jornada | Descrição & Parâmetros Capturados |
| :--- | :--- | :--- |
| `sign_up` | Onboarding / KYC | Disparado na conclusão do cadastro. Contém `method`, `kyc_status`, `tempo_total_onboarding_seg`. |
| `begin_checkout` | Funil Financeiro | Disparado nas telas de confirmação (PIX/Fatura). Contém `value`, `currency`, `items`. |
| `purchase` | Conversão Principal | Confirmado em envios de PIX, pagamentos e aplicações. Contém `transaction_id`, `value`, `currency`, `payment_type`, `items`. |
| `select_content` | Interação / UI | Mapeia cliques em ações rápidas da Home via atributo `data-qa`. Contém `content_type`, `item_id`. |
| `page_view` | Navegação SPA | Disparado em cada troca dinâmica de tela. Contém `page_title`, `page_location`. |

---

## 🛠️ Tecnologias Utilizadas

* **Front-end:** HTML5, CSS3, JavaScript (Vanilla SPA)
* **Tagging & Tracking:** Google Tag Manager, Google Analytics 4, Firebase Analytics
* **Hospedagem:** GitHub Pages

---

## 🚀 Como Testar Localmente ou Produção

1. Acesse a demonstração ativa via [GitHub Pages](https://60aum.github.io/lumora/).
2. Abra o **DevTools do Navegador (F12)** no console e digite `dataLayer` para inspecionar os arrays em tempo real.
3. Utilize a extensão **Google Tag Assistant** conectada ao seu container do GTM para auditar o disparo das tags.
