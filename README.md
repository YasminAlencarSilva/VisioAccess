# SENAI Cam Access
### Sistema de Controle de Acesso por Reconhecimento Facial

## Sobre o Projeto

O SENAI Cam Access é um sistema de controle de acesso por reconhecimento facial em tempo real, desenvolvido com o objetivo de aplicar conhecimentos de desenvolvimento web, inteligência artificial, visão computacional e banco de dados na construção de uma solução tecnológica.

A aplicação utiliza a webcam para capturar imagens, detectar rostos e extrair descritores faciais por meio da biblioteca face-api.js. Os dados obtidos são comparados com os registros armazenados no Supabase, permitindo identificar usuários previamente cadastrados e apresentar o resultado do reconhecimento.

A interface foi desenvolvida com foco em usabilidade, responsividade e identidade visual inspirada no padrão institucional do SENAI.

## Objetivo

Desenvolver uma solução capaz de realizar a identificação de usuários por reconhecimento facial, integrando tecnologias web, processamento de imagens e armazenamento de dados em nuvem.

Durante o desenvolvimento, foram aplicados conhecimentos de:

- Desenvolvimento de interfaces com HTML5 e CSS3.
- Programação e manipulação do DOM com JavaScript.
- Integração com banco de dados em nuvem.
- Inteligência artificial e visão computacional.
- Captura e processamento de imagens em tempo real.
- Desenvolvimento colaborativo de software.

## Funcionalidades

- **Captura de vídeo em tempo real:** utilização da webcam para monitoramento e identificação facial.
- **Detecção facial:** identificação de rostos presentes na imagem capturada.
- **Reconhecimento facial:** extração e comparação de descritores faciais.
- **Controle de acesso:** identificação de usuários cadastrados e apresentação do resultado da verificação.
- **Identificação de usuários:** exibição de nome, matrícula e curso ou cargo.
- **Cadastro de usuários:** formulário para registrar informações pessoais e dados biométricos.
- **Integração com banco de dados:** consulta e armazenamento de registros por meio do Supabase.
- **Interface responsiva:** layout adaptável com identidade visual inspirada no SENAI.

## Tecnologias Utilizadas

| Tecnologia | Finalidade |
|---|---|
| HTML5 | Estruturação da aplicação |
| CSS3 | Estilização e responsividade |
| JavaScript ES6+ | Lógica e funcionalidades do sistema |
| face-api.js | Detecção e reconhecimento facial |
| TensorFlow.js | Execução dos modelos de inteligência artificial |
| Supabase | Banco de dados e persistência de informações |
| Font Awesome | Biblioteca de ícones |

## Reconhecimento Facial

O sistema utiliza a biblioteca face-api.js, construída sobre TensorFlow.js, para realizar o processamento facial diretamente no navegador.

São utilizados três modelos principais:

**Tiny Face Detector:** responsável pela detecção de rostos nas imagens capturadas pela webcam.

**Face Landmark 68 Net:** identifica 68 pontos de referência facial, permitindo mapear características do rosto.

**Face Recognition Net:** realiza a extração de descritores faciais, utilizados na comparação entre os rostos capturados e os registros cadastrados.

Os descritores faciais são armazenados no Supabase e utilizados no processo de identificação dos usuários.

## Banco de Dados

O Supabase é utilizado como solução de armazenamento e consulta das informações dos usuários cadastrados.

A tabela principal do projeto é denominada `usuarios` e possui os seguintes campos:

| Campo | Tipo | Descrição |
|---|---|---|
| id | BIGSERIAL | Identificador único |
| created_at | TIMESTAMPTZ | Data de criação do registro |
| nome | TEXT | Nome do usuário |
| matricula | TEXT | Matrícula institucional |
| curso | TEXT | Curso ou cargo |
| descriptor | JSONB | Dados numéricos do descritor facial |

### Estrutura SQL

```sql
CREATE TABLE usuarios (
    id BIGSERIAL PRIMARY KEY,
    created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
    nome TEXT NOT NULL,
    matricula TEXT NOT NULL,
    curso TEXT NOT NULL,
    descriptor JSONB NOT NULL
);
```

**Segurança:** para utilização em ambiente real, é necessário configurar políticas de segurança RLS, restringir permissões de acesso e proteger as credenciais da aplicação. Os dados biométricos devem ser tratados conforme os requisitos da LGPD.

## Como Executar o Projeto

### Pré-requisitos

- Navegador atualizado com suporte à webcam.
- Visual Studio Code ou outro editor de código.
- Extensão Live Server ou Python instalado.
- Projeto configurado no Supabase.

### 1. Clonar o repositório

```bash
git clone https://github.com/YasminAlencarSilva/VisioAccess.git
```

### 2. Acessar a pasta

```bash
cd VisioAccess
```

### 3. Configurar o Supabase

- Criar um projeto no Supabase.
- Executar o script SQL apresentado na seção Banco de Dados.
- Configurar as credenciais e a integração conforme a implementação do arquivo `script.js`.
- Configurar as políticas de acesso necessárias.

### 4. Iniciar o servidor local

Com Python:

```bash
python -m http.server 8000
```

Ou utilizando a extensão Live Server no Visual Studio Code.

### 5. Acessar a aplicação

```text
http://localhost:8000
```

Após abrir a aplicação, autorize o acesso à webcam para iniciar o processo de reconhecimento facial.

## Estrutura do Projeto

```text
VisioAccess/
│
├── index.html
├── style.css
├── script.js
├── README.md
│
└── models/
    ├── face_landmark_68_model-shard1
    ├── face_landmark_68_model-weights_manifest.json
    ├── face_recognition_model-shard1
    ├── face_recognition_model-shard2
    ├── face_recognition_model-weights_manifest.json
    ├── tiny_face_detector_model-shard1
    └── tiny_face_detector_model-weights_manifest.json
```


