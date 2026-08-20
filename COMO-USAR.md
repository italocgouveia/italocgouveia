# Como colocar isto no ar

Este arquivo é só instrução — **não** faz parte do perfil. Só o `README.md` aparece.

## 1. Criar o repositório especial

O GitHub só mostra o README no perfil se o repositório tiver **exatamente o mesmo nome do usuário**:

```
italocgouveia/italocgouveia
```

Em https://github.com/new:

- **Repository name:** `italocgouveia`
- **Public** (obrigatório — repositório privado não aparece no perfil)
- **Add a README file:** marque. O GitHub mostra um aviso "✨ especial" confirmando que é o repositório de perfil.

Depois é só substituir o conteúdo do README pelo daqui.

## 2. Enviar os arquivos

```bash
cd "C:/Users/Italo/Desktop/perfil-github"
git init
git add -A
git commit -m "perfil: README com tema de interface de IA"
git branch -M main
git remote add origin https://github.com/italocgouveia/italocgouveia.git
git push -u origin main --force
```

O `--force` é porque o GitHub já criou um commit inicial com o README padrão.

## 3. Ligar a Snake Animation

**A snake não é uma URL pronta.** O SVG é gerado por um GitHub Action e commitado numa branch chamada `output`. Sem isso, as imagens da seção `08` ficam quebradas.

O workflow já está em `.github/workflows/snake.yml`. Depois do push:

1. Vá em **Actions** no repositório
2. Se aparecer o aviso de workflows desativados, clique em **I understand my workflows, go ahead and enable them**
3. Selecione **Snake das contribuições** → **Run workflow**
4. Espere ~1 minuto e recarregue o perfil

Ele volta a rodar sozinho de 12 em 12 horas.

Se falhar com **403**, confira em **Settings → Actions → General → Workflow permissions** se está em **Read and write permissions**.

## 4. Os três serviços que estavam fora do ar

Na hora em que este README foi montado, testei todos os serviços externos. Dois estavam com problema, e **não é culpa da sua configuração**:

| Serviço | O que ele desenha | Status testado |
|---|---|---|
| `github-readme-stats` | Cards de estatísticas, linguagens e projetos | **503** — cota estourada |
| `github-profile-trophy` | Troféus | **402** — cota estourada |
| `streak-stats` | Sequência de dias | **sem resposta** (deu 200 num teste e parou de responder logo depois) |

São instâncias públicas gratuitas que o mundo inteiro usa; elas caem e voltam. Duas saídas:

**a) Esperar.** Costumam voltar sozinhas em algumas horas. A faixa de badges que coloquei acima dos cards continua funcionando enquanto isso, então a seção nunca fica vazia.

**b) Hospedar as suas (5 minutos, grátis, resolve pra sempre):**

1. Abra https://github.com/anuraghazra/github-readme-stats → **Deploy** → Vercel
2. Anote a URL gerada, algo como `https://stats-italo.vercel.app`
3. No `README.md`, troque todas as ocorrências de:
   ```
   https://github-readme-stats.vercel.app
   ```
   por
   ```
   https://stats-italo.vercel.app
   ```
4. Mesma coisa para os outros dois:
   - troféus → https://github.com/ryo-ma/github-profile-trophy
   - streak → https://github.com/DenverCoder1/github-readme-streak-stats

## 5. O que já foi testado e funciona

| Recurso | Status |
|---|---|
| Banner (capsule-render) | ✅ 200 |
| Typing / boot animation | ✅ 200 |
| Divisores em degradê | ✅ 200 |
| Contador de visitas (komarev) | ✅ 200 |
| Badges shields.io (todos) | ✅ 200 |
| Gráfico de atividade | ✅ 200 |
| Snake | ⚙️ depende do workflow do passo 3 |

## 6. Antes de publicar, confira

- [ ] O link do **LinkedIn** no rodapé aponta para o seu perfil de verdade
- [ ] O **Instagram** está com o usuário certo
- [ ] Os percentuais da seção `05 · OBJETIVOS` refletem onde você realmente está — eu chutei a partir do que conversamos, e número inventado num perfil é fácil de desmentir numa entrevista
- [ ] Os quatro projetos fixados são os que você quer mostrar
