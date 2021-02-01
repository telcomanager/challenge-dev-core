# Telcomanager core development challenge

## Descrição

Esse desafio faz parte do processo seletivo da Telcomanager para a vaga de Desenvolvedor de Software - Backend / Core e com ele poderemos avaliar melhor seu perfil em relação à vaga. O desafio consiste em desenvolver uma aplicação cliente/servidor na qual serão avaliados a completude da solução, qualidade e organização de código e seu conhecimento de estrutura de dados e de protocolos de rede.

Este projeto deve ser desenvolvido na linguagem C e para um sistema operacional baseado em kernel Linux.

Este projeto é divido em 2 partes: cliente e servidor.



### Servidor

O servidor deverá prover ao cliente dados requisitados por ele, atendendo a um protocolo pré definido. Ele deverá funcionar como um daemon (estar sempre disponível) e escutando requisições TCP na porta 50080.

Ele deve manter em memória uma lista de nomes de clientes e em qual diretório se encontram os dados de cada um.

O cliente será identificado (ID) por caracteres alfanuméricos.

O servidor deve prover:

1) Lista dos arquivos e seus tamanhos do cliente, em ordem alfabética ou por tamanho;
2) Download do arquivo pro cliente;
3) Upload de novos arquivos;


### Cliente

O cliente abrirá uma comunicação com o servidor atendendo ao protocolo definido. Ele deve se identificar e executar as operações de escrita e leitura. Ele só deverá desconectar se for enviado um comando para finalizar a comunicação.

Criar um comando no cliente para exibir as possíveis operações disponíveis.


### Protocolo

A comunicação entre o cliente e o servidor deverá seguir o seguinte protocolo. As linhas que começam com 'S' representam o servidor e as que começam com 'C' o cliente.

- C: hello
- S: hello
- C: **client_id**
- S: **client_status**
- C: **command**
- S: **command status**

Para o cliente iniciar a comunicação com o servidor ele deverá se conectar na porta 50080 usando o protocolo TCP e mandar um texto "hello".

O servidor responderá hello de volta indicando que a conexão foi aceita.

O cliente enviará em seguida o seu ID e o servidor buscará se existe esse cliente na sua base em memória. Caso exista retornar o texto "OOK". Caso contrário retornar "NOK" e fechar a conexão.

Com a conexão aceita, enviar o comando de requisição ou listar as opções disponíveis. Opções:

1. help: lista opções de comando disponíveis
2. list <opção de ordenação> <asc/desc>: as opções de ordenação são 'name' e 'size'
3. send <file>: enviar um arquivo no path 'file'
4. get <file>: recuperar o arquivo com o nome 'file'
5. exit

O comando **help** não precisa ser enviado ao servidor, funcionará localmente.

Para o comando **list** o servidor deve retornar "OOK" ou "NOK". Caso seja "OOK", retornar também o tamanho em bytes da resposta e a lista de arquivos como descrito. A lista deverá ser impressa na tela.

Para o comando de **send**, o servidor deve retornar: "OOK" ou "NOK". Caso seja "OOK", salvar o arquivo no diretório do cliente que fez a requisição. 

Para o comando de **get**, o servidor deve retornar: "OOK" ou "NOK". Caso seja "OOK", retornar o tamanho em bytes do arquivo e em seguida conteúdo do arquivo.

O comando exit deverá fechar a comunicação com o servidor e encerrar o cliente.

Para todos os casos que a resposta for "NOK", retornar o tamanho em bytes da resposta e o conteúdo da resposta (motivo do "NOK") e imprimir na tela.

## Instruções para entrega do projeto

- O projeto deverá ser feito usando linguagem de programação C para ambiente Linux.
- A entrega deve ter instruções de como executar o projeto para ser testado
- Você será avaliado pela qualidade do código, modularização e organização.
- Não economize na usabilidade.
- Desenvolva e use Git para versionamento do código
- Qualquer dúvida sobre esse projeto podem ser perguntadas por email em github@telcomanager.com
