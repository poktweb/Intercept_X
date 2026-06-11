# Pokt Intercept X — Guia de Instalação

**Versão:** 0.2.0

Esta pasta contém os instaladores oficiais e este guia.

Repositório: **https://github.com/poktweb/Intercept_X**

---

## Conteúdo da pasta `Intercept_X`

| Arquivo | Plataforma |
|---------|------------|
| `Pokt-Intercept-X-Setup-0.2.0.exe` | Windows 10/11 (64-bit) |
| `pokt-intercept-x_0.2.0_amd64.deb` | Linux Debian / Ubuntu / derivados |
| `latest.yml` | Metadados de auto-update (Settings → Atualizações) |
| `GUIA_DE_INSTALACAO.md` | Este guia |

---

## Windows

1. Baixe ou copie **`Pokt-Intercept-X-Setup-0.2.0.exe`** desta pasta.
2. Execute o instalador (duplo clique).
3. Siga o assistente — você pode escolher o diretório de instalação.
4. Atalhos serão criados na **Área de Trabalho** e no **Menu Iniciar**.
5. Abra **Pokt Intercept X** pelo atalho.

**Requisitos:** Windows 10 ou superior, 64-bit, 4 GB RAM recomendados.

**Atualizações:** com o app aberto, vá em **Settings → Atualizações → Verificar atualizações** (não é necessário baixar o `.exe` de novo).

---

## Linux (Debian / Ubuntu)

1. Baixe ou copie **`pokt-intercept-x_0.2.0_amd64.deb`** desta pasta.
2. No terminal, na pasta do arquivo:

```bash
sudo dpkg -i pokt-intercept-x_0.2.0_amd64.deb
sudo apt-get install -f
```

3. Inicie pelo menu de aplicativos ou pelo terminal:

```bash
pokt-intercept-x
```

**Requisitos:** amd64, GTK3, dependências listadas no pacote `.deb`.

---

## Novidades v0.2.0

- **Recon Avançado Pro** — motor 100% nativo (subdomínios, diretórios, JS, API, secrets/tokens)
- **pix-pathhunter** — filtro inteligente de status HTTP (200, 301, 403…) e anti-rate-limit
- Correções de sidecar e auto-update

---

## Após instalar (primeiro uso)

1. **Certificado HTTPS** — em **Settings → Certificados**, instale o certificado CA do proxy para interceptar HTTPS sem erros de SSL.
2. **Proxy** — configure o navegador ou use o **Browser** integrado; proxy padrão: `127.0.0.1:8080`.
3. **Projeto** — crie um projeto em **Projetos** para organizar histórico e escopos.
4. **Conta (opcional)** — faça login na sidebar para sincronizar plano Pro/Basic.

---

## Desinstalar

### Windows

**Configurações → Aplicativos → Pokt Intercept X → Desinstalar**

Seus dados (projetos, histórico, sessão) permanecem em `%APPDATA%\pokt-intercept-x` até você apagá-los manualmente.

### Linux

```bash
sudo apt remove pokt-intercept-x
```

Dados do usuário ficam em `~/.config/pokt-intercept-x` (ou pasta equivalente do Electron).

---

## Problemas comuns

| Problema | Solução |
|----------|---------|
| Backend não inicia | Verifique se as portas **9090** e **8080** estão livres |
| HTTPS com erro de certificado | Instale o CA em Settings e confie no proxy |
| App não abre no Linux | Execute `pokt-intercept-x` no terminal e leia a mensagem de erro |
| SmartScreen no Windows | Confirme que baixou desta pasta oficial; assinatura digital em breve |

---

**Suporte:** contato@pokt.dev
