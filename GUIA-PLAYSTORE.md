# 🌿 Livre App — Guia Completo: Play Store + AdSense

## O que você tem agora (3 arquivos)
- `index.html` — O app completo, pronto para web
- `manifest.json` — Transforma em PWA (Progressive Web App)
- `sw.js` — Permite uso offline no celular

---

## PASSO 1 — Criar conta no GitHub (grátis, 5 min)

1. Acesse https://github.com e crie uma conta gratuita
2. Clique em **"New repository"**
3. Nome: `livre-app`
4. Marque **"Public"**
5. Clique em **"Create repository"**
6. Faça upload dos 3 arquivos: `index.html`, `manifest.json`, `sw.js`
7. Vá em **Settings → Pages → Source:** selecione "main" e "/" (root)
8. Aguarde 2 minutos. Seu app estará em:
   `https://SEU-USUARIO.github.io/livre-app/`

✅ **Seu app está no ar, gratuito e com HTTPS (obrigatório para PWA)**

---

## PASSO 2 — Criar ícones para o app (obrigatório para Play Store)

Você precisa de dois ícones:
- `icon-192.png` — 192×192 pixels
- `icon-512.png` — 512×512 pixels

### Opção gratuita:
1. Acesse https://favicon.io/favicon-generator/
2. Texto: **L** | Fonte: qualquer | Cor de fundo: `#1B4332` | Cor do texto: `#FFFFFF`
3. Baixe e renomeie para `icon-192.png` e `icon-512.png`
4. Faça upload para seu GitHub junto dos outros arquivos

---

## PASSO 3 — Configurar Google AdSense (monetização via web)

### 3.1 — Criar conta AdSense
1. Acesse https://adsense.google.com
2. Clique em **"Começar"**
3. Coloque a URL: `https://SEU-USUARIO.github.io/livre-app/`
4. Selecione país: **Brasil**
5. Aceite os termos e clique em **"Iniciar uso do AdSense"**

### 3.2 — Verificar seu site
O Google pedirá que você adicione um código ao `index.html`.
O código já está preparado no arquivo — só substituir:
```
ca-pub-XXXXXXXXXXXXXXXXXX  →  seu número real do AdSense
```

### 3.3 — Aguardar aprovação
- Google analisa em **1 a 14 dias**
- Seu site precisa ter conteúdo útil (o app já tem!)
- Após aprovação, crie os blocos de anúncio e substitua:
  ```
  data-ad-slot="XXXXXXXXXX"  →  ID do seu bloco de anúncio
  ```

### 💰 Quanto dá para ganhar?
- CPC (custo por clique) no nicho saúde: R$0,20 a R$2,00
- Com 1.000 usuários ativos/dia: estimativa R$100-500/mês
- Escala com o volume de usuários

---

## PASSO 4 — Publicar na Play Store via PWABuilder (grátis)

### 4.1 — Criar conta Google Play Console
1. Acesse https://play.google.com/console
2. Pague **US$25** (taxa única, para sempre — cartão crédito/débito)
3. Complete o cadastro de desenvolvedor

### 4.2 — Gerar o APK com PWABuilder
1. Acesse https://www.pwabuilder.com
2. Cole a URL: `https://SEU-USUARIO.github.io/livre-app/`
3. Clique em **"Start"** — o PWABuilder analisa seu app
4. Clique em **"Package for stores"**
5. Selecione **"Android"**
6. Preencha:
   - Package name: `com.livre.parar.fumar`
   - App version: `1.0`
   - Signing key: clique em **"Generate new"** e salve o arquivo `.keystore`
7. Clique em **"Download Package"**
8. Você receberá um `.aab` (Android App Bundle) pronto para upload

### 4.3 — Subir na Play Store
1. No Google Play Console, clique em **"Criar app"**
2. Nome: **Livre — Pare de Fumar**
3. Categoria: **Saúde e fitness**
4. Tipo: **Aplicativo**
5. Preencha:
   - Descrição curta (80 chars): `Sua jornada para parar de fumar, com amor e ciência.`
   - Descrição completa: (use o texto abaixo)
6. Upload o `.aab` gerado pelo PWABuilder
7. Siga o passo a passo de avaliação de conteúdo
8. Envie para revisão

### Texto de descrição da Play Store:
```
🌿 LIVRE — Seu companheiro para parar de fumar

Desenvolvido com amor por alguém que também quis parar, o Livre é o app mais completo do Brasil para quem quer se libertar do cigarro, da maconha ou de qualquer dependência química.

✅ O QUE O APP FAZ:
• Contador de dias em tempo real (com horas e minutos!)
• Calcula o dinheiro que você economizou
• Mostra quantos cigarros você evitou
• Acompanha a recuperação do seu corpo (de 20 min a 10 anos!)
• Exercício de respiração 4-7-8 guiado para fissuras
• Diário pessoal com registro de humor
• Registro de fissuras com gatilhos e intensidade
• 15 conquistas para celebrar cada vitória
• Suporte para recaída sem julgamento

💚 FEITO COM AMOR:
Este app foi criado por alguém que também fumou e quer parar. Aqui não tem julgamento, só suporte.

🔒 PRIVACIDADE:
Todos os seus dados ficam só no seu celular. Nada é enviado para servidores.

Sua jornada começa agora. 🌱
```

---

## PASSO 5 — Screenshots e assets para a Play Store

Você precisa de pelo menos 2 screenshots do app (celular).

### Como tirar screenshots:
1. Abra `https://SEU-USUARIO.github.io/livre-app/` no Chrome
2. F12 → ícone de celular → selecione "iPhone 12 Pro" (390×844)
3. Complete o onboarding com dados de exemplo
4. Print da tela Home e da tela Saúde
5. Salve como PNG

### Dimensões obrigatórias:
- Screenshots: mínimo 320px de largura, máximo 3840px
- Feature graphic: 1024×500px (banner no topo da loja)
- Ícone alta resolução: 512×512px

---

## PASSO 6 — Configurar Digital Asset Links (TWA)

Para que o Google reconheça seu PWA como app (sem barra de URL no celular), você precisa do arquivo `assetlinks.json`:

1. No PWABuilder, após gerar o APK, ele mostra um SHA-256 fingerprint
2. Crie o arquivo `.well-known/assetlinks.json` no seu repositório GitHub com:
```json
[{
  "relation": ["delegate_permission/common.handle_all_urls"],
  "target": {
    "namespace": "android_app",
    "package_name": "com.livre.parar.fumar",
    "sha256_cert_fingerprints": ["SEU_FINGERPRINT_AQUI"]
  }
}]
```
3. O PWABuilder explica como fazer isso no próprio site.

---

## ESTRATÉGIA DE MONETIZAÇÃO COMPLETA

### Fonte 1 — AdSense (web, aprovado pelo Google)
- Anúncios no site/PWA
- Paga por clique e impressão
- Ideal para tráfego vindo de redes sociais

### Fonte 2 — Kiwify (produto digital)
- Versão Premium sem anúncios: R$27-47
- Bônus exclusivos (e-book, planilha de controle)
- Afiliados podem revender e você ganha % de cada venda

### Fonte 3 — Play Store (futuro)
- App gratuito com anúncios (AdSense via TWA)
- Compra única para versão premium: R$9,90
- Mais visibilidade orgânica

### Dica de lançamento:
- Lance primeiro no Kiwify (sem custo)
- Use o Kiwify para validar e ter renda inicial
- Com renda, invista nos US$25 da Play Store
- Use Instagram/TikTok com histórias reais de quem usou o app

---

## TIMELINE REALISTA

| Semana | Ação |
|--------|------|
| Semana 1 | GitHub Pages + Kiwify funcionando |
| Semana 2 | Aplicar no AdSense |
| Semana 3-4 | Aprovação AdSense + primeiros anúncios |
| Semana 5 | Criar conta Play Console (US$25) |
| Semana 6 | PWABuilder → gerar APK |
| Semana 7 | Submeter para Play Store |
| Semana 8-10 | Aprovação e lançamento na loja |

---

## SUPORTE

Se travar em qualquer passo, pergunte ao Claude com:
- "Tá dando erro X no passo Y do guia do Livre"
- Vou te ajudar passo a passo! 💚

---

*Feito com amor. Você vai conseguir! 🌿*
