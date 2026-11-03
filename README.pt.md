# SaaS Web QA Skill

[한국어](README.md) | [English](README.en.md) | [日本語](README.ja.md) | [Tiếng Việt](README.vi.md) | [Español](README.es.md) | Português | [Français](README.fr.md) | [Deutsch](README.de.md) | [Italiano](README.it.md)

Uma única skill para verificar o funcionamento de sites e serviços SaaS, interfaces responsivas e acessibilidade. Adapta seletivamente fluxos de trabalho de skills públicas da Anthropic, Vercel, Microsoft e outras fontes de QA. As instruções e listas de verificação estão incluídas; as skills originais e as respetivas ferramentas não são instaladas.

Conforme o pedido, também ajuda a planear QA com base no risco, verificar APIs, rever testes Playwright ou Cypress existentes e investigar falhas. Consulte as [fontes e o âmbito](skills/saas-web-qa/references/sources.md).

As verificações autenticadas distinguem o papel e espaço de trabalho autorizados, as listas e filtros relevantes e o âmbito da verificação de persistência. Sessões de navegador separadas ainda podem partilhar dados no servidor.

No QA por perfis, dez utilizadores simulados percorrem o serviço num navegador real. Quando possível, subagentes recolhem resultados e capturas de ecrã; se forem solicitadas correções, os percursos são repetidos. Consulte o [procedimento](skills/saas-web-qa/references/persona-journeys.md).

## Fluxo de QA

- **Diagnosticar, corrigir e verificar novamente:** Tanto no QA geral como no QA por perfis, quando são pedidas correções, os problemas no âmbito são corrigidos e o comportamento original é verificado após o serviço em execução receber as alterações. Se não for possível verificar novamente, indicam-se o motivo e o que ficou por verificar.
- **Percursos separados:** Quando são pedidas várias funções, define-se o ponto de entrada e o critério de sucesso de cada percurso. O QA por perfis regista os resultados por percurso e, para cada problema, quantos perfis puderam avaliar o passo e quantos o encontraram. Os problemas são ordenados pela frequência, destacando-se separadamente os mais graves.
- **Antes e depois do início de sessão:** Se o início de sessão estiver bloqueado mas existir uma sessão autorizada, as funções autenticadas podem ser verificadas separadamente. Não se declara sucesso num percurso completo e contínuo.

## Skills públicas de QA e práticas incorporadas

Os fluxos das sete skills ou coleções abaixo foram adaptados de forma seletiva para uma única `saas-web-qa`. Os pacotes originais, regras completas, scripts e ferramentas não são incluídos nem instalados. Consulte as ligações e o âmbito em [fontes](skills/saas-web-qa/references/sources.md).

| Skill ou coleção pública | Prática incorporada |
| --- | --- |
| Anthropic `webapp-testing` | Inspeção da página apresentada antes de verificar ações e resultados. |
| Vercel `web-design-guidelines` | Revisão de UI, usabilidade, interação e acessibilidade. |
| Microsoft `playwright-cli` | Fluxos de interação com o navegador e automação. |
| `qa-skills` | Planeamento baseado em risco, QA exploratório, verificação de API e reporte de defeitos. |
| `e2e-skills` | Revisão da qualidade dos testes E2E existentes e investigação de falhas. |
| TestDino `playwright-skill` | Testes de navegador com a configuração Playwright existente do projeto. |
| `cypress-agent-skill` | Testes de navegador com a configuração Cypress existente do projeto. |

## Pedir a um agente que instale e execute a skill

Envie um pedido como este ao seu agente de programação. O repositório tem de estar publicado no GitHub e acessível ao agente.

```text
Instale a skill saas-web-qa de https://github.com/Fhwang0926/saas-qa-skills
no projeto atual, leia as instruções e realize o QA abaixo.
Se já estiver instalada, confirme que suporta a tarefa pedida antes de a utilizar.

Alvo: página de início de sessão do projeto atual
Âmbito: apresentação em computador e telemóvel, início de sessão e acessibilidade
```

Para apenas instalar, peça a instalação sem solicitar QA. O agente pode precisar de uma nova sessão para detetar a skill; se conseguir ler os ficheiros instalados, pode seguir as instruções na sessão atual.

### Instruções para agentes

1. Identifique o projeto e o agente e leia as instruções do utilizador e do projeto. Se `saas-web-qa` estiver instalada, leia `SKILL.md` e as referências relevantes e confirme que suportam a tarefa; não presuma que o nome significa que está atualizada. Reutilize-a se for suficiente. Se faltar uma função, verifique a fonte acessível deste repositório, a origem da instalação e alterações locais; atualize segundo as regras sem substituir trabalho que não possa ser alterado em segurança. Se a atualização não for segura, utilize diretamente as instruções da fonte quando possível. Informe se não houver acesso ou se a função faltar.
2. Se for necessário instalar, execute o comando abaixo no projeto de destino. Se não houver seleção interativa e o agente for conhecido, selecione apenas esse agente; para Codex, acrescente `--agent codex -y`. Não acrescente `-g` a menos que seja pedida uma instalação global. Respeite as permissões e regras de ferramentas do ambiente.
3. Verifique o resultado e o caminho da instalação e leia `SKILL.md` e os ficheiros relevantes em `references/`. Se a skill não estiver registada na sessão mas os ficheiros puderem ser lidos, siga-os diretamente. Não execute QA se apenas tiver sido pedida a instalação.
4. Dê prioridade ao serviço em execução e ao navegador disponível. Siga as regras do utilizador e do projeto para builds, testes, arranque de servidores, bases de dados e serviços externos. Se faltarem ferramentas ou acesso, comunique o bloqueio e o âmbito realizado; não declare sucesso sem evidência.

## Instalação direta

Após a publicação do repositório, execute no projeto de destino. É necessário Node.js 22.20 ou superior; selecione o agente quando solicitado.

```bash
npx skills add Fhwang0926/saas-qa-skills --skill saas-web-qa
```

Para instalar a partir de uma cópia local, substitua o caminho pela localização real:

```bash
npx skills add /path/to/saas-qa-skills --skill saas-web-qa
```

Por predefinição, a instalação aplica-se ao projeto. Acrescente `-g` para instalar globalmente. Reinicie o agente se necessário para detetar a skill.

## Utilização

```text
$saas-web-qa Verifique a página de início de sessão em computador e telemóvel e indique os problemas reproduzíveis.
```

### Diagnosticar, corrigir e verificar novamente num pedido

```text
$saas-web-qa Analise o serviço em execução com dez perfis de utilizador simulados.
Quando possível, use subagentes separados e verifique num navegador real as páginas
públicas e as funções principais após iniciar sessão com uma conta autorizada.
Capture os pontos confusos ou bloqueados e indique, para cada problema, quantos
perfis chegaram ao passo e quantos o encontraram. Corrija em conjunto os problemas
confirmados, repita os percursos em condições comparáveis e indique o que foi
resolvido e o que permanece.
```

A skill fornece instruções, não um navegador, Playwright, uma aplicação em execução ou contas. As verificações reais exigem ambiente e acesso adequados. As regras do utilizador e do projeto prevalecem.
