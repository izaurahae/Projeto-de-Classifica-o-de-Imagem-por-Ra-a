# Projeto de Classificação o de Imagem por Raça

Este repositório contém a **segunda atividade prática** desenvolvida durante o curso de Inteligência Artificial da Pretalab.  
O objetivo do projeto foi **apresentar conceitos básicos de aprendizado de máquina**, utilizando dados reais e modelos pré-treinados para **classificar imagens de mulheres pretas e brancas**.

## Objetivo da Atividade

A ideia foi construir um projeto prático de machine learning que nos permitisse:

- Baixar imagens reais da internet
- Reconhecer objetos e rostos com modelos prontos (como ViT e DETR)
- Criar um modelo próprio usando imagens armazenadas no Google Drive
- Treinar esse modelo para classificar novas imagens
- Visualizar os resultados de forma clara, com scores de confiança

##  Etapas Realizadas

###  1. Download de Imagens da Internet
Usamos o comando `!wget` no Google Colab para baixar imagens reais da web e testar os modelos.  

###  2. Uso de Modelos Pré-Treinados (Transfer Learning)

- `ViT (Vision Transformer)` – Para **classificar o conteúdo visual da imagem**, como “wig” (peruca), “sombrero”, etc.
- `DETR (DEtection TRansformer)` – Para **detecção de objetos e pessoas**, com retorno de bounding boxes.

Tudo isso foi feito com `pipeline()` da biblioteca `transformers`, o que facilitou bastante o uso dos modelos prontos.

###  3. Bibliotecas Utilizadas

- **`torch`** – Framework para deep learning, responsável pelo “trabalho pesado” do ML
- **`torchvision`** – Cuida da parte de imagens e modelos visuais
- **`matplotlib`** – Usada para visualizar resultados, gráficos e imagens
- **`transformers`** – Biblioteca da Hugging Face usada para aplicar modelos prontos
- **`tensorflo`** e **`keras`** – Usadas para **construir e treinar um modelo próprio de classificação binária**
- **`PIL`**, **`shutil`**, **`requests`** – Auxiliam na manipulação de imagens, organização de pastas e requisições web



## 4. Organização de Dados e Treinamento

Foi feita a **organização de imagens** em duas pastas: `mulher-branca` e `mulher-preta`, usando o Google Drive. Depois:

- As imagens foram divididas em **80% treino e 20% validação**
- Aplicamos técnicas de **Data Augmentation** (girar, inverter, etc.)
- Criamos um modelo `Sequential` com `Conv2D`, `MaxPooling2D`, `Flatten` e camadas `Dense`
- Treinamos o modelo por 15 épocas
- Por fim, salvamos o modelo com `model.save()`



##  5. Testes com MobileNetV2 + Classificador Binário

Também foi utilizado o modelo pré-treinado **MobileNetV2** (do TensorFlow), apenas como **extrator de características**.  
A partir disso, criamos um novo modelo `Sequential` com camada de saída `sigmoid`, e testamos imagens diretamente da internet usando:

- URLs reais (de sites com imagens de mulheres pretas e brancas)
- Visualização da imagem com `matplotlib`
- Predição com retorno de probabilidades de cada classe (branca/preta)



##  Como Executar o Projeto


- Acesse o projeto no **Google Colab**
- Tenha imagens organizadas em pastas no **Google Drive**
- Conecte o Colab com seu Drive com `drive.mount('/content/drive')`


1. Instale as bibliotecas (caso necessário):

```python
!pip install torch torchvision matplotlib transformers tensorflow
```

2. Execute as células do notebook:
   - Baixe uma imagem com `!wget`
   - Aplique o pipeline para classificação e detecção
   - Monte seu Google Drive
   - Organize o dataset
   - Treine o modelo com `model.fit(...)`
   - Salve o modelo
   - Teste novas imagens via URL

3. Veja os resultados exibidos com labels e scores como:

```
🏷️ WIG                            | 📊 90.79%
🏷️ MASK                           | 📊 0.45%
```

