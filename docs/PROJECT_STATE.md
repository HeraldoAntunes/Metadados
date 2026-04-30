# Estado Operacional do Projeto

Última atualização: 2026-04-30, America/Fortaleza.

## Objetivo do Projeto

O projeto é uma aplicação web didática para análise local de metadados, assinaturas técnicas, hashes e indícios de exposição em arquivos digitais. O foco é apoiar aulas e demonstrações sobre privacidade digital, segurança da informação, integridade de arquivos e uso consciente de documentos.

A aplicação deve funcionar diretamente no navegador, sem envio de arquivos para servidor e sem dependências externas.

## Estado Atual

- Aplicação existente em arquivo único: `analisador-local-metadados-hash.html`.
- Interface e documentação em português do Brasil.
- O processamento descrito e implementado é local, usando APIs do navegador.
- Não há sistema de build, servidor, pacote de dependências, testes automatizados ou CI configurados.
- Não havia `AGENTS.md`, `docs/HANDOFF.md`, `docs/PROJECT_STATE.md`, `docs/` ou `.gitignore` antes da atualização de arquitetura de contexto.
- A arquitetura documental para agentes foi criada nesta atualização.
- O arquivo funcional `analisador-local-metadados-hash.html` não foi alterado nesta atualização documental.

## Estrutura Real do Repositório

```text
.
├── AGENTS.md
├── LICENSE
├── README.md
├── analisador-local-metadados-hash.html
└── docs
    ├── HANDOFF.md
    └── PROJECT_STATE.md
```

## Arquivos Principais

- `analisador-local-metadados-hash.html`: aplicação completa em HTML, CSS e JavaScript. Contém a interface, leitura local de arquivos, extração de metadados, cálculo de hashes, classificação de sensibilidade, exportações e rotinas experimentais de limpeza.
- `README.md`: documentação humana do projeto, objetivos, recursos, limitações, modo de uso e arquitetura de contexto.
- `AGENTS.md`: guia permanente para agentes de IA com hierarquia de contexto, rotinas de leitura e encerramento, segurança, Git e conduta.
- `docs/PROJECT_STATE.md`: memória operacional viva do projeto.
- `docs/HANDOFF.md`: documento autocontido de passagem de contexto para outro chat, agente ou sessão.
- `LICENSE`: licença MIT.

## Decisões em Vigor

- `docs/PROJECT_STATE.md` é a memória operacional contínua do projeto.
- `docs/HANDOFF.md` é documento de transferência de contexto, não diário operacional.
- `AGENTS.md` contém regras estáveis e não deve ser alterado automaticamente no futuro sem pedido explícito.
- O app permanece como arquivo único, sem servidor, sem login, sem internet obrigatória, sem CDN e sem dependências externas.
- Projetos pequenos e médios neste repositório devem usar arquitetura suficiente: evitar overengineering, camadas e padrões formais sem necessidade real documentada.
- Nenhum arquivo analisado pelo usuário deve ser enviado para servidor.
- A remoção de metadados é experimental e não deve ser apresentada como anonimização garantida.
- A ausência de metadados detectados não deve ser documentada como prova de ausência total de metadados.
- Dados sensíveis, documentos reais de alunos, documentos institucionais sensíveis, logs e arquivos temporários não devem ser adicionados ao repositório.

## Limitações Conhecidas

- PDFs podem conter objetos comprimidos, codificados ou estruturas complexas que a extração local simplificada não interpreta completamente.
- Arquivos Office modernos podem conter metadados em vários arquivos internos, comentários, revisões, vínculos, macros e nomes internos.
- Arquivos Office antigos em OLE/CFB são detectados, mas a extração completa de metadados antigos não está implementada.
- A limpeza experimental de imagens pode alterar compressão, tamanho, qualidade e formato.
- A limpeza experimental de Office pode ser incompleta e pode gerar novas datas internas no arquivo produzido.
- Arquivos grandes podem deixar a análise lenta no navegador.
- Alguns navegadores podem limitar APIs de hash, clipboard, leitura local ou geração de arquivos.
- Não há testes automatizados registrados no repositório.

## Testes Feitos

- Inspeção do repositório com `rg --files`.
- Verificação de estado Git com `git status --short`.
- Busca por referências antigas a `HANDOFF`, `PROJECT_STATE`, `AGENTS`, `Codex`, `OpenCode`, `agente` e `IA`; nenhuma referência antiga foi encontrada.
- Leitura do `README.md`, `LICENSE` e inspeção estrutural do HTML principal.
- Confirmação de que não existiam `AGENTS.md`, `docs/HANDOFF.md`, `docs/PROJECT_STATE.md`, `docs/` ou `.gitignore` antes da criação desta arquitetura.
- Verificação posterior com `git status --short`: alterações restritas a `README.md`, `AGENTS.md` e `docs/`.
- Verificação posterior com `git diff --check`: sem erros de whitespace; houve apenas aviso de conversão LF/CRLF do `README.md` no Windows.
- Leitura de `README.md`, `AGENTS.md`, `docs/PROJECT_STATE.md` e `docs/HANDOFF.md` antes de atualizar a diretriz permanente de simplicidade arquitetural.

## Testes Pendentes

- Abrir `analisador-local-metadados-hash.html` em navegador moderno e validar fluxo básico de seleção de arquivo.
- Testar amostras sintéticas de JPG/PNG com e sem EXIF/GPS.
- Testar PDF simples, PDF com metadados e PDF com estruturas comprimidas.
- Testar DOCX, XLSX e PPTX sintéticos com propriedades, comentários, revisões, vínculos e macros apenas de teste.
- Validar exportação JSON, CSV e TXT.
- Validar cópia para clipboard em navegadores diferentes.
- Validar limpeza experimental de imagem e Office com reanálise posterior do arquivo gerado.

## Próximos Passos

1. Fazer uma verificação manual da aplicação no navegador com arquivos sintéticos.
2. Registrar resultados relevantes de testes neste arquivo.
3. Se o projeto crescer, decidir se continuará como HTML único ou se precisará de estrutura modular.
4. Se forem adicionadas dependências, documentar motivação, instalação e impacto no funcionamento local.
5. Manter `README.md` para pessoas, `AGENTS.md` para regras permanentes, `PROJECT_STATE.md` para estado vivo e `HANDOFF.md` para transferências.

## Instrução de Retomada Rápida

Para retomar o projeto, leia nesta ordem:

1. `README.md`;
2. `AGENTS.md`;
3. `docs/PROJECT_STATE.md`;
4. `docs/HANDOFF.md`, se a tarefa envolver transferência ou continuidade de sessão;
5. `analisador-local-metadados-hash.html` ou o arquivo diretamente ligado à tarefa.

Depois disso, rode `git status --short`, confirme se há alterações do usuário e só então edite.
