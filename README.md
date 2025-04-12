Claro! Abaixo segue a **versão equivalente dos comandos e scripts do Windows (BAT)** adaptados para **Linux Debian**, utilizando **bash scripts** (arquivos `.sh`):

---

### 🔧 **Equivalentes de comandos no Linux Debian:**

| Windows         | Linux (Debian)                    | Descrição |
|----------------|------------------------------------|----------|
| `tracert`       | `traceroute`                      | Mostra o caminho até um site. |
| `ping`          | `ping`                            | Mostra a conexão com outro host. |
| `dir`           | `ls -l`                           | Lista arquivos e diretórios. |
| `systeminfo`    | `neofetch` ou `inxi -F` ou `uname -a` + `lsb_release -a` + `free -h` | Informações do sistema. |
| `driverquery`   | `lshw` ou `lspci`                  | Lista de hardware e drivers. |
| `date`          | `date`                            | Mostra e define a data. |
| `time`          | `date`                            | Também exibe a hora. Use `date +%T` para hora. |

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

Se quiser, posso empacotar todos esses scripts prontos em um `.zip` ou `.tar.gz`. Deseja isso?
