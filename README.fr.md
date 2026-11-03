# SaaS Web QA Skill

[한국어](README.md) | [English](README.en.md) | [日本語](README.ja.md) | [Tiếng Việt](README.vi.md) | [Español](README.es.md) | [Português](README.pt.md) | Français | [Deutsch](README.de.md) | [Italiano](README.it.md)

Une seule skill pour examiner le fonctionnement des sites et services SaaS, les interfaces adaptatives et l'accessibilité. Elle adapte une sélection de méthodes issues des skills publiques d'Anthropic, Vercel, Microsoft et d'autres sources QA. Les instructions et listes de contrôle sont incluses ; les skills d'origine et leurs outils ne sont pas installés.

Selon la demande, elle aide aussi à planifier la QA selon les risques, vérifier les API, examiner les tests Playwright ou Cypress existants et analyser les échecs. Voir les [sources et le périmètre](skills/saas-web-qa/references/sources.md).

Les vérifications après connexion distinguent le rôle et l'espace de travail autorisés, les listes et filtres concernés et le périmètre de vérification de la persistance. Des sessions de navigateur séparées peuvent partager les données du serveur.

Pour la QA par profils, dix utilisateurs simulés parcourent le service dans un vrai navigateur. Lorsque c'est possible, des sous-agents recueillent les constats et captures ; si des corrections sont demandées, les parcours sont répétés. Voir la [procédure](skills/saas-web-qa/references/persona-journeys.md).

## Déroulement de la QA

- **Diagnostiquer, corriger et vérifier à nouveau :** Pour la QA générale comme pour la QA par profils, les corrections demandées sont effectuées dans le périmètre prévu, puis le comportement initial est vérifié lorsque le service en cours a pris en compte les changements. Si cette vérification est impossible, sa raison et les points non vérifiés sont indiqués.
- **Parcours distincts :** Pour plusieurs fonctionnalités, un point d'entrée et un critère de réussite sont définis pour chaque parcours. La QA par profils sépare les résultats et indique, pour chaque problème, le nombre de profils ayant pu évaluer l'étape et le nombre concerné. Les problèmes sont classés par fréquence, les plus graves étant signalés séparément.
- **Avant et après connexion :** Si la connexion est bloquée mais qu'une session autorisée existe, les fonctions authentifiées peuvent être vérifiées séparément. Cela ne permet pas de déclarer réussi le parcours complet sans interruption.

## Skills QA publiques et pratiques intégrées

Les méthodes des sept skills ou collections ci-dessous ont été adaptées de façon sélective dans une seule `saas-web-qa`. Les paquets d'origine, leurs règles complètes, scripts et outils ne sont ni inclus ni installés. Voir les liens et le périmètre dans les [sources](skills/saas-web-qa/references/sources.md).

| Skill ou collection publique | Pratique intégrée |
| --- | --- |
| Anthropic `webapp-testing` | Inspection des pages rendues avant vérification des actions et résultats. |
| Vercel `web-design-guidelines` | Revue de l'UI, de l'utilisabilité, des interactions et de l'accessibilité. |
| Microsoft `playwright-cli` | Méthodes d'interaction avec le navigateur et d'automatisation. |
| `qa-skills` | Planification selon les risques, QA exploratoire, vérification d'API et signalement des défauts. |
| `e2e-skills` | Revue de qualité des tests E2E existants et analyse des échecs. |
| TestDino `playwright-skill` | Tests navigateur avec la configuration Playwright existante du projet. |
| `cypress-agent-skill` | Tests navigateur avec la configuration Cypress existante du projet. |

## Demander à un agent d'installer et d'exécuter la skill

Transmettez une demande comme celle-ci à votre agent de développement. Le dépôt doit être publié sur GitHub et accessible à l'agent.

```text
Installe la skill saas-web-qa depuis https://github.com/Fhwang0926/saas-qa-skills
dans le projet actuel, lis ses instructions et effectue la QA ci-dessous.
Si elle est déjà installée, vérifie qu'elle prend en charge la tâche avant de l'utiliser.

Cible : page de connexion du projet actuel
Périmètre : affichage ordinateur et mobile, connexion et accessibilité
```

Pour installer uniquement, demandez l'installation sans demander de QA. Une nouvelle session peut être nécessaire pour détecter la skill ; si l'agent peut lire les fichiers installés, il peut suivre leurs instructions dans la session actuelle.

### Instructions pour les agents

1. Identifiez le projet cible et l'agent, puis lisez les consignes de l'utilisateur et du projet. Si `saas-web-qa` est installée, lisez `SKILL.md` et les références utiles et vérifiez qu'ils couvrent la tâche ; ne supposez pas qu'elle est à jour d'après son nom. Réutilisez-la si elle suffit. Sinon, examinez la source accessible de ce dépôt, l'origine de l'installation et les modifications locales ; mettez à jour selon les règles sans écraser un travail qui ne peut pas être remplacé sans risque. Si la mise à jour n'est pas sûre, utilisez directement les instructions de la source lorsque c'est possible. Signalez une source inaccessible ou une fonction absente.
2. Si nécessaire, exécutez la commande ci-dessous dans le projet cible. Si la sélection interactive est impossible et que l'agent est connu, sélectionnez uniquement cet agent ; pour Codex, ajoutez `--agent codex -y`. N'ajoutez pas `-g` sans demande d'installation globale. Respectez les droits et règles d'utilisation des outils.
3. Vérifiez le résultat et le chemin d'installation, puis lisez `SKILL.md` et les fichiers utiles de `references/`. Si la skill n'est pas enregistrée dans la session mais que ses fichiers sont lisibles, suivez-les directement. N'effectuez pas de QA si seule l'installation a été demandée.
4. Privilégiez le service en cours d'exécution et le navigateur disponible. Respectez les règles de l'utilisateur et du projet concernant les builds, tests, démarrages de serveur, bases de données et services externes. Si un outil ou un accès manque, indiquez le blocage et le travail effectué sans affirmer une réussite non vérifiée.

## Installation directe

Après publication du dépôt, exécutez cette commande dans le projet cible. Node.js 22.20 ou plus récent est requis ; sélectionnez l'agent à l'invite.

```bash
npx skills add Fhwang0926/saas-qa-skills --skill saas-web-qa
```

Pour installer depuis une copie locale, remplacez le chemin par son emplacement réel :

```bash
npx skills add /path/to/saas-qa-skills --skill saas-web-qa
```

Par défaut, l'installation concerne le projet. Ajoutez `-g` pour une installation globale. Redémarrez l'agent si nécessaire pour détecter la skill.

## Utilisation

```text
$saas-web-qa Examine la page de connexion sur ordinateur et mobile et signale les problèmes reproductibles.
```

### Diagnostiquer, corriger et vérifier à nouveau en une demande

```text
$saas-web-qa Examine le service en cours d'exécution avec dix profils d'utilisateurs simulés.
Utilise des sous-agents distincts si possible et vérifie dans un vrai navigateur
les pages publiques et les fonctions principales avec un compte autorisé.
Capture les points de confusion ou de blocage et indique, pour chaque problème,
combien de profils ont atteint l'étape et combien l'ont rencontré. Corrige ensemble
les problèmes confirmés, répète les parcours dans des conditions comparables
et indique ce qui est résolu et ce qui reste à traiter.
```

La skill fournit des instructions, mais pas de navigateur, de Playwright, d'application en cours d'exécution ni de comptes. Les vérifications réelles nécessitent l'environnement et les accès appropriés. Les règles de l'utilisateur et du projet prévalent.
