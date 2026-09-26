# Hotmart Downloader

Script pra baixar cursos da Hotmart. Baixa vídeos, PDFs e anexos embutidos.

Baseado no gist do [@juvenal](https://gist.github.com/juvenal/2d9a822325769d30c45c635fbf388c1b) com suporte extra a PDFs embutidos do Google Drive.

---

## O que é baixado

| Tipo | Detalhes |
|---|---|
| Vídeos | Hotmart, Vimeo e YouTube |
| Anexos | PDFs, ZIPs e outros arquivos |
| PDFs do Google Drive | Antes ficavam escondidos; salvos como `gdrive_xxxxx.pdf` na pasta `Materiais` |
| Leitura complementar | Links extras das aulas |
| Descrições | Texto de cada aula |

Tudo organizado certinho em pastas por módulo e aula.

---

## Requisitos

- Python 3.6+
- [FFmpeg](https://ffmpeg.org/) instalado e no `PATH`
- Conexão estável (principalmente para vídeos)
- Espaço em disco suficiente, porque alguns cursos são bem pesados

---

## Instalação

```bash
pip install -r requirements.txt
```

### Configuração

Edite `config_cursos.py` e adicione o subdomínio de cada curso:

```python
CURSOS_SUBDOMINIOS = ["nome-do-seu-curso"]
```

#### Como encontrar o subdomínio

1. Acesse https://sun.hotmart.com/minhas-compras
2. Clique em **Acessar** no curso
3. Veja a URL, algo como:
   `https://hotmart.com/pt-BR/club/punchneedle/products/...`
4. O subdomínio é o trecho entre `/club/` e `/products/`, que neste exemplo é `punchneedle`



### Uso

```bash
python hotmark.py
```

Informe seu email e senha da Hotmart quando o script pedir.

---

## Comportamento

- **Retry:** se um anexo falhar, tenta até 3 vezes antes de desistir
- **Log:** registra toda a execução em `log.txt`

---

## Limitações conhecidas

**Subdomínio manual obrigatório.** Desde 2026, o endpoint `check_token` da API da Hotmart retorna `resources: []` vazio, mesmo com cursos comprados. Por isso os cursos não são listados automaticamente e precisam ser informados em `config_cursos.py`. É uma solução provisória até encontrarem outra forma de listar os cursos.

---

## Solução de problemas

1. **FFmpeg:** rode `ffmpeg -version` no terminal para ver se está instalado
2. **Login:** confira se o email e a senha estão corretos
3. **Outros erros:** veja os detalhes em `log.txt`

---

## Avisos

- ⚠️ Use **apenas** para cursos que você comprou.
- Projeto educacional. Use com responsabilidade.


---

Projeto educacional. Use com responsabilidade.
