# Workshop de IA
Conteúdo preparatório para execução de Workshop de IA

## Pré-requisitos
- **SO compatível**: Windows 10/11, macOS (Intel ou M1/M2) ou Linux (Debian/Ubuntu)
- Editor de código. ( Recomendo o [VSCode](https://code.visualstudio.com/download) )
- Espaço livre em disco: **mínimo 10 GB**
- Python **3.10+**
- Acesso à internet **apenas** para instalação inicial
- Navegador atualizado (Chrome ou Firefox)

## Repository URL
### Shorten
```bash
    https://tinyurl.com/2epp7ehm
```

### QR Code
![QR Code](/assets/qr-code.png)

## Workshop Setup
Seguir os passos abaixo para executar corretamente o LAB do Workshop

### Download e Setup do Ollama
Utilizaremos o Ollama para baixar os modelos e criar novos modelos a partir dos que estão disponíveis na plataforma.

Faça o [download](https://ollama.com/download) do Ollama para o seu sistema operacional

Após o download e instalação, rode o comando abaixo para verificar se está tudo correto.
```bash
    ollama -h
```

---

## Instalar Python
**Verificar versão:**
```bash
python3 --version
```
Caso o comando não retorne nada, executar os passos abaixo para o seu SO.

**Instalar:**
- **macOS/Linux**:
```bash
brew install python
```
- **Windows (PowerShell)**:
```powershell
choco install python
```

---

### Criar Ambiente Virtual
```bash
python3 -m venv .venv

source .venv/bin/activate    # macOS/Linux

.venv\Scripts\activate       # Windows
```


## Criar Modelo Local
Arquivo **Modelfile**:
```
FROM llama2
SYSTEM """
Você é um assistente especializado em orientar alunos em perguntas relacionadas ao contexto e somente ao contexto.
Use sempre as informações a seguir para responder perguntas:

[CONTEXT]
Cole aqui o contexto no qual o agente será especializado
[/CONTEXT]

## Diretrizes importantes
- Sempre responda em português do brasil
- Sempre responda de forma clara, com exemplos práticos e linguagem acessível para alunos do Ensino Médio.
- Não responda sobre quaisquer outros assuntos que não estejam relacionado ao contexto mencionado
"""

```

Criar modelo:
```bash
ollama create agente_ciencias -f Modelfile
```
<!-- 
---

## Instalar Dependências Python
```bash
pip install gradio
```

---

## Criar o Script `app.py`
```python
import subprocess
import gradio as gr

MODEL_NAME = "agente_ciencias"

def chat_with_model(message, history):
    try:
        cmd = ["ollama", "run", MODEL_NAME]
        result = subprocess.run(cmd, input=message, text=True, capture_output=True)
        if result.returncode != 0:
            return f"[ERRO] {result.stderr.strip()}"
        return result.stdout.strip()
    except Exception as e:
        return f"[ERRO] Falha ao executar o modelo: {e}"

demo = gr.ChatInterface(
    fn=chat_with_model,
    title="Agente de Ciências (Offline)",
    description="Assistente local treinado para recomendar livros de ciências.",
    examples=[
        "Qual livro você recomenda para estudar física?",
        "Sugira um livro de biologia e explique o motivo.",
        "Quais livros abordam astronomia de forma introdutória?"
    ]
)

if __name__ == "__main__":
    demo.launch(server_name="0.0.0.0", server_port=7860)
```

---

## Executar o Servidor
```bash
python app.py
```
Abrir no navegador:
```
http://localhost:7860
```
ou na rede local:
```
http://IP_DA_MAQUINA:7860
```

--- -->

## Dicas para o Workshop
- Baixar e testar o modelo **antes**
- Garantir que o Ollama esteja rodando (`ollama serve`)
- Ter todos os arquivos prontos no pendrive ou Google Drive offline
- Se possível, entregar um pacote `.zip` com tudo configurado para os alunos
