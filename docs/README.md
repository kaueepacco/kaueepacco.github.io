# Explorando o cache de HTTP em aplicações REST

Vamos criar um projeto Python com Flask que incorpora conceitos avançados de caching baseados nos artigos selecionados. Este projeto simulará uma API REST que entrega dados potencialmente mutáveis, como previsões meteorológicas ou notícias, onde o caching pode significativamente melhorar a performance e reduzir a carga no servidor.

#### **Pré-requisitos**
- Python 3.x
- Flask
- Flask-Caching
- Postman ou similar (para testar a API)

### **Instalação**

```bash
pip install flask flask-caching
```
### **Passo a Passo**
#### 1. Configuração Inicial:
Inicie seu aplicativo Flask em app.py.
```python
from flask import Flask
app = Flask(_name_)
```
#### 2. Configuração do Flask-Caching:
Integre o Flask-Caching para caching simples no lado do servidor.
```python
from flask_caching import Cache

cache = Cache(app, config={'CACHE_TYPE': 'simple'})
```
#### 3. Rota com Cache:
Crie uma rota que utilize o cache para armazenar dados por 2 minutos. Imagine que esta rota retorna dados que mudam com pouca frequência, como informações de um artigo.
```python
@app.route('/article')
@cache.cached(timeout=120)  # Cache de 2 minutos
def article():
    # Aqui, inseriria a lógica para buscar dados reais, simularemos com um texto estático
    return "Aqui vai o conteúdo de um artigo."
```
