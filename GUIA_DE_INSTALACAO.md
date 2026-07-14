# Pokt Intercept X — Guia de Instalação

**Versão:** 0.4.7

Esta pasta contém os instaladores oficiais e este guia.

Site: **https://www.poktinterceptx.site**

---

## Conteúdo da pasta `Intercept_X`

| Arquivo | Plataforma |
|---------|------------|
| `Pokt-Intercept-X-Setup-0.4.7.exe` | Windows 10/11 (64-bit) |
| `pokt-intercept-x_0.4.7_amd64.deb` | Linux Debian / Ubuntu / derivados |
| `latest.yml` | Metadados de auto-update (Settings → Atualizações) |
| `GUIA_DE_INSTALACAO.md` | Este guia |

---

## Windows

1. Baixe ou copie **`Pokt-Intercept-X-Setup-0.4.7.exe`** desta pasta (ou em [Download no site](https://www.poktinterceptx.site/download)).
2. Execute o instalador (duplo clique).
3. Siga o assistente — você pode escolher o diretório de instalação.
4. Atalhos serão criados na **Área de Trabalho** e no **Menu Iniciar**.
5. Abra **Pokt Intercept X** pelo atalho.

**Requisitos:** Windows 10 ou superior, 64-bit, 4 GB RAM recomendados.

**Atualizações:** com o app aberto, vá em **Settings → Atualizações → Verificar atualizações** (não é necessário baixar o `.exe` de novo).

---

## Linux (Debian / Ubuntu)

1. Baixe ou copie **`pokt-intercept-x_0.4.7_amd64.deb`** desta pasta.
2. No terminal, na pasta do arquivo:

```bash
sudo dpkg -i pokt-intercept-x_0.4.7_amd64.deb
sudo apt-get install -f
```

3. Inicie pelo menu de aplicativos ou pelo terminal:

```bash
pokt-intercept-x
```

**Requisitos:** amd64, GTK3, dependências listadas no pacote `.deb`.

---

## Arsenal — Docker ou Podman (obrigatório para ferramentas CLI)

O **Arsenal** executa ferramentas (subfinder, httpx, nuclei, etc.) e o **Terminal integrado** dentro de **containers Linux**. Você precisa de um runtime de containers instalado e **em execução** antes de usar o Arsenal.

### Opção A — Docker Desktop (recomendado no Windows)

1. Baixe: [https://www.docker.com/products/docker-desktop/](https://www.docker.com/products/docker-desktop/)
2. Instale e reinicie o PC se solicitado.
3. Abra **Docker Desktop** e aguarde o ícone ficar verde (“Docker is running”).
4. No PowerShell, confirme:

```powershell
docker version
docker run --rm hello-world
```

5. **Imagem do terminal Arsenal** (primeira vez ou após atualizar o app):

```powershell
cd C:\Users\Lesenechal\Desktop\Projetos\Ferramentas\Pokt_Intercept_X
npm run build:shell
```

> Se você só usa o instalador `.exe`, abra o PowerShell na pasta do projeto clonado ou rode o build a partir do repositório de desenvolvimento. O app também tenta construir a imagem automaticamente na primeira conexão ao Terminal.

### Opção B — Podman (alternativa open source)

Funciona no **Linux** e no **Windows** (Podman Desktop ou CLI).

- Site: [https://podman.io/](https://podman.io/)
- Linux (Debian/Ubuntu): `sudo apt install podman`
- Confirme: `podman version`

O Pokt Intercept X detecta **Docker ou Podman** automaticamente — basta um dos dois estar disponível no `PATH`.

### O que roda em container?

| Recurso | Imagem / uso |
|---------|----------------|
| Terminal Arsenal | `ghcr.io/pokt/arsenal-shell:latest` |
| Ferramentas do catálogo | `ghcr.io/pokt/arsenal-<tool>:latest` (ex.: `arsenal-subfinder`) |
| Pipelines | Encadeiam containers automaticamente |

As ferramentas são **baixadas/instaladas pelo app** na aba Arsenal (Loja). Na primeira execução de cada tool, a imagem Docker correspondente é obtida.

### Problemas comuns

| Sintoma | Solução |
|---------|---------|
| “Docker/Podman não disponível” | Inicie Docker Desktop ou instale Podman |
| Terminal não abre | Rode `npm run build:shell` na pasta do projeto |
| Ferramenta lenta na 1ª vez | Normal — download da imagem (~100–500 MB por tool) |
| Linux: permission denied | Adicione seu usuário ao grupo `docker`: `sudo usermod -aG docker $USER` |

Documentação completa no site: [Containers & Arsenal](https://www.poktinterceptx.site/docs/containers)

---

## Novidades v0.4.7

- **Findings unificados** — deduplicação, evidências, triagem e reteste
- **Doctor integrado** — diagnóstico de sidecar, CA, Docker e Ollama
- **Guardrails operacionais** — escopo obrigatório, limites e auditoria de jobs
- **UX integrada** — Ctrl+K, Enviar para…, Central de Jobs e Engagement Workspace
- **Evidence Vault** — evidências com hash e relatórios HTML/Markdown/PDF/DOCX
- **Testes avançados** — regressões via CLI (`pix`), Autorização diferencial e schema drift
- **SDK de plugins** — sandbox, assinatura e pacotes colaborativos criptografados
- **HTTP/3 experimental** — disponível via feature flag (desativado por padrão)

## Novidades v0.4.6

- **Arsenal Pro** — cabeçalho exibe o plano correto (Pro / Pro Plus / Pro Team) em vez do texto do Free
- **Terminal Arsenal** — colar via Ctrl+V, botão direito e botão Colar corrigidos (clipboard via IPC Electron)
- **Chaves de API** — tela dedicada com rolagem e botão Voltar ao Arsenal

## Novidades v0.4.4

- **Pipeline custom** — inputs não travam mais ao excluir; botão Editar abre o formulário no topo
- **Terminal Arsenal** — colar com Ctrl+V, Shift+Insert e botão direito corrigidos
- **Evidências** — imagens menores e painel sem barra de rolagem horizontal

## Novidades v0.4.3

- **Anotações** — prévia de imagens nas evidências, colar prints (Ctrl+V) e múltiplos arquivos de anotação por pasta
- **Arsenal** — editar, renomear e excluir pipelines custom salvos
- **Terminal Arsenal** — colar com Ctrl+V e botão direito

---

## Primeiro uso

1. Abra o app → **Settings** → instale o **certificado CA** (necessário para HTTPS).
2. Defina um **Scope** (alvo do teste).
3. Inicie o **Proxy** (porta 8080 por padrão).
4. Abra o **Browser** integrado ou configure o sistema/aplicação para usar o proxy.
5. Use **Intercept** / **HTTP History** para inspecionar tráfego.
6. (Opcional) Inicie o Docker Desktop e abra o **Arsenal** para tools CLI.

---

## Suporte

- Site: https://www.poktinterceptx.site
- Download: https://www.poktinterceptx.site/download
- Docs: https://www.poktinterceptx.site/docs/containers
