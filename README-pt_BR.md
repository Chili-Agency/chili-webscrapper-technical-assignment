## Teste de Web Scraping

### Objetivo

Desenvolver um script de Web Scraping usando a linguagem de programação de sua escolha (Node.js, Python, PHP, C, etc). O script deve:

1. Capturar links contidos na URL informada.
2. Capturar imagens contidas na URL informada (apenas os links das imagens).
3. Capturar o título da página e a meta descrição, caso existam.
4. Apresentar um relatório com as informações coletadas em uma página web.

### Estrutura Sugerida

- URL do endpoint: `http://localhost/web-scrapper?url=https://exemplo.com`
- A estrutura acima é um exemplo; você pode usar a abordagem que preferir, desde que seja entendível.

### Instruções de Entrega

1. **Código:**
   - Subir em uma ferramenta GIT (como GitHub) para análise.

2. **Documentação:**
   - Inclua uma documentação explicando como rodar o script, além das configurações de ambiente necessárias.

### Exemplo de Script (Python)
Aqui está um exemplo básico em Python usando a biblioteca `BeautifulSoup`:

```python
import requests
from bs4 import BeautifulSoup

def scrape(url):
    response = requests.get(url)
    soup = BeautifulSoup(response.content, 'html.parser')

    links = [a['href'] for a in soup.find_all('a', href=True)]
    images = [img['src'] for img in soup.find_all('img', src=True)]
    title = soup.title.string if soup.title else 'No title'
    meta_desc = soup.find('meta', attrs={'name': 'description'})
    meta_desc = meta_desc['content'] if meta_desc else 'No meta description'

    return {
        'links': links,
        'images': images,
        'title': title,
        'meta_desc': meta_desc
    }

if __name__ == '__main__':
    url = 'https://exemplo.com'
    data = scrape(url)
    print(data)
```

### Notas

- Pode usar códigos prontos, desde que forneça o link do código original para comparação.
- Perguntas podem surgir após a conferência.