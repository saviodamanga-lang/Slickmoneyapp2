# SlickMoney — app instalável (PWA)

## Instalar no celular (mais rápido)
1. Publique esta pasta em uma hospedagem HTTPS (Netlify Drop, Vercel, GitHub Pages ou Cloudflare Pages). Basta arrastar a pasta.
2. Abra o endereço no celular.
   - Android (Chrome): menu ⋮ > "Instalar app".
   - iPhone (Safari): Compartilhar > "Adicionar à Tela de Início".
3. O app abre em tela cheia, com o ícone da SlickMoney, e funciona offline.

Os dados ficam salvos no próprio aparelho (localStorage).

## Gerar APK/AAB para a Play Store (opcional)
Requer Node.js e Android Studio no seu computador:
```
mkdir www && cp index.html manifest.json sw.js *.png www/
npm init -y && npm i @capacitor/core @capacitor/cli @capacitor/android
npx cap init SlickMoney com.slickmoney.app --web-dir=www
npx cap add android && npx cap sync && npx cap open android
```
Para iOS é necessário um Mac com Xcode (`@capacitor/ios`) e conta Apple Developer.

## Ainda não incluído
Login real, backend/banco de dados, sincronização entre aparelhos, Open Finance e pagamentos.

## Slick AI com Gemini (v5)
1. A pasta `api/` (com `chat.js`) PRECISA ser enviada junto, mantendo a pasta. O envio por arrastar arquivos soltos costuma perder pastas; prefira GitHub + Vercel ou a Vercel CLI (`vercel --prod`).
2. Na Vercel: Settings > Environment Variables > crie `GEMINI_API_KEY` com a SUA chave (nunca coloque a chave em arquivos). Opcional: `GEMINI_MODEL` para trocar o modelo (padrão: gemini-2.5-flash; confira o nome atual na documentação do Google).
3. Faça um novo deploy para a variável valer.
