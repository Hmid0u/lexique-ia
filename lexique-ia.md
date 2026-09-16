# Lexique IA

- Inférence
- RAG
- ChatBot
- Paramètre
- DataSet
- Agent IA
- Modèle
- Réseau de Neurones
- Machine Learning
- NLP
- Qwen
- Deep Learning
- GPT
- IA Adpatative
- IA Générale
- Ollama
- IA Générative
- Singularité Technologique
- LLM
- Hallucination
- Embedding
- Token
- European AI Act
- Algorithme
- Test de Turing
- Big Data
- Biais
- ModelFile
- SystemPrompt
- Deep Learning
- Données

---

## Fondamentaux

- **Algorithme** : Suite finie d'étapes qui transforme des entrées en sorties. En IA, on distingue l'algorithme d'_inférence_ (le modèle "réfléchit" et produit une réponse) de celui d'_optimisation_ (SGD, Adam) qui ajuste le modèle pendant l'entraînement.

- **Données** : Les "matières premières" : textes, images, paires d'entrées/sorties. Tout passe par un prétraitement (tokenisation, normalisation, augmentation) avant d'entrer dans le modèle. La qualité des données conditionne les résultats.

- **Big Data** : Des volumes de données qu'une machine seule ne peut pas traiter. On utilise des frameworks distribués (Spark, Hadoop) pour les paralléliser. C'est le prérequis pour entraîner un modèle sur des milliards de tokens.

- **Biais** : Un résultat systématiquement décalé par rapport à la réalité. Il vient souvent des données d'entraînement (ex : trop d'hommes dans un dataset médical) ou du choix de l'architecture.

- **Test de Turing** : Test de 1950 : un humain converse avec deux interlocuteurs (un humain et une machine) et doit deviner lequel est la machine. S'il n'y parvient pas, la machine "passe" le test. C'est historique — aujourd'hui on utilise des benchmarks chiffrés (MMLU, HumanEval).

- **IA Générale (AGI)** : Une IA qui saurait faire _n'importe quelle_ tâche intellectuelle comme un humain, sans être re-entraînée pour chaque tâche. N'existe pas encore. Les LLM actuels sont impressionnants mais restent spécialisés.

- **Singularité Technologique** : Idée spéculative : le moment où l'IA s'améliore elle-même plus vite qu'un humain ne peut la comprendre ou la contrôler. Pas une prédiction, un scénario de débat.

---

## Machine Learning / Deep Learning

- **Machine Learning** : Au lieu de programmer des règles à la main, on donne des exemples au modèle et il "devine" les règles lui-même en minimisant son erreur. C'est le cadre général : supervisé (on a les labels), non supervisé (pas de labels), par renforcement (récompenses).

- **Deep Learning** : Un type de ML qui utilise des réseaux de neurones avec _beaucoup_ de couches. Chaque couche apprend un niveau de représentation de plus en plus abstrait (bords → formes → objets en vision, par exemple). C'est ce qui a fait décoller l'IA récente.

- **Réseau de Neurones** : Une succession de couches de "neurones" (multiplications + addition + fonction non linéaire comme ReLU). L'entraînement consiste à ajuster les poids des connexions via la _rétropropagation_ : on mesure l'erreur à la sortie, on la propage en arrière, on ajuste les poids.

- **Paramètre** : Un poids (un nombre) dans le réseau. Un modèle "7B" a 7 milliards de paramètres. Plus il y en a, plus le modèle peut représenter de la complexité — mais plus il est gourmand en mémoire et en calcul.

- **DataSet** : Un ensemble de données structuré pour entraîner et évaluer un modèle. On le divise typiquement en _train_ (80 %), _validation_ (10 %) et _test_ (10 %). Le test sert à vérifier que le modèle généralise, pas juste qu'il a "mémorisé".

- **Embedding** : La représentation d'un mot, d'une phrase ou d'une image sous forme de liste de nombres (un vecteur). Deux concepts proches ont des vecteurs proches. C'est ce qui permet de faire du _retrieval_ (recherche sémantique) et du RAG.

- **Token** : Le morceau de texte le plus petit qu'un LLM lit. Un token ≈ un morceau de mot (1 à 4 tokens par mot en français). Le contexte d'un modèle est limité en tokens (4 096, 32 768, 128 000…). C'est aussi l'unité de facturation des API.

- **Inférence** : Le moment où le modèle _déjà entraîné_ est utilisé en production : on lui donne une entrée, il sort une réponse. Les poids ne changent plus. La contrainte est la latence (temps de réponse) et la mémoire.

- **IA Adaptative** : Un système qui continue d'apprendre en production, sans re-entraînement complet. Il s'ajuste aux nouvelles données ou au changement de comportement des utilisateurs. Techniques : online learning, replay, meta-learning.

---

## NLP & Langage

- **NLP** (Natural Language Processing) : Le domaine qui fait comprendre et produire du langage aux machines. Tâches : classification de texte, extraction d'entités, traduction, question-réponse, génération. Aujourd'hui dominé par les Transformers.

- **LLM** (Large Language Model) : Un modèle de langage _très grand_ (milliards de paramètres) pré-entraîné à prédire le mot suivant sur un corpus massif. C'est le moteur derrière ChatGPT, Claude, Qwen… On le fine-tune ensuite (SFT, RLHF) pour qu'il suive des instructions.

- **GPT** (Generative Pre-trained Transformer) : L'architecture de OpenAI. "Decoder-only" : il lit le texte de gauche à droite et prédit le token suivant. GPT-4/5 : architecture non publiée, mais le principe reste le même.

- **ChatBot** : Une interface de conversation qui orchestre un LLM. En pratique : gestion du contexte (fenêtre glissante, résumé), prompt engineering, appel de fonctions, streaming des tokens, garde-fous de sécurité.

- **Hallucination** : Le modèle invente des faits (citations, dates, noms) avec un ton confiant. Cause : il optimise la _plausibilité linguistique_, pas la vérité. Solutions : RAG, vérification externe, chain-of-verification.

- **System Prompt** : L'instruction "cache" placée en début de conversation, avant les messages de l'utilisateur. Il fixe le rôle, le ton, les contraintes de format et les limites de sécurité. Le modèle lui accorde une priorité élevée.

- **RAG** (Retrieval-Augmented Generation) : Avant de répondre, le système _récupère_ des passages pertinents dans une base de documents (via embeddings + recherche vectorielle), puis les injecte dans le prompt du LLM. Résultat : des réponses ancrées dans des sources réelles, moins d'hallucinations.

- **Agent IA** : Un LLM qui ne se contente pas de répondre mais qui _agit_ : il planifie, appelle des outils (API, terminal, navigateur, exécution de code), observe le résultat, et itère jusqu'à atteindre un objectif. La différence avec un chatbot : la boucle d'action-observation.

---

## Modèles & Outils

- **IA Générative** : Toute IA qui _crée_ du contenu nouveau (texte, image, audio, vidéo, code). Architectures principales : Transformers (texte), Diffusion models (image/vidéo), VAE/GAN (historique).

- **Qwen** : La famille de LLM open-weight d'Alibaba. Architectures Transformer (attention multi-tête, RoPE, SwiGLU). Versions dense et MoE. Disponibles sur Hugging Face / ModelScope.

- **Ollama** : Un runtime local (écrit en Go) pour faire tourner des LLM quantisés (format GGUF) sur ta machine. Tu lances `ollama run llama3.2`, c'est parti. API REST locale sur le port 11434, compatible avec le format OpenAI. Pas de cloud, pas de clé API.

- **ModelFile** : Le "Dockerfile" d'Ollama. Tu y décris le modèle de base (`FROM`), le system prompt, les hyperparamètres d'inférence (temperature, top_k, top_p, num_ctx) et le template de chat. Tu obtiens une image LLM versionnée et reproductible.

---

## Régulation

- **European AI Act** : Le premier cadre juridique mondial sur l'IA (Règlement UE 2024/1689). Il classe les systèmes par niveau de risque : _inacceptable_ (interdit), _élevé_ (conformité stricte : audit, logging, supervision humaine), _limité_ (transparence), _minimal_ (rien). Sanctions jusqu'à 7 % du CA mondial. Déploiement progressif 2025 → 2027.
