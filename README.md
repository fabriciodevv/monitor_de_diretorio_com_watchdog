# monitor_de_diretorio_com_watchdog

# Introdução Watchdog API em Python


Watchdog é uma biblioteca multiplataforma, o que significa que funciona em sistemas como Windows, macOS e Linux. Ela facilita o monitoramento contínuo de diretórios, sem precisar de verificações manuais ou repetitivas. Em vez de ficar checando constantemente se um arquivo foi alterado, a Watchdog utiliza observadores para detectar automaticamente qualquer evento de sistema de arquivos.


## Funcionalidades

- Monitoramento de eventos no sistema de arquivos (criação, modificação, exclusão, movimentação);
- Fácil integração com scripts Python;
- Cross-platform (compatível com Windows, macOS e Linux);
- Ideal para automação e monitoramento de mudanças em diretórios.

## Pré-requisitos

- Python 3.6 ou superior
- Biblioteca `watchdog`

### Instalação

Para instalar o Watchdog, você pode utilizar o **pip**:

```bash
pip install watchdog
