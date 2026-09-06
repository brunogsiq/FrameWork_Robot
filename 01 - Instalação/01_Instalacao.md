
# 🧪 Tutorial Completo de Instalação — Robot Framework

Este documento reúne todos os passos necessários para instalar e configurar o **Robot Framework**, suas bibliotecas principais, o **SeleniumLibrary**, **Browser**, ChromeDriver/ChromiumDriver e extensões no VS Code.

---

## 📌 Comentários e Material Complementar

Para outras dicas sobre Robot Framework:

   Docs - https://robotframework.org/#resources

   [https://docs.google.com/document/d/1UbOEulez9E698tb8Z68ZRFD0XPNQ19-MTlrcO-8_tRg](https://docs.google.com/document/d/1UbOEulez9E698tb8Z68ZRFD0XPNQ19-MTlrcO-8_tRg)

---

# 🚀 1. Instalando o Robot Framework

Para começar, será necessário instalar:

* **Python**
* **Robot Framework**
* **Bibliotecas principais (SeleniumLibrary, Browser, DebugLibrary)**

---

## 🟦 1.1 Instalar Python

1. Faça download do Python em:
   [https://www.python.org/downloads/](https://www.python.org/downloads/)

2. No instalador, **marque a opção**:

```
Add Python to PATH
```

⚠️ **IMPORTANTE:**
Se você esquecer de marcar essa opção, poderá adicionar o Python manualmente nas variáveis de ambiente do Windows.

---

## 🟦 1.2 Verificar instalação

Abra o **CMD** e execute:

```bash
python --version
pip --version
```

Se ambos responderem, a instalação está correta.

Observação: Caso de erro de instalação ou problea com pip, importante reinstalar e verificar se é apresentado nas variáveis de ambientes
   Comando para atualizar pip:  python.exe -m pip install --upgrade pip
---

# 📦 2. Instalando as Bibliotecas do Robot Framework

Abra o CMD e instale:

```bash
pip install robotframework
pip install robotframework-SeleniumLibrary 
pip install robotframework-DebugLibrary
pip install robotframework-Browser
pip install robotframework-Requets

ou pip install --upgrade robotframework-NomeLibrary
```

Observação: Se houver necessidade de reinstalar/atualizar o robot
   Comando para atualizar o robot: pip install -U robotframework 

### 🔍 Verificar bibliotecas instaladas

```bash
pip list
```

### 📌 Observações importantes

* Em alguns casos raros, será necessário instalar o `pip` separadamente.
* Se a versão do pip estiver desatualizada, ele mostrará o comando correto para atualização após executar qualquer `pip install`.

Exemplo:

```bash
python -m pip install --upgrade pip
```

---

# 🌐 3. Instalando o ChromeDriver / ChromiumDriver

O Selenium exige um driver para controlar o navegador.
Nesse caso, precisamos do **ChromiumDriver**.

### 🟦 3.1 Como baixar

Pesquise no navegador:

```
chromiumdriver download
```

Ou acesse:
[https://chromedriver.chromium.org/downloads](https://chromedriver.chromium.org/downloads)

### 🟦 3.2 Versão correta

⚠️ A versão do driver deve ser:

```
igual OU menor que a versão do Chrome instalada
```

Para verificar sua versão, vá em:

```
Chrome → Configurações → Sobre o Google Chrome
```

### 🟦 3.3 Após baixar

1. Descompacte o arquivo `.zip`.
2. Copie o arquivo `chromedriver.exe`.
3. Cole dentro da pasta:

```
C:\Windows\System32
```

---

# 🧰 4. Configurando o VS Code

No VS Code, instale as extensões:

* **Python**
* **Robot Framework Language Server**

Essas extensões habilitam:

* Syntax highlight
* Autocomplete
* Execução de testes
* Debug

---

# 🏃 5. Comandos Essenciais do Robot Framework

Use estes comandos no CMD para trabalhar com o Robot:

---

## 🔹 Ver ajuda geral

```bash
robot --help
```

---

## 🔹 Gerar logs e reports

```bash
robot -d ./log arquivo.robot
```

Cria uma pasta `log/` e salva os arquivos de saída lá.

---

## 🔹 Executar testes de uma TAG específica

### 1. Incluir somente uma TAG:

```bash
robot -i nome_da_tag arquivo.robot
```

### 2. Excluir uma TAG:

```bash
robot -e nome_da_tag arquivo.robot
```

---

## 🔹 Substituir uma variável somente na execução

```bash
robot -v NOME:valor arquivo.robot
```

Exemplo:

```bash
robot -v ambiente:dev teste.robot
```

Após a execução, o valor volta ao padrão definido no arquivo.

---

# 🛠️ 6. Remover warnings do ChromeDriver

No seu código Python/Selenium, use:

```python
options.add_experimental_option('excludeSwitches', ['enable-logging'])
```

Isso remove warnings desnecessários no console.