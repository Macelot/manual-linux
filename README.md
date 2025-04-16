
---

### 🔧 **Equivalentes de comandos no Linux Debian:**
Com certeza! Abaixo está a **tabela ampliada** com os comandos do Windows e seus **equivalentes no Linux (Debian)**, incluindo os comandos `echo`, `mkdir`, `color` e mais alguns comandos úteis que podem enriquecer seus roteiros de shell:

---

### 📋 **Tabela de Comandos: Windows vs Linux (Debian)**

| **Windows (CMD / BAT)** | **Linux (Debian / Bash)**     | **Descrição**                                                                 |
|--------------------------|-------------------------------|--------------------------------------------------------------------------------|
| `tracert`                | `traceroute`                  | Mostra o caminho até um site ou IP.                                           |
| `ping`                   | `ping`                        | Testa conectividade entre computadores.                                       |
| `dir`                    | `ls -l`                       | Lista arquivos e diretórios.                                                  |
| `systeminfo`             | `uname -a` + `lsb_release -a` | Mostra informações sobre sistema e kernel.                                    |
| `driverquery`            | `lshw`, `lspci`, `lsusb`      | Lista os drivers, hardware e periféricos.                                     |
| `date`                   | `date`                        | Mostra e permite alterar a data e hora.                                       |
| `time`                   | `date +"%T"`                  | Mostra a hora atual.                                                          |
| `echo`                   | `echo`                        | Exibe texto ou variável na tela.                                              |
| `mkdir`                  | `mkdir` ou `mkdir -p`         | Cria diretórios.                                                              |
| `color`                  | `tput setaf` + `tput setab`   | Altera cor do texto/fundo no terminal. (Ex: `tput setaf 1` para vermelho)     |
| `cls`                    | `clear`                       | Limpa a tela do terminal.                                                     |
| `pause`                  | `read -p "Pressione Enter..."`| Pausa a execução aguardando entrada do usuário.                               |
| `%username%`             | `$USER`                       | Nome do usuário logado.                                                       |
| `%date%`                 | `date +"%d/%m/%Y"`            | Data formatada.                                                               |
| `%time%`                 | `date +"%H:%M:%S"`            | Hora formatada.                                                               |
| `%systemroot%` ou `%windir%` | `/etc` ou `/usr`            | Diretórios de sistema no Linux.                                               |
| `%homepath%`             | `$HOME`                       | Diretório home do usuário.                                                    |
| `%systemDrive%`          | `/`                           | Unidade principal (raiz) no Linux.                                            |

---

### 💡 **Exemplo de uso do `tput` (equivalente ao `color`)**:
```bash
# Texto em vermelho
tput setaf 1
echo "Este texto está em vermelho"
tput sgr0  # Resetar para cor padrão
```

---

### 🧪 **Versão Linux dos arquivos BAT como scripts `.sh`:**

---

#### ✅ **1. q1.sh** — Salva drivers e login do usuário:
```bash
#!/bin/bash
lshw -short > q1.txt
echo $USER >> q1.txt
```

---

#### ✅ **2. q2.sh** — Salva info do sistema e pede Enter:
```bash
#!/bin/bash
clear
uname -a > q2.txt
lsb_release -a >> q2.txt
echo "Tecle <Enter> para continuar..."
read
date >> q2.txt
```

---

#### ✅ **3. q3.sh** — Salva data e hora atual sem pressionar enter:
```bash
#!/bin/bash
echo $(date +"%d/%m/%Y") > q3.txt
echo $(date +"%H:%M") >> q3.txt
```

---

#### ✅ **4. q4.sh** — Salva login do usuário e arquivos do diretório do sistema:
```bash
#!/bin/bash
echo $USER > q4.txt
ls -l /etc >> q4.txt  # Diretório com configs do sistema no Linux
```

---

#### ✅ **5. q5.sh** — Salva login e arquivos de Downloads e Desktop:
```bash
#!/bin/bash
echo $USER > q5.txt
ls -l ~/Downloads >> q5.txt
ls -l ~/Desktop >> q5.txt
```

---

#### ✅ **6. q6.sh** — Cria diretório no Desktop com login e salva IP:
```bash
#!/bin/bash
mkdir -p ~/Desktop/$USER
ip a > ~/Desktop/$USER/q6.txt
```

---

#### ✅ **7. q7.sh** — Solicita nome e dá boas-vindas:
```bash
#!/bin/bash
read -p "Digite seu nome: " nome
echo "$nome, seja bem-vindo."
```

---

#### ✅ **8. q8.sh** — Solicita nome do arquivo e grava a data:
```bash
#!/bin/bash
read -p "Digite o nome do arquivo: " nome
echo $(date +"%d/%m/%Y") > "$nome.txt"
```

---

#### ✅ **9. q9.sh** — Script com condição `if`, criação de arquivo e pasta:
```bash
#!/bin/bash
read -p "Digite 1 para criar pasta e arquivo, ou 0 para sair: " opcao

if [ "$opcao" -eq 1 ]; then
    mkdir -p ~/Desktop/teste_condicional
    echo "Arquivo criado via condição if" > ~/Desktop/teste_condicional/info.txt
    echo "Pasta e arquivo criados com sucesso."
else
    echo "Nenhuma ação foi realizada."
fi
```

---

### 🔐 **Permitir execução dos scripts:**
Para rodar os arquivos `.sh`, não esqueça de dar permissão de execução:

```bash
chmod +x q1.sh
```

E executar:

```bash
./q1.sh
```

---

## Atividade.

Teste este aquivo:
Crie ele no nano depois definia a permissão de execução:
```bash
chmod +x exemplo.sh
```

por fim execute ele:
```bash
./exemplo.sh
```

# Ativar suporte a UTF-8 para acentos
```bash
export LANG=pt_BR.UTF-8
```

# Definir cores (usando tput)
```bash
RED=$(tput setaf 1)
GREEN=$(tput setaf 2)
BLUE=$(tput setaf 4)
RESET=$(tput sgr0)
```

# Limpar tela
```bash
clear
```

# Exibir mensagem inicial
```bash
echo "${BLUE}Bem-vindo ao script de criação de diretórios e arquivos!${RESET}"
```

# Solicitar nome do usuário
```bash
read -p "Digite seu nome: " NOME
```

# Diretório de destino (Desktop)
```bash
PASTA="$HOME/Desktop/$NOME"
```

# Verificar se diretório já existe
```bash
if [ -d "$PASTA" ]; then
    echo "${RED}Atenção: o diretório '$PASTA' já existe.${RESET}"
else
    mkdir -p "$PASTA"
    echo "${GREEN}Diretório '$PASTA' criado com sucesso.${RESET}"
fi
```

# Criar arquivo com data e hora
```bash
ARQUIVO="$PASTA/info.txt"
echo "Usuário: $NOME" > "$ARQUIVO"
echo "Data: $(date +"%d/%m/%Y")" >> "$ARQUIVO"
echo "Hora: $(date +"%H:%M:%S")" >> "$ARQUIVO"
echo "${GREEN}Arquivo criado em: $ARQUIVO${RESET}"
```

# Pausa
```bash
read -p "${BLUE}Pressione ENTER para encerrar...${RESET}"
```

