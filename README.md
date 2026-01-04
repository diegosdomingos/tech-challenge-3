# 🩺 Assistente Médico com LLM Fine-Tuned

Este projeto implementa um assistente médico-científico baseado em um modelo de linguagem fine-tuned com dados médicos internos, como perguntas frequentes, protocolos clínicos e exemplos padronizados de decisão.

O assistente responde de forma estruturada, objetiva e controlada, seguindo o formato:

Decisão: SIM | NÃO | TALVEZ
Justificativa: explicação objetiva baseada no contexto

O objetivo é apoio à decisão clínica, sem substituir avaliação humana.


# 🧠 O que o modelo faz

Utiliza um modelo LLM fine-tuned (LoRA) hospedado no Hugging Face

Responde exclusivamente em português

Não utiliza conhecimento externo

Não prescreve medicamentos

Segue regras rígidas de formato e segurança

Atua como QA médico geral, usando um contexto padrão interno


# ▶️ Como executar o projeto no Google Colab

## Executando o notebook main.ipynb
  1. Abra o notebook main.ipynb no Google Colab
  2. Altere o modo de execução de CPU para GPU
  3. Crie o arquivo ENV no seu drive no caminho: "/content/drive/MyDrive/token-hf/env"

    - Chaves que devem existir no arquivo ENV:
     HF_TOKEN = Token para acesso ao HuggingFace
     HF_USER_REPO = Nome do usuário do HugginFace
  4. Execute o notebook

## Executando o notebook medical_assistant.ipynb
  1. Abra o notebook main.ipynb no Google Colab
  2. Altere/Verifique o modo de execução de CPU para GPU
  3. Crie/Verifique o arquivo ENV no seu drive no caminho: "/content/drive/MyDrive/token-hf/env"

    - Chaves que devem existir no arquivo ENV:
     HF_TOKEN = Token para acesso ao HuggingFace    
     HF_USER_REPO = Nome do usuário do HugginFace
  4. Execute o notebook


Obs.: É necessário liberar acesso ao Google Drive

# ✅ Após a execução dos passos anteriores, o assistente deve funcionar corretamente

# ⚠️ Aviso importante

Este assistente:

Não substitui avaliação médica

Não realiza prescrição

Deve ser utilizado apenas como ferramenta de apoio
