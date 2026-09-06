## 1. Introdução & Visão Geral

### O que é o Robot Framework

* É um framework de automação de testes baseado em Python, orientado por palavras-chave (keyword-driven). ([robotframework.org][1])
* Suporta testes de aceitação (ATDD), BDD e automação de processos robóticos (RPA). ([robotframework.org][1])
* Ambiente independente da plataforma e da aplicação: você pode testar aplicações web, APIs, mobile, telnet/SSH, etc. ([robotframework.org][2])
* A sintaxe de dados de teste é tabular, simples de editar, versionar e integrar com CI/CD. ([robotframework.org][3])

### Por que usar

* Permite criar keywords reutilizáveis a partir de keywords existentes. ([robotframework.org][1])
* Geração automática de relatórios e logs em HTML. ([robotframework.org][2])
* Integração fácil com controle de versão — os testes são arquivos e pastas como qualquer código. ([robotframework.org][3])
* Modularidade: o núcleo (“core”) não conhece detalhes da aplicação; a interação é feita via bibliotecas. ([robotframework.org][1])

### Arquitetura de alto nível

* O fluxo típico: dados de teste (tabulares) → motor do Robot Framework → execução dos testes → geração de logs/reports. ([robotframework.org][2])
* O núcleo do framework tem uma camada de abstração, e todas as interações concretas com o sistema sob teste são feitas via bibliotecas. ([robotframework.org][3])

---

## 2. Instalação & Pré-requisitos

* O Robot Framework requer Python ou sua alternativa PyPy. ([robotframework.org][2])
* Instalação típica com `pip install robotframework`. ([robotframework.org][2])
* Em versões mais antigas/complexas pode haver configurações específicas para ambientes virtuais, Windows etc. ([robotframework.org][4])

---

## 3. Sintaxe de Testes & Estrutura Básica

Embora a documentação completa detalhe muitos aspectos, aqui seguem os pontos-chave:

### Seções principais de um arquivo `.robot`

* `*** Settings ***` → Configurações gerais (bibliotecas, recursos, variáveis)
* `*** Variables ***` → Definição de variáveis reutilizáveis
* `*** Test Cases ***` → Casos de teste propriamente ditos
* `*** Keywords ***` → Palavras-chave definidas pelo usuário
  (Confira exemplos na documentação do User Guide)

### Sintaxe keyword-driven

* Cada passo dentro de um caso de teste invoca uma keyword.
* Argumentos são geralmente separados por dois ou mais espaços.
* Variáveis são definidas com `${VARIAVEL}`.
* A estrutura torna os testes legíveis, quase em linguagem natural.

### Exemplos básicos

```robot
*** Test Cases ***
Hello world test
    Log    Hello world
```

A keyword `Log` já vem na biblioteca padrão.

---

## 4. Bibliotecas Padrão (Standard Libraries)

Estas bibliotecas são distribuídas junto com o Robot Framework e fornecem funcionalidades comuns. ([docs.robotframework.org][5])
Aqui vai uma síntese das mais usadas:

| Biblioteca      | Descrição                                                                                        |
| --------------- | ------------------------------------------------------------------------------------------------ |
| **BuiltIn**     | Keywords genéricas sempre disponíveis, pois importada automaticamente. ([robotframework.org][6]) |
| Collections     | Manipulação de listas e dicionários. ([docs.robotframework.org][5])                              |
| DateTime        | Criação, verificação e cálculos com datas/horas. ([docs.robotframework.org][5])                  |
| Dialogs         | Pausa de execução e entrada de usuário. ([docs.robotframework.org][5])                           |
| OperatingSystem | Ações no sistema operacional (arquivos, diretórios etc.). ([docs.robotframework.org][5])         |
| Process         | Execução de processos externos, captura de saída. ([docs.robotframework.org][5])                 |
| Remote          | Interface para bibliotecas remotas (não keywords próprias). ([docs.robotframework.org][5])       |
| Screenshot      | Captura de telas da área de trabalho. ([docs.robotframework.org][5])                             |
| String          | Manipulação de strings/textos. ([docs.robotframework.org][5])                                    |
| Telnet          | Conexão a servidores Telnet, execução de comandos. ([docs.robotframework.org][5])                |
| XML             | Verificação e modificação de documentos XML. ([docs.robotframework.org][5])                      |

### Importação de uma biblioteca

Por exemplo, para usar a Collections em seu arquivo de testes:

```robot
*** Settings ***
Library    Collections
```

Isso torna disponíveis os keywords da biblioteca Collections. ([docs.robotframework.org][5])

---

## 5. Ferramentas Internas (Built-in Tools)

Além do mecanismo de execução de testes, o Robot Framework oferece ferramentas para documentação, relatório e manutenção. ▸ Principais:

* **Rebot** → Gera logs, relatórios HTML a partir dos arquivos de saída XML. Usuário: combinar múltiplos outputs ou produzir relatórios finais.
* **Libdoc** → Gera documentação de keywords para bibliotecas ou arquivos resource.
* **Testdoc** → Gera documentação HTML de alto nível com base em casos de teste.
* **Tidy** → Ferramenta para limpezas, formatações, padronização de arquivos de teste.
  Essas ferramentas são listadas na página oficial de documentação. ([robotframework.org][7])

---

## 6. Extensão / Bibliotecas Personalizadas

Você pode estender o Robot Framework criando suas próprias bibliotecas, por exemplo em Python. Veja os pontos importantes:

* Bibliotecas estáticas: definidas como funções Python ou classes com métodos que se tornam keywords. ([docs.robotframework.org][8])
* Você pode criar também “non-Python libraries” ou usar a interface Remote.
* Isso é ideal se sua equipe já tem lógica de negócio ou utilitários que gostaria de reutilizar como keywords.

---

## 7. Boas Práticas & Dicas para QA

Para você que está atuando como Engenheiro(a) de Qualidade, algumas dicas aplicáveis:

* Mantenha seus casos de teste legíveis: a sintaxe tabular do Robot ajuda, mas vale aplicar boas práticas de nomenclatura de keywords, modularização (Keywords definidas em `*** Keywords ***` ou em arquivos Resource).
* Use **variáveis** para evitar repetição: por exemplo `${URL_PRD}`, `${USUARIO}`, `${SENHA}`.
* Categorize casos usando **tags** (ex: `@smoke`, `@regression`, `@critical`) para facilitar execução seletiva.
* Use bibliotecas padrão quando possível antes de buscar bibliotecas externas: ajuda na manutenção e independência de versão.
* Gere relatórios e logs automaticamente: os relatórios HTML são um diferencial para apresentação de resultados.
* Integre com CI/CD: como os testes são arquivos versionados, ficam bem para pipelines automatizados.
* Documente suas keywords personalizadas e mantenha padronização: isso ajuda outros membros do time a entender e usar o framework.
* Explore e utilize as ferramentas internas (Rebot, Libdoc etc) para ganhar produtividade.

---

## 8. Referências / Links Úteis

* Página oficial de documentação: [robotframework.org](https://robotframework.org) ([robotframework.org][7])
* Guia do usuário (User Guide) — versão mais recente: vê-se a introdução em 7.0.1 como exemplo. ([robotframework.org][3])
* Standard Library overview: [https://docs.robotframework.org/docs/different_libraries/standard](https://docs.robotframework.org/docs/different_libraries/standard) ([docs.robotframework.org][5])
* Como estender com bibliotecas Python: [https://docs.robotframework.org/docs/extending_robot_framework/custom-libraries/python_library](https://docs.robotframework.org/docs/extending_robot_framework/custom-libraries/python_library) ([docs.robotframework.org][8])

---

Se quiser, posso **baixar ou disponibilizar para você um documento PDF ou ZIP** com **todo o User Guide + bibliotecas padrão** da versão que você escolher (por exemplo a versão 7.x ou a mais recente) para que possa incluir no seu repositório de QA. Você gostaria que eu fizesse isso?

[1]: https://robotframework.org/robotframework/latest/RobotFrameworkUserGuide.html?utm_source=chatgpt.com "Robot Framework User Guide"
[2]: https://robotframework.org/robotframework/6.1.1/RobotFrameworkUserGuide.html?utm_source=chatgpt.com "Robot Framework User Guide"
[3]: https://robotframework.org/robotframework/7.0.1/RobotFrameworkUserGuide.html?utm_source=chatgpt.com "Version 7.0.1"
[4]: https://robotframework.org/robotframework/4.0.1/RobotFrameworkUserGuide.html?utm_source=chatgpt.com "Version 4.0.1"
[5]: https://docs.robotframework.org/docs/different_libraries/standard?utm_source=chatgpt.com "Standard Library"
[6]: https://robotframework.org/robotframework/latest/libraries/BuiltIn.html?utm_source=chatgpt.com "BuiltIn"
[7]: https://robotframework.org/robotframework/?utm_source=chatgpt.com "Robot Framework documentation"
[8]: https://docs.robotframework.org/docs/extending_robot_framework/custom-libraries/python_library?utm_source=chatgpt.com "Python Libraries"