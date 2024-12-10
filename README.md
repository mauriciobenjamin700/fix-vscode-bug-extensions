# Tutorial de como Resolver Erros de Extensão e Bugs no VS Code pelo Ubuntu 24.04 LTS pelo Snap (Loja do ubuntu e gerenciador de pacotes)

Este tutorial explica como desinstalar o VS Code instalado via **Snap**, limpar o cache e reinstalá-lo do zero no Ubuntu.

---

## 1. Verifique se o VS Code está Instalado como Snap

Execute o comando abaixo para verificar se o VS Code está instalado como Snap:

```bash
snap list
```

Se o `code` aparecer na lista, significa que ele foi instalado como Snap.

---

## 2. Feche o VS Code

Antes de continuar, certifique-se de que o VS Code está fechado.

---

## 3. Remova o VS Code (Snap)

Para desinstalar o VS Code, execute:

```bash
sudo snap remove code
```

Se aparecer uma mensagem como esta:

```bash
Save data of snap "code" in automatic snapshot set #2
```

Isso significa que o Snap salvou um **snapshot** dos dados do VS Code para backup automático.

---

## 4. Remova Snapshots do VS Code (Opcional)

Se você não quiser manter os backups criados pelo Snap, siga estes passos:

1. **Liste os Snapshots Criados**:

   ```bash
   sudo snap saved
   ```

   Você verá uma saída semelhante a:

   ```bash
   ID  | Nome | Revisão | Data
   ----|------|---------|----------------
   2   | code | 123     | 2024-12-10T10:00:00Z
   ```

2. **Remova o Snapshot do VS Code**:

   Substitua `<ID>` pelo número do snapshot (neste caso, `2`):

   ```bash
   sudo snap forget <ID>
   ```

   Exemplo:

   ```bash
   sudo snap forget 2
   ```

---

## 5. Limpe Configurações e Cache do VS Code

Mesmo após remover o Snap, as configurações e caches do VS Code podem permanecer no sistema. Para limpar tudo, execute:

```bash
rm -rf ~/.config/Code
rm -rf ~/.vscode
rm -rf ~/.cache/Code
```

Se quiser verificar outros arquivos relacionados ao VS Code, use:

```bash
find ~ -name "*Code*" -exec rm -rf {} +
```

---

## 6. Reinstale o VS Code

Você pode reinstalar o VS Code usando um dos métodos abaixo:

### Método 1: Via Snap

Se prefere usar o Snap novamente, execute:

```bash
sudo snap install code --classic
```

### Método 2: Via Pacote `.deb`

1. Baixe o arquivo `.deb` do site oficial do VS Code:
   - [VS Code para Linux](https://code.visualstudio.com/Download)

2. Instale o pacote `.deb` com os comandos:

   ```bash
   sudo dpkg -i <nome_do_arquivo>.deb
   sudo apt-get install -f
   ```

---

## 7. Reinstale Suas Extensões (Opcional)

Após reinstalar o VS Code, você pode configurar novamente as extensões que utiliza:

- Use a interface do VS Code para instalar as extensões desejadas.
- Se tiver sincronização ativada, suas extensões e configurações serão restauradas automaticamente.
