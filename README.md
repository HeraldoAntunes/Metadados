# Analisador Local de Metadados e Hash de Arquivos

Aplicação web didática para análise local de metadados, hashes e informações técnicas de arquivos digitais.

O projeto foi desenvolvido para uso em aulas de **Informática Aplicada**, **Segurança da Informação**, **Privacidade Digital** e temas correlatos, especialmente em cursos como Engenharia Ambiental e Sanitária, Tecnologia, Informática Básica e disciplinas introdutórias sobre uso consciente de arquivos digitais.

A proposta é simples: o usuário seleciona ou arrasta um arquivo para a página, e a aplicação mostra quais informações invisíveis podem estar guardadas nele.

Essas informações podem incluir autoria, datas internas, software usado, dados de localização, estrutura do arquivo, assinaturas, hashes e outros rastros digitais.

---

## Objetivo do projeto

O objetivo principal é demonstrar, de forma prática e visual, que arquivos digitais podem carregar informações que normalmente não aparecem quando são abertos em programas comuns.

Um documento, uma planilha, uma apresentação ou uma foto podem expor dados como:

- nome do autor;
- último editor;
- datas de criação e modificação;
- software usado;
- empresa ou organização vinculada;
- comentários e revisões;
- caminhos internos do computador;
- coordenadas GPS em fotografias;
- links externos;
- scripts, macros ou conexões internas;
- assinatura técnica do arquivo;
- hashes criptográficos.

A ferramenta foi pensada para funcionar como uma espécie de “raio-X” didático do arquivo. Ela não substitui ferramentas profissionais de perícia digital, mas ajuda a revelar, em sala de aula, que um arquivo pode falar mais do que parece.

---

## Funcionamento local e privacidade

A aplicação funciona diretamente no navegador.

Nenhum arquivo é enviado para servidor.

Todo o processamento ocorre localmente, usando recursos do próprio navegador, como:

- File API;
- ArrayBuffer;
- TextDecoder;
- Web Crypto API;
- leitura binária local;
- processamento local de imagens;
- parsing local de estruturas como PDF, PNG, JPEG, ZIP e Office Open XML.

Isso significa que o arquivo analisado permanece no computador do usuário.

Mesmo assim, recomenda-se cuidado ao usar arquivos reais em sala de aula, pois a própria visualização dos metadados pode expor nomes, e-mails, caminhos internos ou outras informações sensíveis.

---

## Principais recursos

A aplicação permite:

- carregar arquivos por seleção manual;
- carregar arquivos por arrastar e soltar;
- analisar informações básicas do arquivo;
- identificar assinatura mágica e tipo provável;
- detectar divergência entre extensão e assinatura;
- calcular hashes do arquivo;
- extrair metadados de diferentes formatos;
- classificar metadados por sensibilidade;
- exibir um resumo dos dados mais sensíveis;
- exibir uma tabela técnica completa;
- filtrar metadados;
- copiar informações;
- exportar dados em JSON;
- exportar dados em CSV;
- gerar relatório resumido;
- visualizar explicações didáticas;
- realizar remoção experimental de metadados em alguns casos.

---

## Interface da aplicação

A interface é organizada em abas:

### 1. Resumo sensível

Mostra os dados mais relevantes para privacidade e segurança, como:

- autor;
- criador;
- proprietário;
- último editor;
- e-mail;
- empresa;
- datas internas;
- coordenadas GPS;
- dispositivo usado;
- software criador;
- comentários;
- revisões;
- macros;
- links externos;
- anexos;
- conexões externas.

Essa aba é voltada para uma leitura rápida, especialmente para usuários iniciantes ou para apresentação em sala de aula.

### 2. Dados técnicos completos

Mostra todos os metadados extraídos em uma tabela técnica.

A tabela inclui:

- categoria;
- campo;
- valor;
- origem da informação;
- tipo de dado;
- nível de sensibilidade.

Também permite busca, filtro, cópia e exportação.

### 3. Hashes e integridade

Mostra hashes criptográficos do arquivo.

A aplicação calcula, quando possível:

- SHA-256;
- SHA-1;
- SHA-512;
- MD5.

O hash funciona como uma impressão digital matemática do arquivo. Se qualquer byte do arquivo for alterado, o hash muda.

### 4. Explicação didática

Apresenta textos curtos explicando os principais grupos de metadados:

- metadados de autoria;
- metadados de tempo;
- metadados de localização;
- metadados de dispositivo;
- metadados de documentos Office;
- metadados de PDF;
- hashes;
- limpeza de metadados.

Essa seção foi pensada para apoiar aulas, oficinas e demonstrações.

### 5. Remoção experimental

Inclui funções experimentais para gerar cópias com redução de metadados em alguns formatos.

No caso de imagens, a aplicação pode regravar JPG/PNG usando canvas, o que geralmente remove EXIF, GPS e outros metadados embutidos.

No caso de documentos Office modernos, como DOCX, XLSX e PPTX, a aplicação tenta reescrever algumas propriedades internas, mas sem garantir anonimização completa.

---

## Tipos de arquivos analisados

A aplicação busca analisar, em diferentes níveis, os seguintes formatos:

### Imagens

- JPG/JPEG;
- PNG;
- GIF;
- WEBP;
- TIFF;
- BMP;
- SVG.

Em imagens, a aplicação pode extrair ou detectar informações como:

- dimensões;
- proporção;
- megapixels;
- EXIF;
- XMP;
- IPTC;
- marca da câmera;
- modelo da câmera;
- software;
- data/hora original;
- orientação;
- GPS;
- latitude;
- longitude;
- altitude;
- comentários;
- chunks internos.

### PDF

Em PDFs, a aplicação tenta identificar:

- versão do PDF;
- título;
- autor;
- assunto;
- palavras-chave;
- criador;
- produtor;
- data de criação;
- data de modificação;
- número aproximado de páginas;
- XMP;
- anexos embutidos;
- JavaScript;
- formulários;
- links externos.

A análise de PDF é local e simplificada. PDFs podem conter objetos internos complexos que não são totalmente interpretados pela aplicação.

### Documentos Office modernos

Arquivos DOCX, XLSX e PPTX são pacotes ZIP com arquivos XML internos.

A aplicação pode ler estruturas como:

- `docProps/core.xml`;
- `docProps/app.xml`;
- `docProps/custom.xml`;
- relacionamentos internos;
- comentários;
- revisões;
- nomes de planilhas;
- notas de apresentação;
- vínculos externos;
- macros ou indícios de VBA;
- propriedades personalizadas.

Formatos suportados:

- DOCX;
- XLSX;
- PPTX.

### Documentos Office antigos

Arquivos antigos como DOC, XLS e PPT usam estruturas OLE/CFB.

A aplicação detecta esse tipo de arquivo pelo cabeçalho, mas a extração completa desses metadados ainda é limitada.

### Arquivos de texto

A aplicação também pode analisar arquivos como:

- TXT;
- CSV;
- JSON;
- XML;
- HTML;
- SVG;
- MD;
- LOG;
- CSS;
- JS.

Nesses casos, pode identificar:

- codificação provável;
- presença de BOM;
- número de linhas;
- número de caracteres;
- comentários;
- links externos;
- scripts;
- metatags;
- estrutura básica do conteúdo.

---

## Classificação de sensibilidade

Os metadados são classificados em níveis de sensibilidade:

### Baixo

Dados geralmente técnicos ou estruturais, como:

- tamanho do arquivo;
- extensão;
- tipo MIME;
- assinatura;
- dimensões da imagem;
- número de páginas ou slides, quando isolado.

### Médio

Dados que podem ajudar a reconstruir a origem técnica do arquivo, como:

- software criador;
- produtor;
- versão do programa;
- datas internas;
- modelo de câmera;
- estrutura de pacote;
- informações de compressão;
- metadados XMP genéricos.

### Alto

Dados com maior potencial de exposição, como:

- nome de autor;
- proprietário;
- último editor;
- e-mail;
- caminho interno do computador;
- comentários;
- revisões;
- histórico de alterações;
- coordenadas GPS;
- links externos;
- scripts;
- macros;
- conexões externas;
- anexos embutidos.

---

## Hashes gerados

A aplicação calcula hashes para ajudar na identificação e verificação de integridade do arquivo.

### SHA-256

Hash moderno e recomendado para verificação de integridade.

### SHA-512

Hash moderno, com saída maior que o SHA-256.

### SHA-1

Mantido por compatibilidade e fins didáticos. Não deve ser usado como mecanismo criptográfico moderno de segurança.

### MD5

Mantido para comparação didática e compatibilidade com sistemas antigos. Não deve ser usado como segurança criptográfica moderna.

---

## Remoção experimental de metadados

A aplicação possui uma área de remoção experimental.

### Imagens

Para JPG e PNG, a aplicação pode regravar a imagem em canvas e gerar uma nova cópia.

Esse processo geralmente remove metadados como:

- EXIF;
- GPS;
- XMP;
- comentários embutidos.

Porém, pode alterar:

- tamanho do arquivo;
- compressão;
- qualidade visual;
- formato de saída.

### Office

Para DOCX, XLSX e PPTX, a aplicação pode tentar reescrever arquivos internos de propriedades, como:

- `docProps/core.xml`;
- `docProps/app.xml`;
- `docProps/custom.xml`.

Essa remoção é experimental.

Ela não garante anonimização completa.

Comentários, revisões, nomes internos, vínculos externos, macros, notas e outros dados podem permanecer no arquivo.

Após gerar um arquivo limpo experimental, recomenda-se analisá-lo novamente na própria aplicação.

### PDF

A aplicação detecta metadados em PDF, mas não garante remoção segura de metadados nesse formato.

Para anonimização real de PDF, recomenda-se o uso de ferramentas especializadas e validação posterior.

---

## Limitações importantes

Esta aplicação é didática.

Ela não deve ser tratada como ferramenta profissional de perícia digital, auditoria forense ou anonimização garantida.

Limitações conhecidas:

- alguns formatos possuem estruturas internas complexas;
- PDFs podem conter objetos comprimidos ou codificados;
- documentos Office podem conter dados em vários arquivos internos;
- arquivos antigos do Office não têm extração completa implementada;
- a ausência de metadados detectados não garante ausência total de metadados;
- a limpeza experimental pode ser incompleta;
- arquivos grandes podem deixar a análise lenta;
- alguns navegadores podem ter limitações no cálculo de hashes ou leitura de arquivos.

---

## Como usar

1. Baixe o arquivo HTML da aplicação.
2. Abra o arquivo diretamente no navegador.
3. Selecione ou arraste um arquivo para a área de upload.
4. Aguarde a análise.
5. Veja o resumo sensível.
6. Consulte os dados técnicos completos, se necessário.
7. Copie ou exporte os resultados.
8. Em arquivos de teste, experimente a remoção experimental.
9. Analise novamente o arquivo gerado, caso tenha usado a função de limpeza.

---

## Uso em sala de aula

Sugestões de atividades:

### Atividade 1: Metadados em fotos

Peça aos alunos que comparem fotos tiradas com celular, imagens baixadas da internet e imagens regravadas.

Questões para discutir:

- A foto contém GPS?
- Aparece modelo do celular?
- Há data e hora da captura?
- O que muda quando a imagem é regravada?

### Atividade 2: Metadados em documentos

Compare documentos DOCX criados por usuários diferentes.

Questões para discutir:

- Aparece nome do autor?
- Aparece último editor?
- Há comentários ou revisões?
- O documento expõe empresa ou organização?

### Atividade 3: Hash e integridade

Gere o hash de um arquivo, altere uma única palavra e gere novamente.

Questões para discutir:

- O hash mudou?
- O nome do arquivo mudou?
- O conteúdo visual mudou muito?
- O que isso ensina sobre integridade digital?

### Atividade 4: Extensão versus assinatura

Renomeie uma cópia de arquivo, mudando a extensão, e analise novamente.

Questões para discutir:

- A extensão mudou?
- A assinatura mudou?
- O tipo provável detectado continua o mesmo?
- Por que confiar apenas na extensão pode ser perigoso?

---

## Requisitos

A aplicação precisa apenas de um navegador moderno.

Não exige:

- servidor;
- banco de dados;
- instalação;
- internet;
- login;
- dependências externas;
- CDN.

Recomendado:

- navegador atualizado;
- arquivos de teste;
- cuidado ao usar arquivos reais com dados pessoais.

---

## Estrutura do projeto

O projeto foi organizado como arquivo único:

```text
analisador-local-metadados-hash.html
