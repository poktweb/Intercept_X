# Pokt Intercept X — Guia de Instalação

**Versão:** 0.4.2

Esta pasta contém os instaladores oficiais e este guia.

Site: **https://www.poktinterceptx.site**

---

## Conteúdo da pasta `Intercept_X`

| Arquivo | Plataforma |
|---------|------------|
| `Pokt-Intercept-X-Setup-0.4.2.exe` | Windows 10/11 (64-bit) |
| `pokt-intercept-x_0.4.2_amd64.deb` | Linux Debian / Ubuntu / derivados |
| `latest.yml` | Metadados de auto-update (Settings → Atualizações) |
| `GUIA_DE_INSTALACAO.md` | Este guia |

---

## Windows

1. Baixe ou copie **`Pokt-Intercept-X-Setup-0.4.2.exe`** desta pasta (ou em [Download no site](https://www.poktinterceptx.site/download)).
2. Execute o instalador (duplo clique).
3. Siga o assistente — você pode escolher o diretório de instalação.
4. Atalhos serão criados na **Área de Trabalho** e no **Menu Iniciar**.
5. Abra **Pokt Intercept X** pelo atalho.

**Requisitos:** Windows 10 ou superior, 64-bit, 4 GB RAM recomendados.

**Atualizações:** com o app aberto, vá em **Settings → Atualizações → Verificar atualizações** (não é necessário baixar o `.exe` de novo).

---

## Linux (Debian / Ubuntu)

1. Baixe ou copie **`pokt-intercept-x_0.4.2_amd64.deb`** desta pasta.
2. No terminal, na pasta do arquivo:

```bash
sudo dpkg -i pokt-intercept-x_0.4.2_amd64.deb
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

## Novidades v0.4.2

- **Domínio oficial** — poktinterceptx.site (auth, licença, checkout e auto-update)
- **UI refinada** — HttpEditor, busca global, sitemap e confirmações de host
- **Painel de segurança do Arsenal** nas Configurações
- **Proteção IPC reforçada** e links externos seguros no frontend
- Validação e sanitização ampliadas em handlers da API local

## Novidades v0.3.9

- **Hardening de segurança** — Electron sandbox, auth da API local, token criptografado
- **Proxy de autenticação** — sessão do site sem expor JWT ao renderer
- **Docker.sock opt-in** — terminal Arsenal mais seguro por padrão (Configurações)
- Validação reforçada em URLs, Arsenal, IA, webhooks e busca FTS

## Novidades v0.3.8

- **AI Security Assistant** — chat unificado com histórico de conversas salvo
- **IA executa ferramentas** — peça subfinder + httpx e receba relatório no chat
- Download de relatórios `.md` e saída `.txt` direto na conversa
- Progresso em tempo real durante execução de pipelines no Arsenal

## Novidades v0.3.7

- **Correção:** Dockerfiles do Arsenal incluídos no instalador (.exe / .deb)
- Instalação de ferramentas (httpx, subfinder, nuclei…) funciona sem clonar o repositório

## Novidades v0.3.6

- **Arsenal expandido** — 160+ ferramentas CLI via containers Docker/Podman
- **Terminal Bash integrado** — sessão persistente no Arsenal com wrappers das tools
- **Pipelines customizados** — monte e salve pipelines personalizados
- **Correções de terminal no Windows** — conexão estável, saída alinhada, reconexão
- **Auto-update** via site oficial (`Settings → Atualizações`)

---

## Após instalar (primeiro uso)

1. **Instale Docker Desktop** (ou Podman) — veja seção Arsenal acima.
2. **Certificado HTTPS** — em **Settings → Certificados**, instale o certificado CA do proxy para interceptar HTTPS sem erros de SSL.
3. **Proxy** — configure o navegador ou use o **Browser** integrado; proxy padrão: `127.0.0.1:8080`.
4. **Projeto** — crie um projeto em **Projetos** para organizar histórico e escopos.
5. **Conta** — faça login em **Settings → Conta** para licença Pro e workspace Team.

---

## Suporte

- Site: https://www.poktinterceptx.site
- Download: https://www.poktinterceptx.site/download
- Containers: https://www.poktinterceptx.site/docs/containers
- E-mail: contato@pokt.dev
