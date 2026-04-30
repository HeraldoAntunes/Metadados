# Guia Para Agentes de IA

Este arquivo define regras permanentes para agentes que trabalham neste repositório. Ele não é diário de bordo, não é memória operacional e não deve ser alterado automaticamente em tarefas futuras sem pedido explícito do usuário.

## Hierarquia de Contexto

Ao decidir como agir, use esta ordem de prioridade:

1. Instrução explícita do usuário na conversa atual.
2. `AGENTS.md`.
3. `docs/PROJECT_STATE.md`.
4. `docs/HANDOFF.md`.
5. `README.md`.
6. Código real do projeto como fonte final de comportamento executável.

`docs/HANDOFF.md` não substitui `docs/PROJECT_STATE.md`. O handoff é documento de transferência para outro chat, agente ou sessão. O estado operacional contínuo do projeto fica em `docs/PROJECT_STATE.md`.

## Rotina de Leitura

Ao iniciar qualquer tarefa não trivial, leia:

1. `README.md`.
2. `AGENTS.md`.
3. `docs/PROJECT_STATE.md`.
4. `docs/HANDOFF.md`, se a tarefa envolver retomada de contexto, passagem para outro chat ou continuidade de sessão.
5. Arquivos diretamente relacionados à tarefa.

Depois da leitura, confirme a estrutura real do repositório antes de editar. Não presuma que a documentação está mais atualizada que o código.

## Rotina de Encerramento

Ao finalizar uma alteração relevante:

1. Avalie se `docs/PROJECT_STATE.md` precisa ser atualizado.
2. Atualize `docs/PROJECT_STATE.md` quando houver mudança de estado, decisão, comportamento, limitação, teste ou próximo passo.
3. Atualize `docs/HANDOFF.md` quando o usuário pedir handoff ou quando a tarefa gerar um ponto claro de passagem para outro chat ou agente.
4. Recomende atualização do `AGENTS.md` quando regras permanentes tiverem mudado, mas não altere `AGENTS.md` sem pedido explícito.
5. Informe os arquivos alterados e os testes ou verificações feitos.

## Arquitetura do Projeto

Este projeto é uma aplicação web didática de arquivo único:

- `analisador-local-metadados-hash.html`: aplicação completa com HTML, CSS e JavaScript.
- `README.md`: guia humano do projeto.
- `AGENTS.md`: regras permanentes para agentes de IA.
- `docs/PROJECT_STATE.md`: memória operacional viva do projeto.
- `docs/HANDOFF.md`: passagem de contexto para outro chat, agente ou sessão.
- `LICENSE`: licença MIT.

A aplicação deve continuar funcionando diretamente no navegador, sem servidor, sem build, sem dependências externas e sem CDN, salvo decisão explícita em contrário.

## Simplicidade Arquitetural

Use arquitetura suficiente para o problema real atual. Este projeto deve priorizar funcionalidade, clareza, manutenção simples e baixo custo de contexto para pessoas e agentes de IA.

- Prefira a solução mais simples que resolva o problema atual.
- Preserve o funcionamento local, direto e sem dependências desnecessárias.
- Não crie camadas, interfaces, DTOs, mappers, factories, services, use cases ou patterns apenas por convenção.
- Não introduza Clean Architecture completa, arquitetura hexagonal, CQRS, event sourcing, microservices, DDD tático completo, repository pattern formal ou dependency inversion sem justificativa explícita.
- Separe responsabilidades de forma simples, sem multiplicar arquivos desnecessariamente.
- Prefira encapsulamento simples antes de interfaces formais.
- Não crie interface para algo que tem apenas uma implementação, salvo necessidade real documentada.
- Não reorganize o projeto inteiro sem pedido explícito.
- Comece simples e abstraia apenas quando houver dor concreta.
- Considere que cada arquivo, camada e indireção aumenta custo de leitura, revisão e contexto para agentes de IA.
- Mantenha lógica de negócio separada de detalhes de interface, DOM, HTTP, armazenamento local, arquivos ou integrações quando isso for aplicável, mas sem cerimônia arquitetural desnecessária.

Antes de criar nova abstração, responda:

- Esta abstração resolve um problema real já existente?
- Há pelo menos dois usos concretos?
- Ela reduz duplicação ou só espalha código?
- Ela facilita teste e manutenção ou aumenta navegação?
- O custo em arquivos, imports e contexto compensa?
- Se a resposta for duvidosa, mantenha simples.

## Regras de Trabalho

- Não altere arquivos de código em tarefas documentais, exceto quando houver referência quebrada que exija ajuste mínimo.
- Preserve a proposta local e didática do projeto: nenhum arquivo analisado deve ser enviado para servidor.
- Prefira mudanças pequenas, legíveis e compatíveis com a estrutura de arquivo único.
- Não introduza dependências externas sem justificar a necessidade e sem autorização do usuário.
- Não trate a ferramenta como solução profissional de perícia digital, auditoria forense ou anonimização garantida.
- Se alterar comportamento do app, atualize a documentação humana e o estado operacional quando pertinente.
- Use o código real como fonte final para confirmar comportamento executável.

## Segurança e Dados Sensíveis

Não incluir no repositório:

- chaves de API;
- tokens;
- senhas;
- credenciais;
- dados pessoais;
- dados reais sensíveis;
- documentos de alunos;
- documentos institucionais sensíveis;
- logs;
- arquivos temporários.

Use apenas arquivos sintéticos, públicos ou explicitamente autorizados para testes. Ao documentar testes, descreva o tipo de arquivo usado sem registrar conteúdo sensível.

## Git

- Não faça commit automaticamente.
- Verifique `git status` antes e depois de alterações relevantes.
- Não reverta mudanças do usuário sem pedido explícito.
- Não coloque `AGENTS.md`, `docs/PROJECT_STATE.md` ou `docs/HANDOFF.md` no `.gitignore`.
- Ao sugerir commit, prefira uma mensagem objetiva que descreva a mudança documental ou funcional.

## Conduta do Agente

- Responda em português quando o usuário escrever em português.
- Seja direto, técnico e acionável.
- Antes de editar, leia o contexto suficiente para entender o impacto.
- Registre decisões duráveis em `docs/PROJECT_STATE.md`, não em `docs/HANDOFF.md`.
- Use `docs/HANDOFF.md` apenas para transferência de contexto.
