# Handoff do Projeto

## Tema

Arquitetura de contexto e documentação operacional para o projeto "Analisador Local de Metadados e Hash de Arquivos".

## Status

Arquitetura documental criada e padronizada para uso com Codex, OpenCode e outros agentes de IA. O projeto passou a separar documentação humana, regras permanentes para agentes, memória operacional viva e documento de transferência.

## Complexidade

Baixa a média. O repositório é pequeno e a aplicação é um HTML único, mas o arquivo principal concentra todo o comportamento do app e exige cuidado para não misturar documentação operacional com regras permanentes.

## Objetivo

Manter uma aplicação didática que analisa localmente metadados, assinaturas de arquivo, hashes e indícios de exposição em arquivos digitais. A aplicação deve continuar funcionando diretamente no navegador, sem servidor, sem envio de arquivos e sem dependências externas.

## Estado Atual

- Branch atual observada durante a atualização: `main`.
- App principal: `analisador-local-metadados-hash.html`.
- Documentação humana: `README.md`.
- Regras permanentes para IA: `AGENTS.md`.
- Memória operacional contínua: `docs/PROJECT_STATE.md`.
- Documento de passagem de contexto: `docs/HANDOFF.md`.
- Licença: MIT em `LICENSE`.
- Não há build, servidor, gerenciador de pacotes, testes automatizados ou CI configurados.

## Artefatos Principais

- `analisador-local-metadados-hash.html`: interface, estilos e lógica JavaScript. Implementa leitura local de arquivos, detecção de assinatura, hashes SHA-256/SHA-1/SHA-512/MD5, extração de metadados para imagens, PDF, Office Open XML e textos, classificação de sensibilidade, exportações e limpeza experimental.
- `README.md`: guia para pessoas, com objetivo, funcionamento local, recursos, formatos, limitações, uso em sala e arquitetura de contexto.
- `AGENTS.md`: hierarquia de contexto, rotinas de leitura e encerramento, regras de segurança, Git e conduta para agentes.
- `docs/PROJECT_STATE.md`: estado vivo com estrutura, decisões, limitações, testes feitos, pendências e retomada rápida.
- `docs/HANDOFF.md`: este documento, destinado a levar contexto para outra sessão.

## Decisões Tomadas

- `docs/PROJECT_STATE.md` substitui qualquer uso antigo de `docs/HANDOFF.md` como memória operacional.
- `docs/HANDOFF.md` fica reservado para transferência de contexto entre chats, agentes ou sessões.
- `AGENTS.md` é guia permanente e não deve ser editado automaticamente no futuro sem pedido explícito do usuário.
- A hierarquia de contexto definida é: instrução explícita do usuário, `AGENTS.md`, `docs/PROJECT_STATE.md`, `docs/HANDOFF.md`, `README.md` e código real.
- O projeto deve evitar overengineering: usar arquitetura suficiente, começar simples e só criar abstrações quando houver necessidade real documentada.
- O projeto deve permanecer livre de segredos, dados pessoais, documentos reais sensíveis, logs e arquivos temporários.
- A documentação deve evitar prometer anonimização, perícia digital completa ou ausência total de metadados quando a ferramenta apenas não detecta algo.

## Questões Abertas

- Ainda falta validação manual recente no navegador após esta atualização documental.
- Não há suíte automatizada para regressão do HTML.
- Ainda não há amostras sintéticas versionadas para testes didáticos.
- Se o app crescer, será preciso decidir se continua como HTML único ou se migra para uma estrutura modular.

## Restrições

- Não fazer commit automaticamente.
- Não alterar código nesta tarefa documental, salvo ajuste mínimo de referência documental quebrada.
- Não adicionar chaves, tokens, senhas, credenciais, dados pessoais, documentos de alunos, documentos institucionais sensíveis, logs ou temporários.
- Não colocar `AGENTS.md`, `docs/PROJECT_STATE.md` ou `docs/HANDOFF.md` no `.gitignore`.
- Não introduzir dependências externas sem autorização explícita.
- Preservar funcionamento local no navegador.

## Estilo e Preferências Relevantes do Usuário

O projeto documenta uma preferência clara por linguagem didática, em português do Brasil, com foco em sala de aula, privacidade digital, segurança da informação e explicações acessíveis. Não há preferências pessoais adicionais do usuário registradas no repositório.

## Próximo Passo Recomendado

Revisar o diff documental e, depois, abrir `analisador-local-metadados-hash.html` em um navegador moderno para validar o fluxo básico com arquivos sintéticos. Em seguida, registrar qualquer resultado relevante em `docs/PROJECT_STATE.md`.

## Instruções Para a Próxima IA

1. Leia `README.md`, `AGENTS.md` e `docs/PROJECT_STATE.md` antes de editar.
2. Leia este `docs/HANDOFF.md` se estiver retomando de outra sessão ou preparando nova passagem.
3. Rode `git status --short` e preserve alterações existentes do usuário.
4. Para mudanças documentais, mantenha `docs/PROJECT_STATE.md` como memória viva e use este handoff apenas para transferência.
5. Para mudanças no app, evite camadas e padrões formais sem necessidade real; inspecione o trecho relevante de `analisador-local-metadados-hash.html`, valide manualmente quando possível e atualize a documentação afetada.
