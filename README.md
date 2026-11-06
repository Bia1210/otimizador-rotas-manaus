# 📍 Otimizador de Rotas e Visitas de Campo (Manaus)

> Projeto de otimização geoespacial, priorização de rotas e assistente de voz para representantes farmacêuticos.

> **Projeto independente de portfólio, com dados fictícios.** Não possui vínculo com nenhuma empresa ou laboratório. Nomes de médicos, CRMs, produtos e telefones são inventados.

## 📌 Visão Geral

Este projeto foi desenvolvido em Python para apoiar a logística e a gestão de tempo de representantes comerciais e propagandistas médicos na cidade de Manaus. A ferramenta automatiza a leitura dos dados de visitação, calcula a prioridade de retorno com base no histórico, gera mapas interativos para navegação e sintetiza resumos matinais em áudio com Inteligência Artificial.

## 🛠️ Tecnologias e Bibliotecas

- **Python 3.x** (Google Colab)
- **Pandas:** limpeza, manipulação e cálculo de priorização.
- **Folium:** mapas interativos.
- **Geopy (Nominatim/OpenStreetMap):** geocodificação de endereços.
- **gTTS (Google Text-to-Speech):** síntese de voz para o briefing diário.
- **Ollama / Llama 3.2 (local):** geração dinâmica do texto do briefing, sem enviar dados para APIs pagas.
- **Power BI:** painel executivo.

## 🚀 Funcionalidades

1. **Ingestão resiliente de dados:** leitura de planilha com detecção automática do cabeçalho e dados de segurança (*fallback*) caso a conexão falhe.
2. **Priorização por cadência:** classifica cada visita em `Urgente` (mais de 7 dias sem visita), `Atenção` (5 a 7 dias) e `Em Dia` (menos de 5 dias).
3. **Mapeamento geoespacial:** pontos de visita em Manaus coloridos por prioridade, com links diretos para navegação (Google Maps).
4. **Mensagem para WhatsApp:** monta a rota do dia em um link de envio.
5. **Briefing matinal com IA:** texto gerado por LLM local e convertido em áudio `.mp3`.

## 📊 Painel Executivo (Power BI)

Os dados tratados no notebook são exportados em CSV e consumidos por um dashboard em Power BI:

- **Indicadores:** `Total Visitas`, `Visitas Prioritárias` e `% Urgência`.
- **Mapa de visitas:** bairros de Manaus (Adrianópolis, Centro, Chapada, Japiim), com cores por status de retorno.
- **Análise por especialidade:** volume de visitas por especialidade médica.

![Dashboard](docs/dashboard.png)

📄 Documentação técnica completa: [`docs/Documentacao_Otimizador_de_Rotas.pdf`](docs/Documentacao_Otimizador_de_Rotas.pdf)

## ▶️ Como executar

1. Abra `assistente_rotas_propagandista.ipynb` no Google Colab.
2. Na célula de ingestão, troque `SEU_ID_DA_PLANILHA` pelo ID da sua planilha do Google Sheets (com as colunas esperadas), ou use seus próprios dados fictícios.
3. Na célula do WhatsApp, troque `55929XXXXXXXX` por um número de teste.
4. *(Opcional)* Para o briefing com IA, instale o [Ollama](https://ollama.com) e baixe o modelo: `ollama pull llama3.2:3b`. Sem ele, o notebook usa um texto padrão.
5. Rode as células em ordem. O CSV `dados_rotas_visitas.csv` é gerado ao final, pronto para o Power BI.

## ⚠️ Limitações

- Base pequena, de demonstração.
- O **Geopy** envia endereços ao serviço Nominatim e o **gTTS** envia o texto do briefing ao Google. Com dados reais de médicos, isso exige avaliação de privacidade (LGPD) e autorização da empresa.
- O painel **prioriza e localiza** as visitas; o cálculo da ordem ótima de deslocamento é uma evolução prevista.

## 🔒 Privacidade

Este repositório contém apenas **dados fictícios (mock data)** para demonstração técnica e portfólio. Nenhuma informação comercial confidencial ou dado pessoal real está incluído.

## ✒️ Autora

Desenvolvido por **Beatriz Cavalcante de Melo**.
