# Finanças — app pessoal para iPhone

App de controle financeiro que roda no seu iPhone como aplicativo instalado:
ícone na tela de início, tela cheia sem barra do Safari, e funciona sem internet.

**Seus dados nunca saem do aparelho.** Não existe servidor, conta ou sincronização.
Lançamentos, cartões e renda ficam gravados no armazenamento local do próprio app.

---

## 1. Publicar (uma vez, pelo computador)

O iPhone só deixa instalar na tela de início páginas servidas por `https`.
Por isso o código precisa ficar numa URL. O GitHub Pages resolve isso de graça
em poucos minutos.

1. Acesse github.com e crie um repositório novo — por exemplo `fin`.
   Marque **Public**. Em conta gratuita, o GitHub Pages só publica repositório
   público; com repositório privado o Pages exige plano pago. Como o que sobe é
   apenas o código, sem nenhum dado seu, público não expõe nada.
2. Na página do repositório, clique em **Add file › Upload files** e arraste
   TODOS os arquivos desta pasta, incluindo a pasta `icons`.
   Faça o commit.
3. Vá em **Settings › Pages**.
   Em *Source*, escolha **Deploy from a branch**; em *Branch*, escolha `main` e `/ (root)`.
   Clique em **Save**.
4. Espere cerca de um minuto e recarregue a página. O endereço aparece no topo,
   no formato `https://SEU-USUARIO.github.io/fin/`.

## 2. Instalar no iPhone

1. Abra esse endereço **no Safari** (precisa ser o Safari; Chrome no iOS não instala).
2. Toque no botão de **Compartilhar** (o quadrado com a seta para cima).
3. Role e toque em **Adicionar à Tela de Início**.
4. Confirme. O ícone aparece junto dos outros apps.

Abra sempre por esse ícone. Assim ele roda em tela cheia e offline.
Depois da primeira abertura, o app fica guardado no aparelho e não precisa mais
de internet para funcionar.

## 3. Primeiro uso

Abra os **Ajustes** (⚙ no topo) e preencha:

- **Renda fixa esperada** — a base de todos os cálculos: tetos, quanto pode gastar
  por dia, alertas. Sem ela o app registra, mas não aconselha.
- **Cartões** — nome, limite, dia de fechamento e dia de vencimento.
  É com isso que o app descobre sozinho em qual fatura cada compra cai.

## 4. Privacidade

- O **código** fica público no endereço do GitHub Pages. Mesmo em planos pagos,
  onde o repositório pode ser privado, a página publicada continua acessível a
  quem tiver o link — Pages com acesso restrito só existe no Enterprise.
- Os **seus dados** não estão lá. Quem abrir o link vê um app vazio.
- Nada é enviado para lugar nenhum: não há requisição de rede depois que o app
  carrega.

Se você preferir que nem o endereço seja público, as alternativas são o
Cloudflare Pages com Cloudflare Access (grátis, exige login com o seu e-mail para
abrir a página) ou a Netlify com proteção por senha (plano pago).

## 5. Backup — importante

Os dados vivem apenas neste iPhone. Se você apagar o app, trocar de aparelho ou
limpar os dados do site, eles se perdem.

Em **Ajustes › Backup › Exportar**, o app gera um arquivo `.json` e abre a folha
de compartilhamento do iOS — salve nos Arquivos, no iCloud Drive ou mande para
você mesmo por e-mail. Para restaurar, use **Importar** e escolha o arquivo.

O app avisa sozinho na tela inicial quando passam 14 dias sem backup.

## 6. Atualizar o app

Suba o `index.html` novo no repositório. Na próxima vez que abrir o app com
internet, ele baixa a versão nova e usa a partir da abertura seguinte.

## 7. Sobre a interface

A interface segue as Human Interface Guidelines da Apple: tipografia SF nos tamanhos
padrão do sistema, cores dinâmicas do iOS, listas agrupadas, barra de abas e folhas
modais nativas. O app acompanha o tema claro ou escuro do aparelho automaticamente —
não existe um botão de tema dentro dele, porque a Apple recomenda respeitar a escolha
do sistema.

Também responde aos ajustes de acessibilidade: Reduzir Transparência troca o efeito de
vidro das barras por fundo sólido, Aumentar Contraste escurece os textos secundários e
Reduzir Movimento desliga as animações.

---

## Arquivos

| Arquivo | Para que serve |
|---|---|
| `index.html` | O app inteiro: interface, cálculos e armazenamento |
| `manifest.webmanifest` | Diz ao iOS o nome, o ícone e que ele abre em tela cheia |
| `sw.js` | Guarda o app no aparelho para funcionar offline |
| `icons/` | Ícones da tela de início |

Sem publicar, o `index.html` também abre direto no navegador de um computador,
com duplo clique — só não vira ícone no iPhone desse jeito.
