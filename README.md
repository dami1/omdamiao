# OMDamião

Patcher de composição assistida que roda no navegador, com bibliotecas do OpenMusic portadas para JavaScript
(OMTristan, Profile, OMRC, Esquisse, Alea, Chaos, OM-JI, RepMus, MathTools, OMScoreTools, Filters, Pareto, Situation, RQ) e uma biblioteca de jazz.

O site é um arquivo, `index.html`, com o código, os estilos e as fontes embutidos. Só os modelos de rede neural do
Magenta ficam fora, na pasta `magenta/`, e são lidos quando um objeto Magenta é usado.

## Publicar no GitHub Pages

1. Crie um repositório no GitHub (por exemplo `omdamiao`).
2. Envie para a raiz dele tudo o que há nesta pasta: `index.html`, `.nojekyll`, `README.md` e a pasta `magenta/`
   (os pesos dos modelos MelodyRNN e DrumsRNN, 25 MB; sem ela os objetos Continue pedem o modelo a quem usa).
3. No repositório, abra **Settings → Pages**. Em **Build and deployment**, escolha **Deploy from a branch**,
   o ramo `main` e a pasta `/ (root)`, e salve.
4. Em um ou dois minutos o site fica em `https://SEU-USUARIO.github.io/omdamiao/`.

O arquivo `.nojekyll` (vazio) diz ao GitHub para servir os arquivos como estão, sem passar pelo Jekyll.
Se preferir manter o site numa pasta `docs/`, coloque os arquivos lá e escolha `/docs` no passo 3.

## Observações

- O patch em edição fica guardado no navegador de quem usa (localStorage), separado por endereço.
- A exportação de MIDI baixa um `.zip` direto pelo navegador.
- A importação de MIDI e de áudio lê os arquivos localmente; nada é enviado a servidor algum.

## Fontes embutidas

VT323, Silkscreen e Noto Music, todas sob a SIL Open Font License 1.1.

## Código de terceiros embutido

A transcrição de áudio usa o Basic Pitch (Spotify AB, 2022) e o TensorFlow.js (Google), ambos sob a licença Apache 2.0.
O modelo e a biblioteca estão dentro do `index.html`; nada é baixado nem enviado durante o uso.
- **Magenta** (Google, Apache 2.0): os pesos em `magenta/music_rnn/` são os checkpoints originais `melody_rnn` e `drum_kit_rnn`;
  as contas da rede foram reescritas em JavaScript a partir do magenta-js.
- **Situation** (A. Bonnet, C. Rueda, IRCAM; GPL v3): o código Lisp original vai embutido e roda num interpretador próprio.
- **Matter.js 0.20** (Liam Brummitt, MIT): motor de física embutido, usado pelos objetos do grupo Matter.
- **RQ** (A. Ycart, F. Jacquemard, J. Bresson, IRCAM; GPL v3): o código Lisp original do algoritmo de quantificação rítmica vai embutido e roda no mesmo interpretador.
