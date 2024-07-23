# [Titulo do seu projeto]

> Conectando projeto web com banco de dados Postgresql"

[![Author](https://img.shields.io/badge/author-jotafin-ff9000?style=flat-square)](https://github.com/jotafin)[![Languages](https://img.shields.io/github/languages/count/jotafin/conexaodb?color=%23ff9000&style=flat-square)](#)[![Stars](https://img.shields.io/github/stars/jotafin/conexaodb?color=ff9000&style=flat-square)](https://github.com/jotafin/conexaodb/stargazers)[![Forks](https://img.shields.io/github/forks/jotafin/conexaodb?color=%23ff9000&style=flat-square)](https://github.com/jotafin/conexaodb/network/members)[![Contributors](https://img.shields.io/github/contributors/jotafin/conexaodb?color=ff9000&style=flat-square)](https://github.com/jotafin/conexaodb/graphs/contributors)


<br />

# :rocket: Passo 1: Configuração do Ambiente
Instalação do PostgreSQL:

Instale o PostgreSQL no seu sistema operacional. Você pode baixá-lo e seguir as instruções de instalação no site oficial do PostgreSQL: https://www.postgresql.org/download/.


# :framed_picture: Configuração do Banco de Dados:

Após a instalação, crie um banco de dados e uma tabela para armazenar os veículos. Por exemplo:

CREATE DATABASE nomedobanco;
\c nomedobanco;
CREATE TABLE veiculos (
    id SERIAL PRIMARY KEY,
    marca VARCHAR(100),
    modelo VARCHAR(100),
    ano INT
);

<p align="left">
<!-- <img src="src/images/mockup.png" /> -->
</p>

# :construction_worker: Passo 2: Desenvolvimento do Backend com Node.js e Express
- Instalação do Node.js:

Instale o Node.js no seu sistema. Você pode baixá-lo em https://nodejs.org/ e seguir as instruções.

- Inicialização do Projeto:

Crie um novo diretório para o seu projeto e inicialize um projeto Node.js:

mkdir meu-projeto
cd meu-projeto
npm init -y

- Instalação de Dependências:

Instale os pacotes necessários:

npm install express pg


# :runner: Configuração do Servidor Express:

- Crie um arquivo index.js para configurar o servidor Express e conectar ao PostgreSQL




# :postbox: Passo 3: Desenvolvimento do Frontend com HTML, CSS e JavaScript
- Estrutura do Frontend:

Crie arquivos HTML para a interface do usuário (index.html, cadastro.html, consulta.html).

- Interação com o Backend via JavaScript:

Utilize JavaScript (usando fetch ou XMLHttpRequest) para enviar dados do formulário de cadastro para o backend e para exibir os dados consultados.


# :bug: Passo 4: Testando e Executando o Projeto
- Execução do Servidor:

Execute o servidor Node.js com o comando:

node index.js

- Abra o navegador e vá para `http://localhost:3000`.




# :rocket: Passo 1: INTEGRANDO COM ELECTRON

- Instale o electron através do comando:

npm install --save-dev electron


- Configure o package.jason

{
  "name": "hoje",
  "version": "1.0.0",
  "description": "",
  "main": "main.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "electron ."
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.19.2",
    "pg": "^8.12.0"
  },
  "devDependencies": {
    "electron": "^31.2.1"
  }
}

- Configure o main.js para inicializar 
Consultar a documentação do electron

- Função para iniciar o servidor Node.js (adicionar junto ao main.js):

// Função para iniciar o servidor Node.js
function startServer() {
    const serverProcess = spawn('node', ['index.js']); //arquivo que foi configura o banco de dados

    serverProcess.stdout.on('data', (data) => {
        console.log(`Servidor Node.js: ${data}`);
    });

    serverProcess.stderr.on('data', (data) => {
        console.error(`Erro no servidor Node.js: ${data}`);
    });

    serverProcess.on('close', (code) => {
        console.log(`Servidor Node.js encerrado com código ${code}`);
    });

    return serverProcess;
}

- Configurar o electron para abrir no servidor node:

function createWindow () {
  const win = new BrowserWindow({
    width: 800,
    height: 600,
    webPreferences: {
      preload: path.join(__dirname, 'preload.js')
    }
  })

  win.loadURL('http://localhost:3000') //link do servidor do node
}

app.whenReady().then(() => {
    //inicializando o servidor node
    const serverProcess = startServer();
  createWindow()

  app.on('activate', () => {
    if (BrowserWindow.getAllWindows().length === 0) {
      createWindow()
    }
  })
  // Encerra o servidor Node.js quando o Electron for fechado
  app.on('before-quit', () => {
    serverProcess.kill();
});
# :rocket: Passo 2: EXECUTANDO COM ELECTRON
- Certifique-se de que todas as dependências estejam instaladas:
npm install electron express pg

-Execute o electron
npm start


# :closed_book: Licença
Lançado em 2024.
Este projeto esta sob a licença [MIT license](https://github.com/NomeDeUsuario/NomeRepositorio/master/LICENSE).

Se você tiver alguma dúvida ou sugestão, entre em contato atravésdo email: [seu-email@example.com](mailto:seu-email@example.com).