📄 README.md atualizado
 
# 🖼️ Conversor de PDFs para Imagens com Suporte ao Label Studio

Este projeto converte **milhares de PDFs** em imagens `.jpg`, com estrutura organizada e performance otimizada.  
Ideal para workflows que envolvem **marcação/anotação de certificados digitais** usando o [Label Studio](https://labelstud.io).

---

## ⚙️ Funcionalidades

- ✅ Processa +2000 PDFs com paralelismo (uso de múltiplos núcleos)
- ✅ Gera imagens `.jpg` por página, organizadas em pastas
- ✅ Evita reconversões (não processa PDFs já convertidos)
- ✅ Exporta CSV com caminhos das imagens para o Label Studio
- ✅ Estrutura modular (`main.py`, `utils.py`, `settings.py`)

---

## 🗂️ Estrutura do Projeto

pdf_para_imagem/
├── src/
│ ├── main.py # Script principal (conversão paralela)
│ ├── utils.py # Funções de conversão
│ ├── settings.py # Caminhos e configurações
│ └── export_csv.py # Exporta CSV com caminhos das imagens
├── pdfs/ # PDFs originais (entrada)
├── imagens_pdf/ # Resultado (uma pasta por PDF)
├── dataset_imagens.csv # Arquivo gerado para importar no Label Studio
├── .gitignore
├── README.md
└── venv/

## 🛠️ Requisitos

- Python 3.10+
- Poppler instalado no Windows
- pacotes `pdf2image` e `pillow`

 
pip install pdf2image pillow
🚀 Como usar
Coloque os arquivos .pdf na pasta pdfs/

Execute a conversão:

python src/main.py
Para gerar o CSV com todos os caminhos das imagens:


python src/export_csv.py
🧠 Integração com Label Studio
Após rodar export_csv.py, você terá um arquivo chamado:
 
dataset_imagens.csv
📥 Importar no Label Studio:
Crie um novo projeto

Escolha "Import from CSV"

Use o campo image_path

Use esta interface XML:

xml
 
<View>
  <Image name="image" value="$image_path" zoom="true" rotateControl="true"/>
  <RectangleLabels name="label" toName="image">
    <Label value="Assinatura Digital" background="green"/>
    <Label value="Carimbo" background="blue"/>
    <Label value="Selo" background="orange"/>
    <Label value="Outro" background="gray"/>
  </RectangleLabels>
</View>
📤 Exportação para treinamento
Após a anotação, você poderá exportar as marcações como:

JSON

COCO

Pascal VOC

YOLO

Ideal para treinar modelos de IA que reconhecem certificados, assinaturas ou elementos gráficos.

🧑‍💻 Autor
Projeto desenvolvido por @mirellaoliveiraa com ❤️
Colaborações são bem-vindas!

