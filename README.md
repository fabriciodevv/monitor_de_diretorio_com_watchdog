

# Introdução Watchdog API em Python 🐍

Watchdog é uma biblioteca multiplataforma, o que significa que funciona em sistemas como Windows, macOS e Linux. Ela facilita o monitoramento contínuo de diretórios, sem precisar de verificações manuais ou repetitivas. Em vez de ficar checando constantemente se um arquivo foi alterado, a Watchdog utiliza observadores para detectar automaticamente qualquer evento de sistema de arquivos.

# Como Funciona

A biblioteca Watchdog funciona através de "observadores" que monitoram um diretório específico. Eles capturam eventos, como:

* Criação de arquivos/diretórios
* Modificação de arquivos
* Exclusão de arquivos/diretórios
* Movimentação de arquivos/diretórios
* Você pode personalizar o comportamento para cada tipo de evento, reagindo a essas mudanças em tempo real, por exemplo, disparando ações como backups automáticos ou processamento de dados.

# Exemplos de Uso
A Watchdog pode ser usada em diversos cenários práticos:

* Automação de backup: Toda vez que um arquivo for adicionado ou modificado em um diretório, um script pode ser executado para fazer backup automático.

* Processamento de arquivos: Em pipelines de dados, quando um novo arquivo de dados é adicionado a um diretório, o Watchdog pode iniciar o processamento automaticamente.

* Sincronização de arquivos: Para sincronizar automaticamente diretórios locais com diretórios na nuvem sempre que ocorrer uma mudança.

* Segurança e monitoramento: Pode ser usado para monitorar alterações não autorizadas em arquivos sensíveis, disparando alertas em tempo real.

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
````

#EXEMPLO DE APLICAÇÃO, MONITORANDO UM DIRETÓRIO DE ARQUIVOS

```
import time
from watchdog.observers import Observer
from watchdog.events import FileSystemEventHandler

class MonitoramentoHandler(FileSystemEventHandler):
    def on_created(self, event):
        print(f"Arquivo ou diretório criado: {event.src_path}")
    
    def on_modified(self, event):
        print(f"Arquivo ou diretório modificado: {event.src_path}")
    
    def on_deleted(self, event):
        print(f"Arquivo ou diretório excluído: {event.src_path}")
    
    def on_moved(self, event):
        print(f"Arquivo ou diretório movido: {event.src_path}")

if __name__ == "__main__":
    path = "./diretorio_para_monitorar"
    event_handler = MonitoramentoHandler()
    observer = Observer()
    observer.schedule(event_handler, path, recursive=True)
    observer.start()
    
    try:
        while True:
            time.sleep(1)
    except KeyboardInterrupt:
        observer.stop()
    observer.join()


