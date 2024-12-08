# Babá de cachorro
Uma área é delimitada(neste caso, o pátio). E qualquer cachorro que aparece no vídeo é monitorado, assim que um cachorro sair e aparecer fora desta área, é emitido um alerta.

## Detecção de Objetos com YOLO e OpenCV

Este projeto utiliza a biblioteca OpenCV e o modelo de detecção de objetos YOLO (You Only Look Once) para identificar e monitorar objetos em vídeos. O foco principal do código é detectar um cachorro dentro de um vídeo e alertar caso ele saia de uma região delimitada.

## Funcionalidades

- **Carregamento de modelo pré-treinado:** utiliza os arquivos de configuração e pesos do YOLO para detecção de objetos.
- **Pré-processamento de frames:** ajusta os frames do vídeo para serem compatíveis com o modelo YOLO.
- **Detecção de objetos:** identifica objetos em um frame do vídeo e filtra por classe (neste caso, cachorro).
- **Alerta de fuga:** verifica se o objeto detectado (cachorro) saiu de uma região específica do frame.
- **Visualização:** desenha as detecções e a região delimitada no frame do vídeo.

## Arquivos Necessários

1. **Arquivos do modelo YOLO:**
   - `yolov3.cfg` ou `yolov3-tiny.cfg`
   - Baixe os arquivos `yolov3.weights` ou `yolov3-tiny.weights` em https://pjreddie.com/darknet/yolo
   - `coco.names`
2. **Vídeo:**
   - Um arquivo de vídeo ou uma câmera para análise das imagens.

## Bibliotecas Utilizadas

1. **OpenCV (`cv2`)**:
   - Manipulação de vídeos e imagens.
   - Criação e execução do modelo de rede neural YOLO.

2. **NumPy (`numpy`)**:
   - Operações matemáticas e manipulação de arrays para pré-processamento e detecção de objetos.

## Estrutura do Código

### 1. **Carregar Modelo Pré-treinado**
A função `carregar_modelo_pretreinado` inicializa e configura o modelo YOLO com os arquivos de configuração e pesos especificados.

### 2. **Pré-processamento de Frames**
A função `preprocessar_frame` converte um frame de vídeo em um blob para ser processado pelo modelo YOLO.

### 3. **Detecção de Objetos**
A função `detectar_objetos` utiliza o modelo YOLO para identificar objetos em um frame e retorna as detecções.

### 4. **Desenhar Detecções**
A função `desenhar_deteccoes` processa as detecções, desenha caixas delimitadoras ao redor dos objetos detectados e verifica se o objeto saiu da região delimitada.

### 5. **Função Principal**
A função `main`:
- Inicializa o modelo YOLO.
- Carrega o vídeo para análise.
- Processa cada frame para detecção de objetos.
- Exibe o vídeo com as detecções desenhadas.

## Como Executar
1. Criar o ambiente virtual:
  ```
  python -m venv env-visao
  ```
2. Ativar o ambiente virtual:
  
  No macOS e Linux:
  ```
  source ./env-visao/bin/activate
  ```
  No Windows:
  
  ```
  .\env-visao\Scripts\activate
  ```
3. Instalação de Dependências
   Certifique-se de que seu ambiente virtual esteja ativado. Instale as dependências listadas no arquivo ```requirements.txt```:
     ```
     pip install -r requirements.txt
     ```
   Conteúdo do arquivo requirements.txt:
     ```
     numpy==2.0.0
     opencv-python==4.10.0.84     ```

4. Execute o script com o comando:
   ```bash
   python nome_do_script.py
   ```
5. O vídeo processado será exibido em uma janela. Pressione `q` para sair.
6. Quando terminar de trabalhar no projeto, você pode desativar o ambiente virtual com o comando:
  ```
  deactivate
  ```

## Observações
- O alerta de fuga é acionado caso o cachorro saia da região delimitada por um polígono especificado no código.
- Ajuste os arquivos e parâmetros conforme necessário para outros casos de uso.

