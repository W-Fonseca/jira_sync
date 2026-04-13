🔄 Jira Worklog Sync

Script em Python para sincronizar worklogs entre dois ambientes Jira (origem → destino), com categorização automática e controle de duplicidade.

📌 Funcionalidades
Sincroniza worklogs da semana atual (segunda a domingo)
Filtra apenas worklogs do usuário autenticado
Classifica automaticamente por palavras-chave
Mapeia atividades para issues específicas no Jira destino
Evita duplicação de registros
Permite ajuste fácil das categorias (DE-PARA)

⚙️ Configuração
1. Instalar dependências
pip install requests

📍 Configurar acessos

Preencha as credenciais dos dois ambientes Jira diretamente no código:

# ─ CONFIGURAÇÕES - JIRA ORIGEM ─
SRC_BASE_URL    = "https://seu-dominio.atlassian.net"
SRC_EMAIL       = "seu-email@empresa.com"
SRC_API_TOKEN   = "seu_token_aqui"

# ─ CONFIGURAÇÕES - JIRA DESTINO ─
DST_BASE_URL    = "https://outro-dominio.atlassian.net"
DST_EMAIL       = "seu-email@empresa.com"
DST_API_TOKEN   = "seu_token_aqui"

🧠 Mapeamento de tarefas

O script utiliza palavras-chave para definir automaticamente em qual issue do Jira destino o worklog será registrado.

TASK_MAPPING = [
    (["daily"],                                   "UN-12"),
    (["desenvolvimento", "development"],          "UN-14"),
    (["reunião", "reuniao", "meeting", "reunio"], "UN-24"),
    (["sustentação", "sustentacao", "sustenta"],  "UN-22"),
    (["documentação", "documentacao", "document", "definição", "definicao", "arquitetura"], "UN-26"),
    (["apoio", "apoio time", "support"],          "UN-27"),
    (["teste", "testes"],                         "UN-31"),
]
