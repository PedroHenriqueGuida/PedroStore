# PedroStore

Loja oficial de apps do **PedroOS**. O app PedroStore (dentro do PedroOS) lê o
[`index.json`](index.json) deste repositório e baixa os pacotes da pasta `pacotes/`.

> Este repositório precisa ficar **público**: o PedroOS baixa os arquivos sem login.
> A loja é **curada**: só entra aqui o que o dono da loja aprovar, porque o código de
> um app roda com o mesmo poder do sistema.

## Estrutura

```
index.json              lista de apps da loja
pacotes/
  tinta-1.0.pedroapp    pacotes dos apps (app.json + app.pck)
  imagens-1.1.pedroapp
  planilha-1.0.pedroapp
  documentos-1.0.pedroapp
  shell-1.0.pedroapp
  breakout-1.1.pedroapp
```

## index.json

```json
{
 "loja": "PedroStore",
 "apps": [
  {
   "id": "tinta",
   "nome": "Tinta",
   "versao": "1.0",
   "autor": "Pedro",
   "descricao": "…",
   "permissoes": ["world", "som"],
   "pacote": "pacotes/tinta-1.0.pedroapp",
   "sha256": "…"
  }
 ]
}
```

- `pacote`: caminho relativo a este repositório (ou um endereço completo).
- `sha256`: impressão digital do arquivo. O PedroOS confere antes de instalar; se não
  bater, recusa. O SDK mostra o sha256 quando empacota.

## Publicar um app novo
1. Crie e empacote o app com o **PedroOS App SDK** (pasta `sdk/` do projeto PedroOS).
2. Coloque o `.pedroapp` em `pacotes/`.
3. Adicione uma entrada no `index.json` com o `sha256` do pacote.
4. No PedroOS, abra a PedroStore e toque em **Atualizar lista**.

## Atualizar um app
Empacote com `versao` nova, coloque o arquivo novo em `pacotes/` e troque `versao`,
`pacote` e `sha256` no `index.json`. Quem já tem o app vê **Atualizar** na loja
(a versão nova vale quando o PedroOS reiniciar).
