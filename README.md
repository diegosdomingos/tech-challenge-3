# 🧠 Assistente Médico Inteligente com RAG e LLM em Português

## 🎯 Objetivo do Projeto

Este projeto tem como objetivo desenvolver um **assistente médico inteligente em português**, combinando **Large Language Models (LLMs)** com **Retrieval-Augmented Generation (RAG)** e um **banco de dados clínico simulado**.

O assistente é capaz de:
- Identificar e buscar pacientes em um banco de dados
- Consultar histórico de atendimentos médicos fictícios
- Realizar buscas semânticas em bases médicas científicas
- Responder perguntas médicas de forma clara, contextualizada e segura
- Controlar o fluxo conversacional por estados (ex.: aguardando nome do paciente)

⚠️ **Todos os dados clínicos são fictícios** e utilizados apenas para fins educacionais.

---

## 🚀 Passo a Passo para Clonar, Abrir e Executar

### 1️⃣ Clonar o Repositório (branch correta)
```bash
git clone -b branch_diego_assistant https://github.com/diegosdomingos/tech-challenge-3.git
```
### 2️⃣ Abrir o Notebook
Abra o arquivo `main.ipynb` no Google Colab (recomendado)

### 3️⃣ Instalar Dependências
Execute as células iniciais do notebook, que instalam automaticamente as dependências:

```bash
pip install -q unsloth[colab-new] faiss-cpu sentence-transformers trl datasets scikit-learn
pip install --no-deps xformers "trl<0.9.0" peft accelerate bitsandbytes
pip install -U spacy transformers accelerate
python -m spacy download pt_core_news_lg
```

---

### 4️⃣ Configurar Variáveis de Ambiente
Crie um arquivo `.env` com (Passo opicional para salvar modelo no HuggingFace):

```
HF_TOKEN=seu_token_huggingface
HF_USER_REPO=seu_usuario/seu_repositorio
```

---

### 5️⃣ Executar o Notebook
Execute as células **em ordem**, respeitando o fluxo definido no `main.ipynb`.

---

## 📘 Explicação do Notebook `main.ipynb`

### 🔹 1. Setup Inicial
Instala e importa bibliotecas para:
- NLP em português
- Embeddings semânticos
- FAISS
- Fine-tuning com LoRA
- Banco de dados SQLite
- Controle de fluxo conversacional

---

### 🔹 2. Criação do Banco de Dados Clínico
Criação do banco `prontuarios.db` contendo:
- Tabela de pacientes
- Tabela de atendimentos médicos

Os dados são **totalmente fictícios** e simulam um cenário real de clínica médica.

---

### 🔹 3. Carregamento do Dataset Médico
Utiliza o **PubMedQA** como base de conhecimento médico para:
- Criar documentos de contexto
- Alimentar o pipeline RAG

---

### 🔹 4. Pré-processamento e Limpeza de Texto
Aplicação de:
- Normalização textual
- Limpeza de dados
- Preparação dos documentos para embeddings

---

### 🔹 5. Embeddings e Índice FAISS
- Geração de embeddings com `SentenceTransformers`
- Criação e persistência do índice FAISS
- Busca semântica eficiente para recuperação de contexto

---

### 🔹 6. Pipeline RAG
Integra:
- Consulta semântica no FAISS
- Injeção de contexto médico no prompt
- Respostas baseadas em documentos relevantes

---

### 🔹 7. Dataset de Alinhamento em Português
Carregamento do dataset `language_alignment_pt.jsonl`, utilizado para alinhar o comportamento do modelo à língua portuguesa e ao domínio médico.

---

### 🔹 8. Fine-Tuning do Modelo com LoRA
- Modelo base: `unsloth/llama-3-8b-bnb-4bit`
- Treinamento supervisionado (SFT)
- Uso de LoRA para reduzir consumo de memória e custo computacional

---

### 🔹 9. Upload do Modelo para o Hugging Face
Após o treinamento:
- Modelo e tokenizer são enviados para o Hugging Face Hub
- Permite reutilização e inferência futura

---

### 🔹 10. Assistente Conversacional com Controle de Estado
Implementação de lógica de estados, como:
- `awaiting_patient_name`
- Identificação do paciente
- Decisão entre busca no banco ou no RAG
- Fluxo conversacional mais realista

---

## 📊 Datasets Utilizados

| Dataset | Descrição | Fonte |
|------|---------|------|
| **PubMedQA** | Perguntas e respostas baseadas em artigos médicos científicos | https://github.com/pubmedqa/pubmedqa |
| **language_alignment_pt.jsonl** | Dataset de alinhamento em português para uso em Fine-tuning| Incluso no repositório |
| **dataset_intention.jsonl** | Dataset de intenção para uso em Fine-tuning| Incluso no repositório |


---

## 🧠 Tecnologias Utilizadas

- Python
- Hugging Face Transformers
- Unsloth + LoRA
- FAISS
- Sentence Transformers
- SQLite
- spaCy (Português)
- Google Colab

---

## 📌 Considerações Finais

Este projeto demonstra uma arquitetura moderna de **assistente médico inteligente**, integrando:

- Retrieval-Augmented Generation (RAG)
- Fine-tuning eficiente de LLMs
- Banco de dados relacional
- Controle de fluxo conversacional

A solução é modular, extensível e adequada para estudos de IA aplicada à saúde, respeitando boas práticas de segurança e ética.
