# ICTRP → Zotero (XML → RIS)

Ferramenta de conversão local de registros exportados em XML da **WHO International Clinical Trials Registry Platform (ICTRP)** para o formato RIS, visando à importação no Zotero e, posteriormente, em ferramentas de triagem como o Rayyan.

> **Status:** protótipo funcional. Foi utilizado com êxito em pelo menos uma exportação real, mas ainda precisa de uma validação sistemática antes de ser descrito como plenamente validado para todas as variantes de exportações do ICTRP.

## Acesso e execução

Abra `index.html` em um navegador moderno ou acesse o site configurado pelo GitHub Pages. Selecione o XML original, confira as opções de resumo sintético e preservação de campos, execute a conversão e baixe o RIS. Em seguida, no Zotero, use **Arquivo → Importar → Um arquivo**.

Toda a conversão é feita no navegador. O programa não possui chamadas de rede para transmitir o conteúdo do XML. O GitHub Pages hospeda o código público da ferramenta, mas não recebe o arquivo XML enviado pelo usuário à interface.

## Publicar com GitHub Pages

1. Crie uma conta gratuita em https://github.com/, caso ainda não tenha.
2. Crie um repositório **público** chamado `ictrp-zotero-converter` (ou outro nome que preferir).
3. Faça upload dos arquivos `index.html`, `.nojekyll` e `README.md` **na raiz do repositório**, não da pasta/ZIP inteiro como único arquivo.
4. Em **Settings → Pages → Build and deployment**, selecione **Deploy from a branch**. Depois escolha `main` e `/(root)` e salve.
5. O endereço esperado será `https://SEU-USUARIO.github.io/ictrp-zotero-converter/`, substituindo `SEU-USUARIO` pelo login do GitHub e o nome do repositório pelo nome exato escolhido.

A URL não existe até que o repositório seja criado e o GitHub Pages publicado.

## Mapeamento resumido

- `Scientific_title` (alternativa `Public_title`) → RIS `TI` (título).
- `TrialID` → RIS `AN` + nota (`N1`).
- `Date_registration3` ou `Date_registration` → RIS `DA` (data de registro, **não** de publicação).
- `Brief_summary`, `Abstract` ou campos equivalentes → RIS `AB`, se disponíveis.
- Se não houver resumo original e a opção for selecionada, `AB` será uma **síntese identificada**, composta apenas de campos existentes. Essa síntese **não deve ser citada como resumo escrito pelos autores**.
- Demais campos disponíveis → notas RIS `N1` se marcada a opção de preservação.
- Tipo RIS → `RPRT` (relatório de registro de ensaio; não equivale a artigo).

## Limitações e controle de qualidade

- Confira o número de registros e a integridade de títulos, IDs e desfechos antes da triagem.
- Exportações do ICTRP podem variar na estrutura e nos nomes dos campos: variantes desconhecidas talvez precisem de ajustes no código.
- Não há garantia de deduplicação entre registros distintos do mesmo estudo.
- O resumo sintético é uma facilitação de triagem, não um resumo original do estudo.
- A validação em um arquivo real é uma demonstração de uso, **não** equivale a avaliação formal de sensibilidade, completude ou acurácia.

## Contribuição e transparência

Protótipo criado com **assistência substancial de IA generativa (ChatGPT)** a partir de uma demanda concreta de pesquisadora por interoperabilidade entre ICTRP, Zotero e Rayyan. Para uma publicação científica formal, os responsáveis devem documentar e declarar as contribuições humanas, a participação da IA, a revisão do código e a verificação sistemática dos resultados.

## Licença

**Ainda não foi escolhida uma licença de código aberto.** Antes de distribuir oficialmente como projeto open source, selecione e adicione uma licença compatível com o objetivo do projeto (por exemplo, MIT) e esclareça a titularidade e os créditos. Publicar um repositório publicamente não significa automaticamente que ele esteja licenciado para reutilização.

## Natureza do projeto

Projeto independente. Não afiliado, aprovado ou endossado pela OMS, pelo Zotero ou pelo Rayyan.
