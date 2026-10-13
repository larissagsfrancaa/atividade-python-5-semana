# Sistema de Análise de Dados em Python 🐍
### Entregável da Semana 05 - Desafio Sprint 5

Este projeto consiste na finalização de um **Sistema de Análise de Dados** desenvolvido em Python. O objetivo principal é consolidar os três pilares fundamentais estudados em aula: **manipulação de arquivos**, validação de dados via **expressões regulares (Regex)** e **tratamento robusto de exceções**.

---

## 📋 Critérios Técnicos Atendidos

### 1. Manipulação Segura de Arquivos
Para garantir a integridade dos dados na leitura e escrita dos relatórios, o sistema utiliza o gerenciador de contexto `with open()`, evitando vazamento de memória ou arquivos corrompidos:
```python
with open(caminho, "w", encoding="utf-8") as arquivo:
    # Código protegido para escrita está aqui
```
* **Justificativa de Uso:** O parâmetro `encoding="utf-8"` foi explicitamente declarado para prevenir problemas de acentuação e garantir a compatibilidade do sistema em diferentes sistemas operacionais (Windows, Linux e macOS).

### 2. Validação com Regex (Expressões Regulares)
Utilizando o módulo embutido `re`, foram aplicados os metacaracteres corretos (como `\d`, `\w`, `\s`, `^`, `$`) em raw strings (`r''`) para evitar conflitos de escape. Os padrões validados incluem:
* **E-mail:** Validação estrutural do domínio e provedor.
* **CPF:** Verificação da máscara e sequência numérica (`\d{3}\.\d{3}\.\d{3}-\d{2}`).
* **Telefone:** Checagem de DDD e quantidade de dígitos válidos.
* **Data:** Validação do formato padrão de calendário.

### 3. Tratamento de Exceções e Resiliência
Para impedir o encerramento abrupto do programa diante de dados corrompidos ou erros inesperados, foi implementada a estrutura completa `try/except/else/finally`:
* **`FileNotFoundError`:** Capturado caso o arquivo CSV informado para leitura não exista no diretório.
* **`ValueError`:** Capturado se houver falhas de conversão de tipos de dados inválidos.
* **`KeyError`:** Tratado para identificar e alertar sobre colunas ausentes no cabeçalho do arquivo CSV de entrada.
* **Bloco `finally`:** Implementado para assegurar a execução de rotinas críticas do ciclo de vida dos arquivos, ocorrendo ou não uma exceção durante o processamento.

### 4. Exceções Personalizadas
Para tratar regras de negócio específicas que o Python não mapeia nativamente, foram criadas classes que herdam diretamente da classe base `Exception`:
* `IdadeInvalidaError`
* `FormatoInvalidoError`

### 5. Relatório Formatado
Ao final do processamento, o script gera um resumo detalhado utilizando *f-strings* dinâmicas contendo:
* Total de registros analisados.
* Quantidade de registros válidos.
* Quantidade de registros inválidos.
* Estatísticas gerais da consistência da análise de dados.

---

## 📂 Arquivos do Repositório

* `sistema.py`: Script Python principal que executa a leitura, validações de Regex e tratamento de erros.
* `dados.csv`: Arquivo de dados original utilizado para os testes de entrada.
* `relatorio.txt`: Relatório final estruturado gerado automaticamente pelo sistema após o processamento.
* `README.md`: Documentação explicativa do projeto (este arquivo).
