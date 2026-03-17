# SQUID CONFIGURAÇÃO 
PASSO A PASSO PARA CONFIGURAÇÃO DO SQUID NO WINDOWS 11

C:\squid
     
│
├── bin
├── etc
├── libexec
├── sbin
├── share
├── var

Estrutura básica.

### 1️⃣ `bin`

Contém executáveis principais.

### 2️⃣ `etc` ⭐ (uma das mais importantes)

Aqui ficam **os arquivos de configuração**.

---

### 3️⃣ `libexec`

Arquivos auxiliares usados pelo Squid.

### 4️⃣ `sbin`

Executáveis administrativos.

---

### 5️⃣ `share`

Arquivos auxiliares e de suporte.

### 6️⃣ `var` ⭐ (muito importante)

Aqui ficam **logs e cache**.

---

## 1. PASSO

Criar as pastas cache e logs dentro da pasta var.

![image.png](attachment:92002120-e854-4317-8abb-d540f8999123:image.png)

---

## 2. PASSO

Utilizando o bloco de notas você deve criar o arquivo squid.conf dentro da pasta **etc.**

Depois crie o arquivo mimo.conf também na pasta **etc.**

![image.png](attachment:e2fbd98f-2e82-4620-a3e1-3634948807d2:image.png)

![image.png](attachment:c205e482-d8d3-4a8f-a6c6-ed4814f0fb8b:image.png)

### Conteúdo do arquivo squid.config

### Conteúdo do arquivo mimo.config

![image.png](attachment:9ce5b930-1cb0-4790-8e02-2ecd694b54b2:image.png)

> EXPLICAÇÃO LINHA A LINHA
> 
1. O Squid vai **escutar conexões HTTP** na porta **3128**.
2. Define o **nome do servidor proxy**.
3. Cria uma acl chamada all (TODOS OS IPS).
4. Cria uma acl chamada rede_local com ip da rede.
5. Regra de acesso http_access allow.
6. Regra de bloqueio html_access deny.
7. Define onde o squid guarda o conteúdo cacheado da internet.
    
    Ufs = tipo de sistema de cache
    
    100 = tamanho de cache em MB
    
    16 = número de diretórios de primeiro nível
    
    256 = número de diretórios de segundo nível
    
8. Define onde salvar o log de acesso dos usuários.
9. Define o log interno do Squid.

![image.png](attachment:0d07e4a3-a298-41b5-ac5c-b5228213df17:image.png)

---

## 3. PASSO

Se as pastas cache e log não existirem, você deve criar.

![image.png](attachment:ec2154f5-a5ad-498e-8499-544d20447667:image.png)

---

## 4. PASSO

Abra **Prompt como administrador** e rode:

![image.png](attachment:10339b1b-5354-4cbc-94c7-b6774a01076c:image.png)

Se der certo aparecerá a mensagem: 

![image.png](attachment:f8dc2661-42dc-4752-8d2f-2b079704c574:image.png)

---

## 5. PASSO

Agora execute o squid.

![image.png](attachment:447688e2-e4dc-440e-825e-60174ca2b6c4:image.png)

---

## 6. PASSO

No computador cliente. Versão Windows 11.

Configurações → Rede e Internet → Proxy → Desative Detectar configurações automaticamente.

Configuração de Proxy manual → Usar um servidor proxy → Configurar → Ative a opção Usar um servidor proxy.

Em Endereço IP do proxy insira nome da máquina servidor exemplo ECE334M33SN1 → Porta: 3128.

![image.png](attachment:1f73ba9d-551d-40af-8be7-18f4c3751b93:image.png)

![image.png](attachment:a63b1aed-3a9b-4065-aad0-bd1f2a92a57f:image.png)

---

## 7. PASSO

Crie o arquivo sites_bloqueados.txt dentro da pasta Squid.

![image.png](attachment:556abaac-a53e-46a7-ba0d-e8d0bed981f5:image.png)

O arquivo sites_bloqueados.txt deve conter a lista de sites que serão bloqueados.

dstdomain "c:/squid/sites_bloqueados.txt bloqueia todos as extensões do site.

dstdomain = domínio de destino

![image.png](attachment:28caeb54-4843-4c10-ab12-2f1e4935db18:image.png)

---

## 8. PASSO

Acessar gpedit.msc como Administrador.

![image.png](attachment:e438ab27-2b7b-4737-bcf3-95e1e7e8c012:image.png)

Configuração do Usuário 

→ Modelos Administrativos 

→ Painel de Controle

→ Proibir acesso ao painel de Controle e às configurações do PC

→ Visibilidade da Página de Configurações

![image.png](attachment:493d9040-7921-4947-a6d2-1f35cdf66071:image.png)

![image.png](attachment:3b8e8fca-22c9-4cf5-b366-aef0601b7469:image.png)

---

## 9. PASSO

![image.png](attachment:729b54a9-29e9-401a-accc-e8499639b498:image.png)

O arquivo sites_bloqueados.txt tem todos os sites bloqueados.

Para bloquear um site você deve inserir seu domínio exemplo: 

.facebook.com

.instagram.com

Para comentários dentro do arquivo sites_bloqueados.txt você deve utilizar # no inicio da linha.

O Computador servidor  deve clicar em INICIAR SQUID toda vez que for ligado.

Caso algum problema aconteça clicar em PAUSAR SQUID e depois em INICIAR SQUID.

O Reconfigurar deve ser rodado toda vez que você fizer alguma alteração no arquivo sites_bloqueados.txt
