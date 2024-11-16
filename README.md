# Annif-Install
Instalação do Annif

A instalação do Annif pode ser realizada seguindo os passos descritos no guia. Aqui está um resumo detalhado:

---

### **Requisitos**
1. **Sistema Operacional**:
   - Preferencialmente Linux. Em outros sistemas (Windows/MacOS), use Docker ou uma máquina virtual Linux.
2. **Versão do Python**:
   - Compatível com Python 3.9 a 3.12. Confirme a versão instalada:
     ```bash
     python3 -V
     ```

---

### **Passos para instalação**

#### 1. **Preparar o ambiente**
   - Certifique-se de ter suporte para ambientes virtuais no Python. No Ubuntu, instale o pacote necessário:
     ```bash
     sudo apt install python3-venv
     ```

   - Crie um ambiente virtual:
     ```bash
     python3 -m venv annif-venv
     ```

   - Ative o ambiente virtual:
     ```bash
     source annif-venv/bin/activate
     ```

---

#### 2. **Atualizar ferramentas**
   - Atualize o `pip` e instale o utilitário `wheel`:
     ```bash
     pip install -U pip wheel
     ```

---

#### 3. **Instalar o Annif**
   - Instale o Annif:
     ```bash
     pip install annif
     ```

   - Baixe o modelo **punkt** do NLTK:
     ```bash
     python -m nltk.downloader punkt
     ```

   - Instale dependências opcionais conforme necessário:
     ```bash
     pip install annif[omikuji] annif[fasttext] annif[nn]
     ```

---

#### 4. **Habilitar autocompletar no terminal**
   - Para o **bash**, habilite o suporte à conclusão automática:
     ```bash
     source <(annif completion --bash)
     ```

   - Para habilitar o suporte de conclusão em todas as novas sessões, primeiro adicione o script de conclusão em Seu diretório inicial `~/.bashrc`:
     ```bash
     annif completion --bash > ~/.annif-complete.bash
     ```

 - Em seguida, faça com que o script seja originado automaticamente para novas sessões de terminal adicionando o seguindo para o seu arquivo: `~/.bashrc`:
     ```bash
     source ~/.annif-complete.bash
     ```

---

### **Testar a instalação**
- Verifique se o Annif está instalado:
  ```bash
  annif
  ```

- Para iniciar o aplicativo:
  ```bash
  annif run --host 0.0.0.0
  ```

### **Tornar o ambiente virtual permanente (opcional)**
- Se quiser que o Annif inicie automaticamente no ambiente virtual ao ligar o servidor:
1. Crie um script bash para ativar o ambiente e iniciar o Annif:
   ```bash
   #!/bin/bash
   source ~/annif-venv/bin/activate
   annif run --host 0.0.0.0
   ```
2. Torne o script executável:
   ```bash
   chmod +x iniciar_annif.sh
   ```

3. Configure um serviço systemd para garantir que o Annif seja executado automaticamente.
