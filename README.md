# TC_fase3_Fine_tuning_llama3
# 🚀 Desafio do Tech Challenge

## 🎯 **Objetivo Principal**
- Executar o **fine-tuning** de um modelo de linguagem (ex.: **LLaMA**, **BERT**, **GPT**) usando o dataset **"The AmazonTitles-1.3MM"**.
- Receber perguntas dos usuários com base em um **contexto** (título do produto).
- Gerar respostas baseadas na **descrição do produto** após o fine-tuning.
- 🔗Links Principais:
- https://github.com/beatrizcardc/TC_fase3_Fine_tuning_llama3.git
- https://youtu.be/yFqfh31Yg10
- https://colab.research.google.com/drive/1CZzwU-CrVC8pPMEcnoTDA2CgrvQYtTqE#scrollTo=wvvIfq-5GjW6
---

## 📌 **Pipeline Completo do Trabalho**

### 🗂️ **Escolha do Dataset**
- **Dataset**: The AmazonTitles-1.3MM.
- **Campos**: Utilizar os campos **título** e **descrição** dos produtos.
- 📥 **Download e Armazenamento**: Realizar download e armazenar de forma segura no **Google Drive**.

---

### 🧹 **Preparação do Dataset**
- 📤 **Carregar e Inspecionar**: Carregar e revisar os dados.
- 🧼 **Limpeza**:  
  - Remover linhas com **valores ausentes**.  
  - Remover **duplicatas**.  
  - Normalizar o texto (**remoção de caracteres especiais**).  
- 📉 **Redução**: Reduzir o tamanho do dataset para **40k registros**.  
- 🔀 **Divisão**: Separar em **80% treino** e **20% validação**.

---

### 📊 **Análise de Comprimento**
- 📏 **Analisar Comprimentos** dos prompts e responses.
- 🎯 **Definir max_length**:  
  - **Prompt**: 75 tokens.  
  - **Response**: 450 tokens (para acomodar até 300 palavras).  
  - **Total**: 525 tokens.  
- 🛠️ **Ajuste de Hyperparameters**: Para evitar erros de **Out Of Memory (OOM)** durante o treinamento.

---

### 🔧 **Carregamento do Modelo**
- 📥 **Modelo Pré-treinado**: **Llama 3.2-1B** ou similar.
- 🧪 **Quantização**: Aplicar **8-bit** ou **4-bit** para otimização de memória.
- 🛠️ **LoRA**: Configurar **LoRA** para fine-tuning eficiente.

---

### 🔄 **Pré-processamento e Tokenização**
- 📝 **Função de Pré-processamento**:  
  - Combinar **prompts** e **responses** em um único formato.  
  - **Tokenização** com truncamento e padding.  
- 🔗 **Definir pad_token** como eos_token para compatibilidade.

---

### ⚙️ **Configuração do Treinamento**
- 📊 **Hiperparâmetros**:  
  - **Epochs**: 3 a 5.  
  - **Batch Size**: 4 - 2 (ajustado para evitar OOM).  
  - **max_length**: 1024 tokens (ou conforme análise).  
  - **Checkpoints**: Salvar checkpoints a cada `save_steps`.  
- 📊 **Monitoramento**:  
  Usar **WandB** e **TensorBoard** para acompanhar métricas como:  
  - `eval_loss`  
  - `validation_loss`  
- 💾 **Callbacks**: Salvar os **dois últimos checkpoints** automaticamente.

---

### 🚀 **Execução do Fine-Tuning**
- ▶️ **Iniciar Treinamento**: Utilizar o **Trainer** para treinar o modelo.
- 📉 **Validação**: Avaliar durante o treinamento para acompanhar **eval_loss** e **validation_loss**.

---

### 🧪 **Avaliação e Geração de Respostas**
- 📝 **Dados de Teste**: Carregar os dados de teste e o **Ground Truth**.
- 📥 **Modelos**: Carregar os modelos **pré-treinado** e **fine-tuned**.
- 🗨️ **Gerar Respostas**: Produzir respostas para os dados de teste.
- 🔄 **Retreinamento com Ajustes**: Modificar hiperparâmetros e formatar o dataset com title e content.
- 📈 **Métricas de Desempenho**:  (somente referÊncia)
  - **BLEU**  
  - **ROUGE**
![Análise das Respostas v4](https://raw.githubusercontent.com/beatrizcardc/TC_fase3_Fine_tuning_llama3/main/analise_respostas_v4.png)

🔍 **Após Melhorias da Geração**
![Análise das Respostas v4](https://raw.githubusercontent.com/beatrizcardc/TC_fase3_Fine_tuning_llama3/main/analise2_respostas_v4.png)
 - Como projeto inicial de Fine Tuning e ao reduzir os registros, por limitações técnicas, sabemos que não teremos respostas tão robustas. Mas como MVP atingimos o resultado satisfatório para alguns prompts.
---

### 📦 **Entrega do Projeto**
- 📄 **Documento Detalhado**:  
  - Descrição da **seleção e preparação** do dataset.  
  - Processo de **fine-tuning** com parâmetros utilizados.  
- 💻 **Código-Fonte**: Repositório com o código do **fine-tuning**.  
- 🎥 **Vídeo de Demonstração**: Mostrando o modelo gerando respostas.

---



