# 🚀 Como configurar o site OxeIphone

---

## PASSO 1 — Criar a planilha no Google Sheets

1. Acesse **sheets.google.com** e crie uma nova planilha.
2. Crie **5 abas** com os nomes exatos abaixo (clique no "+" no rodapé):
   - `iPhones Lacrados`
   - `iPhones Vitrine`
   - `Produtos Apple`
   - `Outros`
   - `Xiaomi`

---

## PASSO 2 — Formato de cada aba

Cada aba deve ter essa estrutura (a 1ª linha é o cabeçalho):

| A - Modelo | B - Armazenamento | C - Condição | D - Preço | E - Preço Antigo | F - Oferta | G - Marca |
|---|---|---|---|---|---|---|
| iPhone 16 Pro Max | 256GB | Lacrado | 9799 | | | Apple |
| iPhone 15 Pro | 128GB | Vitrine | 5299 | 5699 | SIM | Apple |
| Xiaomi 14T | 256GB | Lacrado | 3999 | 4299 | SIM | Xiaomi |

**Regras:**
- Coluna **D (Preço)**: apenas números, sem R$ ou pontos. Ex: `9799`
- Coluna **E (Preço Antigo)**: preencha só quando tiver desconto, senão deixe vazio
- Coluna **F (Oferta)**: escreva `SIM` para aparecer nas "Ofertas da semana", senão deixe vazio
- Coluna **G (Marca)**: `Apple`, `Xiaomi`, `Samsung`, `Motorola`, `Acessório`, etc.
- Coluna **C (Condição)**: use exatamente `Lacrado`, `Vitrine`, `Seminovo` ou `Novo`

---

## PASSO 3 — Publicar a planilha

1. No Google Sheets, clique em **Arquivo → Compartilhar → Publicar na web**
2. Selecione **"Pasta de trabalho inteira"** e formato **"Valores separados por vírgula (.csv)"**
3. Clique em **Publicar** e confirme

---

## PASSO 4 — Pegar o ID da planilha

Na URL da sua planilha, o ID é o trecho entre `/d/` e `/edit`:

```
https://docs.google.com/spreadsheets/d/ ESTE_É_O_ID /edit#gid=0
```

Copie esse ID.

---

## PASSO 5 — Configurar o site

Abra o arquivo `index.html` em um editor de texto (Bloco de Notas, VS Code, etc.).

Procure o trecho:
```javascript
const CONFIG = {
  SHEET_ID: "COLE_O_ID_DA_SUA_PLANILHA_AQUI",
  WPP_NUMBER: "5581999999999",
  ...
}
```

Substitua:
- `COLE_O_ID_DA_SUA_PLANILHA_AQUI` → pelo ID copiado no Passo 4
- `5581999999999` → pelo número do WhatsApp do OxeIphone (com 55 + DDD + número, sem espaços)

---

## PASSO 6 — Colocar o site no ar (grátis)

### Opção A — Vercel (recomendado, mais fácil)
1. Acesse **vercel.com** e crie uma conta gratuita
2. Clique em **"Add New → Project"**
3. Arraste a pasta `oxeiphone` ou conecte ao GitHub
4. Clique em **Deploy**
5. Seu site estará em algo como `oxeiphone.vercel.app`

### Opção B — GitHub Pages (também gratuito)
1. Crie uma conta em **github.com**
2. Crie um repositório público chamado `oxeiphone`
3. Suba o arquivo `index.html`
4. Vá em **Settings → Pages → Source: main branch**
5. Seu site estará em `seuusuario.github.io/oxeiphone`

---

## PASSO 7 — Domínio próprio (opcional)

Para ter `oxeiphone.com.br`, compre o domínio no **Registro.br** (~R$40/ano) e aponte para o Vercel ou GitHub Pages seguindo as instruções deles.

---

## ✅ Como atualizar os preços toda semana

1. Abra a planilha do Google Sheets
2. Edite os preços diretamente nas células
3. Salve — o site atualiza automaticamente em segundos!

Não precisa mexer em nenhum código. ✨

---

## ❓ Dúvidas frequentes

**O site não carrega os dados?**
→ Verifique se a planilha foi publicada corretamente no Passo 3 e se o ID está certo no Passo 5.

**Como adicionar mais produtos?**
→ Basta adicionar novas linhas na planilha. O site atualiza sozinho.

**Como mudar o número do WhatsApp?**
→ Edite `WPP_NUMBER` no arquivo `index.html` na seção `CONFIG`.

**Posso ter mais de 4 ofertas em destaque?**
→ Sim! Coloque `SIM` na coluna F de quantos quiser. O site mostra os primeiros 4.
