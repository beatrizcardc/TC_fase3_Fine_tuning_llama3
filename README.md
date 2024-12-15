# TC_fase3_Fine_tuning_llama3
Desafio do Tech Challenge 
Objetivo Principal:  Executar o fine-tuning de um modelo de linguagem (ex.: LLaMA, BERT, GPT) usando o dataset "The AmazonTitles-1.3MM".  
Receber perguntas dos usuários com base em um contexto (título do produto).  
Gerar respostas baseadas na descrição do produto após o fine-tuning.

________________________________________
📌 Pipeline Completo do Trabalho
________________________________________
🗂️ Escolha do Dataset
•	Dataset: The AmazonTitles-1.3MM.
•	Campos: Utilizar os campos título e descrição dos produtos.
•	📥 Download e Armazenamento: Realizar download e armazenar de forma segura no Google Drive.
________________________________________
🧹 Preparação do Dataset
•	📤 Carregar e Inspecionar: Carregar e revisar os dados.
•	🧼 Limpeza:
o	Remover linhas com valores ausentes.
o	Remover duplicatas.
o	Normalizar o texto (remoção de caracteres especiais).
•	📉 Redução: Reduzir o tamanho do dataset para 40k registros.
•	🔀 Divisão: Separar em 80% treino e 20% validação.
________________________________________
📊 Análise de Comprimento
•	📏 Analisar Comprimentos dos prompts e responses.
•	🎯 Definir max_length:
o	Prompt: 75 tokens.
o	Response: 450 tokens (para acomodar até 300 palavras).
o	Total: 525 tokens.
•	🛠️ Ajuste de Hyperparameters: Para evitar erros de Out Of Memory (OOM) durante o treinamento.
________________________________________
🔧 Carregamento do Modelo
•	📥 Modelo Pré-treinado: Llama 3.2-1B ou similar.
•	🧪 Quantização: Aplicar 8-bit ou 4-bit para otimização de memória.
•	🛠️ LoRA: Configurar LoRA para fine-tuning eficiente.
________________________________________
🔄 Pré-processamento e Tokenização
•	📝 Função de Pré-processamento:
o	Combinar prompts e responses em um único formato.
o	Tokenização com truncamento e padding.
•	🔗 Definir pad_token como eos_token para compatibilidade.
________________________________________
⚙️ Configuração do Treinamento
•	📊 Hiperparâmetros:
o	Epochs: 3 a 5.
o	Batch Size: 8 (ajustado para evitar OOM).
o	max_length: 525 tokens (ou conforme análise).
o	Checkpoints: Salvar checkpoints a cada save_steps.
•	📊 Monitoramento: Usar WandB e TensorBoard para acompanhar métricas como:
o	eval_loss
o	validation_loss
•	💾 Callbacks: Salvar os dois últimos checkpoints automaticamente.
________________________________________
🚀 Execução do Fine-Tuning
•	▶️ Iniciar Treinamento: Utilizar o Trainer para treinar o modelo.
•	📉 Validação: Avaliar durante o treinamento para acompanhar eval_loss e validation_loss.
________________________________________
🧪 Avaliação e Geração de Respostas
•	📝 Dados de Teste: Carregar os dados de teste e o Ground Truth.
•	📥 Modelos: Carregar os modelos pré-treinado e fine-tuned.
•	🗨️ Gerar Respostas: Produzir respostas para os dados de teste.
•	📈 Métricas de Desempenho:
o	BLEU
o	ROUGE
________________________________________
📦 Entrega do Projeto
•	📄 Documento Detalhado:
o	Descrição da seleção e preparação do dataset.
o	Processo de fine-tuning com parâmetros utilizados.
•	💻 Código-Fonte: Repositório com o código do fine-tuning.
•	🎥 Vídeo de Demonstração: Mostrando o modelo gerando respostas.


