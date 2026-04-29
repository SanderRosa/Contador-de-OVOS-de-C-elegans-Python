# 🔬 Contador de Ovos de *C. elegans* — Visão Computacional com Python

> Ferramenta de análise de imagem para contagem automatizada de ovos do nematódeo *Caenorhabditis elegans* usando visão computacional.

---

## 🧬 Sobre o Projeto

O *Caenorhabditis elegans* é um organismo modelo amplamente utilizado em biologia celular e genética. A contagem manual dos seus ovos em imagens microscópicas é uma tarefa tediosa e sujeita a erros. Este projeto automatiza esse processo utilizando técnicas de **Visão Computacional** com OpenCV e Python.

O script processa uma imagem microscópica e retorna:
- O **número total de ovos detectados**
- Uma **imagem anotada** com bounding boxes e centroides marcados em cada ovo

---

## ⚙️ Como Funciona

O pipeline de processamento segue as etapas:

1. **Leitura da imagem** (`Contar.jpg`)
2. **Conversão para escala de cinza**
3. **Equalização de histograma (CLAHE)** — melhora o contraste localmente
4. **Binarização adaptativa Gaussiana** — destaca os ovos do fundo
5. **Máscara circular** — remove artefatos nas bordas da imagem
6. **Remoção de ruído morfológico** (MORPH_OPEN)
7. **Contagem por componentes conectados** (`connectedComponentsWithStats`)
8. **Visualização** com Matplotlib mostrando o threshold e os ovos detectados

---

## 🛠️ Tecnologias

| Biblioteca | Uso |
|---|---|
| `OpenCV` (`cv2`) | Processamento de imagem |
| `NumPy` | Operações matriciais |
| `Matplotlib` | Visualização dos resultados |

---

## 🚀 Como Usar

### 1. Instalar dependências
```bash
pip install opencv-python numpy matplotlib
```

### 2. Colocar sua imagem
Coloque a imagem a ser analisada na pasta do projeto com o nome `Contar.jpg` (ou ajuste o caminho no código).

### 3. Executar
```bash
python Bublle.py
```

### 4. Resultado
O script imprime no terminal:
```
✅ Quantidade de pontinhos encontrados: <N>
```
E abre uma janela com a imagem do threshold e os ovos detectados marcados.

---

## 📁 Estrutura
```
Contador de OVOS de C. elegans - Python/
├── Bublle.py       # Script principal de detecção
└── Contar.jpg      # Imagem microscópica de entrada
```

---

## 📌 Observações

- O algoritmo é sensível ao contraste da imagem. Caso os resultados sejam imprecisos, ajuste os parâmetros do `adaptiveThreshold` (block size e constante C).
- Projetado para imagens em campo claro (bright-field) com ovos ovais e escuros sobre fundo claro.
