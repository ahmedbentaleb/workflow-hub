# Workflow — hub

`2026-09-24 19:27` UTC · branche `cursor/cloud-agent-1789332190597-33bq8` · tag `—` · ⚠️ 15 fichiers non commités

| Tests | Reste | En cours | Fait | Décisions en attente | Sessions |
|---|---|---|---|---|---|
| ⚪ jamais | **8** | 0 | 0 | 0 | 0 |

## Où en est chaque session

```
aucune session ne pointe
```

_Aucune session ne pointe._

## ⬜ Ce qui reste à faire

| # | Point | État |
|---|---|---|
| 1 | Le kit `projet` pose `<projet>/.claude/skills/` : `mere` · `fille` · `balises` · `schema-chemins` | ⬜ |
| 2 | Gabarit **vide** `deployer` — la procédure est propre à chaque projet | ⬜ |
| 3 | `_ops/adr/` : gabarit + le test « quelqu'un pourrait-il défaire ça dans six mois ? » | ⬜ |
| 4 | Un installeur **unique** `kits/installer.ps1 -Kit <nom>` — plus un par kit | ⬜ |
| 5 | Kit **`audit`** : la méthode ERPHT, 11 axes, CCCERR, triple cotation | ⬜ |
| 6 | Kit **`design`** : la charte Avaliance, la veille, le miroir de site | ⬜ |
| 7 | Kit **`rapport`** : le rapporteur — hebdo, audit, panne | ⬜ |
| 8 | Le hub gagne un onglet par kit posé | ⬜ |

Source : [`_ops/PLAN_2026-09-24_kits.md`](../PLAN_2026-09-24_kits.md)

## ⚠️ Ce qui attend une décision

_Rien en attente._

## Les portes

⚪ **jamais** — aucune mesure — lancer _ops/tests/lancer.sh

## Les journaux

| Journal | Mois | Lignes | Dernière |
|---|---|---|---|
| SESSIONS | 2026-09 | 1 | `2026-09-24 14:30` UTC · **fille-kit** — kit projet construit, quatre portes vues rouges |
| DECISIONS | 2026-09 | 4 | `2026-09-24 15:05` UTC · **Hamada** — le hub sur la forme dAva Manager : noir, schemas, onglets |
| PANNES | — | 0 |  |

## Ce qui a été livré

_Aucun commit._


## Anti-régression

**On n'écrit pas des tests pour le code. On écrit des tests pour les pannes.**

⭐ Un test unitaire dit « cette fonction est juste aujourd'hui ». Un test d'anti-régression dit « ce bug-là ne reviendra pas ».

| # | Étape | Comment |
|---|---|---|
| 1 | Lister les vraies pannes | Les incidents, les tickets, les messages « ça ne marche plus ». ⛔ Pas les risques imaginés. |
| 2 | Écrire le cas, nommé par sa date et son symptôme | cas_2026_09_06_deux_lockfiles, pas test_config. |
| 3 | ⭐ Le voir ROUGE | Remettre le bug, ou lancer le test sur le commit d'avant la réparation. |
| 4 | Réparer, ou figer l'existant | Si le comportement actuel est bizarre mais voulu, on le fige tel quel — test de caractérisation. |
| 5 | Le voir VERT, et écrire comment il a été vu rouge | Au message de commit : « vu rouge en &lt;ce qu'on a cassé&gt; ». |
| 6 | La porte | Le cas entre dans le banc, et le banc refuse le commit. ⛔ Pas un avertissement. |

### Comment tu sais que ce que tu as testé est bon

| La question | Ce qui la prouve |
|---|---|
| Ce test a-t-il déjà été vu rouge ? | la ligne du commit : « vu rouge en… » |
| Si je casse la ligne qu'il garde, tombe-t-il ? | le sabotage, relancé maintenant |
| Son nom dit-il quelle panne ? | date + symptôme dans le nom |
| Tourne-t-il avant le commit ? | le hook, pas la bonne volonté |
| Teste-t-il le code, ou des bouchons ? | ce qui est simulé dans le test |
| Combien de temps dure le banc ? | la durée, mesurée |
| Depuis quand n'a-t-il rien attrapé ? | la date du dernier rouge réel |

## Comment auditer

**Je ne crois personne : je copie, je casse exprès, et je regarde si quelque chose crie.**

⭐ Pas de preuve, pas de constat — et un test vert ne prouve rien tant qu'on ne l'a pas vu **rouge**.

| # | Étape | En une phrase |
|---|---|---|
| 1 | Contrôle d'entrée | la branche contient-elle tout le travail, et le canon est-il le même que sur main ? Sinon ⛔ je n'audite pas |
| 2 | Copie isolée | mon clone, ma base, mon port — je ne touche jamais à ce que l'autre utilise |
| 3 | Mur d'indépendance | ⭐ je retire les plans et les prompts : je juge le code sur le contrat, pas sur les intentions |
| 4 | Banc de référence | base refaite de zéro, tous les tests lancés — tout doit être vert avant de commencer |
| 5 | Sabotages | je casse une chose à la fois, je relance tout ; si aucun test ne tombe, ce test ne garde rien |
| 6 | Deux vérificateurs | l'un suit chaque ancien défaut, l'autre passe la grille et la sécurité — chacun prouve tout |
| 7 | Cliquet et rapport | je fais tomber le cliquet exprès — serveur mort, tests effacés — puis j'écris le verdict, une preuve par ligne |

### Comment tu sais que tu as vraiment audité

| La question | Ce qui la prouve |
|---|---|
| Ai-je vu un test tomber ? | combien de sabotages, et combien de tests sont tombés |
| Ai-je jugé sans lire les intentions ? | le dossier des plans était-il absent du clone |
| Le banc était-il vert avant ? | la sortie du banc de référence, horodatée |
| Chaque constat a-t-il sa preuve ? | le nombre de constats sans fichier:lignes |
| Qui a contesté ? | un nom, et un modèle différent |
| Le cliquet a-t-il été vu tomber ? | ce qu'on a cassé pour le faire tomber |
| Puis-je refaire l'audit ? | le commit exact, les commandes, dans l'ordre |

## Mettre à niveau

**On n'améliore pas un code qu'on ne comprend pas. On l'explique d'abord — sans toucher une seule instruction.**

⭐ Ce qui rend la promesse tenable est une **porte** qui compare les deux versions sans les commentaires.

| # | Étape | Comment |
|---|---|---|
| 1 | Lire, et ne rien toucher | Une route, un écran, une fonction à la fois. On note ce qu'on ne comprend pas. |
| 2 | Annoter — ⛔ zéro instruction modifiée | On ajoute : un en-tête (route, reçoit, renvoie, effet), des titres de section, des lignes vides, et la règle métier trouvée. Rien d'autre. |
| 3 | ⭐ La porte qui prouve que rien n'a bougé | Un script retire tous les commentaires et les blancs des deux versions et les compare. Différent = refusé. |
| 4 | Tester ce qu'on vient de comprendre | Chaque règle découverte devient un cas, vu rouge d'abord. On fige le comportement actuel, même s'il paraît bizarre. |
| 5 | Corriger — un constat, un commit | Un défaut = une correction, encadrée et étiquetée ([V1.5 CST-SECU-13]), dans son propre commit. |
| 6 | Ajouter la fonctionnalité | Maintenant seulement. Sur un code lisible, testé, dont les règles sont écrites. |

### Comment tu sais que tu n'as rien cassé

| La question | Ce qui la prouve |
|---|---|
| Ai-je changé une instruction ? | la porte : deux versions comparées sans commentaires |
| Le diff contient-il autre chose que des commentaires ? | le diff, lu ligne à ligne |
| Les corrections sont-elles étiquetées ? | un marqueur par bloc : [V1.5 CST-nn] |
| Annotation et correction sont-elles séparées ? | deux commits distincts |
| Quelle règle métier ai-je découverte ? | la règle, écrite, et envoyée au métier |
| Le code mort est-il conservé ? | les lignes commentées d'origine, intactes |
| Les tests d'avant passent-ils encore ? | le banc, relancé, avec sa durée |

## Mon PC

`ASUS TUF GAMING X670E-PLUS WIFI · Ryzen 7 9800X3D · 64 Go DDR5 · Samsung 990 EVO Plus 1 To`

| # | Quoi | Comment |
|---|---|---|
| 1 | Poser le pilote **GeForce `581.80`** | `sauvegardes/pilotes_2026-09-20/581.80-desktop-win10-win11-64bit-international-dch-whql.exe` |
| 2 | **Tout remettre sauf la Quadro** | `_ops/pcwatch/tout-remettre-sauf-quadro.ps1` |
| 3 | Relancer **AMD Chipset Software 8.08.12.551** | ⚠️ à la main — `amdfendr.inf` et `amd3dvcache.inf` ont été retirés du magasin |
| 4 | Redémarrer | une seule fois, à la fin |
| 5 | Vérifier : **6 écrans**, Quadro toujours coupée, verrou WU intact |   |
| 6 | **Travailler 2 jours** | 21-22/09, usage normal |
| 1 | **Couper HAGS** (`HwSchMode = 2 → 1`, redémarrer) — vise directement `dxgmms2` | 2 min | oui |
| 2 | **Retirer NVIDIA App** — pilote seul | 5 min | oui |
| 3 | **BIOS** : slot de la 5070 en **Gen 4**, **ASPM coupé** | 5 min, devant la machine | oui |
| 4 | Un pilote par carte, comme les 9 mois : 5070 `591.59` + P2000 `581.80` Enterprise | 20 min | oui |
| 5 | Remplacer la P2000 par une RTX A2000/A4000 (même pilote que la 5070) | achat | — |
| 1 | Retirer **NVIDIA App** (réinstallée par le 581.80) — pilote seul | Microsoft Q&A, RTX 3070 + GTX 1080 Ti |

## Coder proprement

**La raison disparaît toujours avant le code.**

⭐ C'est le seul des trois chapitres qu'on ne peut pas rattraper.

### Trois journaux, jamais un seul

| Journal | Ce qu'on y met |
|---|---|
| <code>SESSIONS</code> | qui a fait quoi, quand |
| <code>DECISIONS</code> | un choix tranché, avec son motif |
| <code>PANNES</code> | symptôme, cause, porte posée |

### Le test de l'ADR

> Quelqu'un pourrait-il défaire ça dans six mois en croyant bien faire ?

| Section | Contenu |
|---|---|
| Contexte | ce qui est vrai au moment de décider, en faits |
| Décision | ce qu'on fait, à l'indicatif présent |
| Motif | pourquoi celle-là |
| ⭐ Ce qu'on a écarté | les options rejetées, et pourquoi |
| Conséquences | y compris ce que ça coûte |
| Ce qui prouverait qu'on s'est trompé | le signal qui ferait rouvrir l'ADR |

### Comment tu sais que tu codes proprement

| La question | Ce qui la prouve |
|---|---|
| La décision d'hier, peux-tu dire pourquoi ? | la ligne du journal, ou l'ADR |
| Est-ce poussé ? | le commit, sur le distant |
| Écrire coûte combien de gestes ? | compter — dire.sh = un |
| Les commentaires disent-ils pourquoi ? | en ouvrir cinq au hasard |
| Combien d'ADR ce trimestre ? | le compte |
| La doc s'écrit-elle, ou se génère-t-elle ? | le hub, régénéré par le pre-commit |
| Un nouveau peut-il démarrer seul ? | le tester avec quelqu'un qui arrive |

## Mes skills

| Kit | Lignes | Ce qu'il pose |
|---|---|---|
| **audit** | 81 | Le kit d'audit — il POSE la méthode Tech Due Diligence dans le dépôt : les 11 axes, la fiche CCCERR, la triple cotation, le registre à numérotation st… |
| **couts** | 90 | Le kit coûts — la porte sur les appels payants. Une liste d'appels autorisés qui refuse tout par défaut, un plafond qui ARRÊTE au lieu d'avertir, et l… |
| **deploiement** | 83 | Le kit de déploiement — il POSE la procédure à UN seul endroit, le script qui prend le verrou lui-même, le témoin « le serveur SERT », et le retour ar… |
| **design** | 74 | Le kit design — il POSE la charte dans le dépôt : les couleurs avec leurs contrastes MESURÉS, la règle du vert dessous, les contraintes de figure, la … |
| **donnees** | 78 | Le kit données — migrations versionnées avec leur retour arrière, accès fermés par défaut et testés PAR L'ÉCHEC, et une sauvegarde qu'on a essayé de r… |
| **neuf** | 82 | Le kit général — démarrer un nouveau projet sérieux. Il ne pose aucun fichier à lui : il pose quatre questions et enchaîne les autres kits, dans l'ord… |
| **projet** | 157 | Le kit unique d'un projet — il POSE les fichiers au lieu de les décrire : le hub de contrôle (index.html local + README.md à l'adresse GitHub), le ban… |
| **rapport** | 75 | Le kit rapporteur — il POSE les gabarits de ce qu'un tiers va lire : hebdo, rapport de panne, et la skill /rapporteur. Le résultat en ligne 1, ce qui … |

### Les 18 skills

| Famille | Skills |
|---|---|
| Audit | `audit-code` · `audit-correction` · `audit-rapport` |
| Méthode | `balises` · `miroir-site` · `schema-chemins` · `veille-design` |
| Forme | `brainstorm` · `cadrage` · `focus` · `plan` · `recadrage` |
| — | `charte` · `rapporteur` |
| Charte | `design-avaliance` |
| Rôle de session | `fille` · `installer-mere-fille` · `mere` |
---

⛔ **Ce fichier est généré.** Ne pas l'écrire à la main — il serait écrasé, et il mentirait
avant ça. Le régénérer :

```bash
node _ops/hub/generer-hub.mjs
```
