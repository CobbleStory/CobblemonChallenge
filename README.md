# 📋 Configuration Documentation - Cobblemon Challenge

## 📁 Structure des Fichiers

Le mod utilise un système de configuration modulaire situé dans `config/cobblemon-challenge/` :

```
config/cobblemon-challenge/
├── config.yml                    # Configuration principale
├── challenges/                   # Dossier des défis par rareté
│   ├── common.yml                # Défis communs
│   ├── uncommon.yml              # Défis peu communs
│   ├── rare.yml                  # Défis rares
│   ├── epic.yml                  # Défis épiques
│   └── legendary.yml             # Défis légendaires
└── rewards/                      # Dossier des récompenses par rareté
    ├── common.yml                # Récompenses communes
    ├── uncommon.yml              # Récompenses peu communes
    ├── rare.yml                  # Récompenses rares
    ├── epic.yml                  # Récompenses épiques
    └── legendary.yml             # Récompenses légendaires
```

---

## ⚙️ Configuration Principale (`config.yml`)

### Apparence des Items de Défi

```yaml
# Material de base pour les papiers de défi
challenge_item_material: "minecraft:paper"

# Nom affiché sur l'item (%status%, %name%, %rarity% disponibles)
challenge_item_name: "%status% §6Défi : %name%"

# Texte d'en-tête dans la description (%description%, %rarity%, %progress% disponibles)
challenge_item_lore_header: "§7%description%"

# Titre de la section objectifs
challenge_item_lore_objectives: "§eObjectifs :"

# Texte affiché quand le défi est terminé
challenge_item_lore_completed: "§a§l✓ DÉFI COMPLÉTÉ !"

# Instructions en bas de l'item
challenge_item_lore_footer: "§aCliquez avec le papier en main pour récupérer vos récompenses !"
```

### Symboles de Statut

```yaml
# Icône pour les défis en cours
status_icon_pending: "§e⏳"

# Icône pour les défis terminés
status_icon_completed: "§a✓"
```

### Barres de Progression

```yaml
# Caractère pour la partie remplie de la barre
progress_bar_filled: "§a█"

# Caractère pour la partie vide de la barre
progress_bar_empty: "§7█"

# Longueur totale de la barre de progression
progress_bar_length: 10
```

### Configuration des Messages

```yaml
# Afficher la progression dans la barre d'action
show_progress_in_actionbar: true

# Afficher un message lors de la complétion d'un défi
show_completion_message: true

# Afficher un message lors de la réception d'un nouveau défi
show_new_challenge_message: true

# Préfixe pour tous les messages du mod
message_prefix: "§8[§6CobblemonChallenge§8]§r "

# Messages personnalisables
message_new_challenge: "§a§lNOUVEAU DÉFI REÇU !"
message_challenge_completed: "§a§l✓ DÉFI COMPLÉTÉ !"
message_rewards_claimed: "§a§l✓ RÉCOMPENSES RÉCUPÉRÉES !"
```

### Options de Debug

```yaml
# Activer le mode debug (logs supplémentaires)
debug_mode: false

# Logger tous les événements de progression
log_progression_events: false
```

---

## 🎯 Configuration des Défis

Chaque fichier de rareté (`challenges/*.yml`) contient une liste de défis disponibles.

### Structure d'un Défi

```yaml
- id: "nom_unique_du_defi"           # Identifiant unique (obligatoire)
  name: "Nom Affiché"                # Nom visible du défi (obligatoire)
  description: "Description du défi" # Description courte (obligatoire)
  icon: "minecraft:item_icon"        # Icône (optionnel, pour référence)
  objectives:                        # Liste des objectifs (obligatoire)
    - type: "TYPE_OBJECTIF"          # Type d'objectif (voir liste ci-dessous)
      target: "cible"                # Cible spécifique ou "any"
      amount: 10                     # Quantité requise
```

### Types d'Objectifs Disponibles

#### 🔹 Événements Pokémon

| Type | Description | Exemples de Target |
|------|-------------|-------------------|
| `CATCH_POKEMON` | Capturer des Pokémon | `any` |
| `CATCH_SPECIFIC_POKEMON` | Capturer un Pokémon spécifique | `pikachu`, `charizard` |
| `CATCH_SHINY_POKEMON` | Capturer des Pokémon Shiny | `any` |
| `CATCH_SPECIFIC_SHINY` | Capturer un Shiny spécifique | `pikachu` |
| `DEFEAT_WILD_POKEMON` | Vaincre des Pokémon sauvages | `any` |
| `DEFEAT_SPECIFIC_WILD_POKEMON` | Vaincre un Pokémon spécifique | `garchomp` |
| `DEFEAT_SHINY_POKEMON` | Vaincre des Pokémon Shiny | `any` |
| `WIN_BATTLES` | Gagner des combats | `any` |
| `EVOLVE_POKEMON` | Faire évoluer des Pokémon | `any` |
| `EVOLVE_SPECIFIC_POKEMON` | Faire évoluer un Pokémon spécifique | `charmander` |
| `LEVEL_UP_POKEMON` | Faire monter des niveaux | `any` |
| `LEVEL_UP_TO_TARGET` | Atteindre un niveau spécifique | `any` |
| `HEAL_POKEMON` | Soigner des Pokémon | `any` |
| `INTERACT_POKEMON` | Interagir avec des Pokémon | `any` |
| `HATCH_EGGS` | Faire éclore des œufs | `any` |
| `RELEASE_POKEMON` | Relâcher des Pokémon | `any` |

#### ⛏️ Événements de Minage

| Type | Description | Exemples de Target |
|------|-------------|-------------------|
| `MINE_BLOCKS` | Miner n'importe quels blocs | `any` |
| `MINE_SPECIFIC_BLOCK` | Miner un bloc spécifique | `diamond_ore`, `stone` |
| `MINE_ORES` | Miner des minerais | `any` |
| `MINE_DIAMONDS` | Miner des diamants | `any` |
| `MINE_COAL` | Miner du charbon | `any` |
| `MINE_IRON` | Miner du fer | `any` |
| `MINE_GOLD` | Miner de l'or | `any` |

#### 🚶 Événements de Déplacement

| Type | Description | Exemples de Target |
|------|-------------|-------------------|
| `WALK_DISTANCE` | Marcher une distance | `any` |
| `SPRINT_DISTANCE` | Courir une distance | `any` |
| `SWIM_DISTANCE` | Nager une distance | `any` |
| `FLY_DISTANCE` | Voler une distance | `any` |
| `TRAVEL_DISTANCE` | Voyager (total) une distance | `any` |

#### 🗺️ Événements d'Exploration

| Type | Description | Exemples de Target |
|------|-------------|-------------------|
| `DISCOVER_BIOMES` | Découvrir des biomes | `any` |
| `DISCOVER_SPECIFIC_BIOME` | Découvrir un biome spécifique | `desert`, `ocean` |
| `VISIT_NETHER` | Visiter le Nether | `any` |
| `VISIT_END` | Visiter l'End | `any` |

#### 🛠️ Événements Minecraft Divers

| Type | Description | Exemples de Target |
|------|-------------|-------------------|
| `BREAK_BLOCKS` | Casser des blocs | `any` |
| `KILL_MOBS` | Tuer des mobs | `any` |
| `CRAFT_ITEMS` | Craft des objets | `any` |
| `PLACE_BLOCKS` | Placer des blocs | `any` |
| `JUMP_COUNT` | Sauter | `any` |
| `TAKE_DAMAGE` | Subir des dégâts | `any` |
| `SLEEP_IN_BED` | Dormir | `any` |
| `EAT_FOOD` | Manger | `any` |

### Exemple de Défi Complet

```yaml
- id: "ultimate_trainer"
  name: "Dresseur Ultime"
  description: "Maîtrisez tous les aspects du dressage"
  icon: "minecraft:dragon_egg"
  objectives:
    - type: "CATCH_POKEMON"
      target: "any"
      amount: 100
    - type: "WIN_BATTLES"
      target: "any"
      amount: 50
    - type: "EVOLVE_POKEMON"
      target: "any"
      amount: 15
```

---

## 🎁 Configuration des Récompenses

Chaque fichier de rareté (`rewards/*.yml`) contient des sets de récompenses possibles.

### Structure d'un Set de Récompenses

```yaml
- commands:                        # Liste des commandes à exécuter
    - "give %player% minecraft:diamond 5"
    - "experience add %player% 100"
    - "say %player% a terminé un défi !"
  weight: 40                       # Poids pour la sélection aléatoire
```

### Variables Disponibles

- `%player%` : Nom du joueur
- `%uuid%` : UUID du joueur

### Exemples de Commandes de Récompense

```yaml
# Donner des items
- "give %player% minecraft:diamond 10"
- "give %player% cobblemon:master_ball 1"

# Donner de l'expérience
- "experience add %player% 500"

# Donner de l'argent (si plugin d'économie)
- "money give %player% 1000"

# Exécuter des commandes personnalisées
- "crate key give mythiquecrate 1 %player%"
- "lp user %player% permission set vip.temp true"

# Messages publics
- "say §6%player% a accompli un exploit légendaire !"

# Titres et effets
- "title %player% title {\"text\":\"LÉGENDE\",\"color\":\"gold\",\"bold\":true}"
- "effect give %player% minecraft:speed 60 1"
```

### Système de Poids

Le poids détermine la probabilité qu'un set de récompenses soit choisi :

```yaml
- commands: ["give %player% minecraft:diamond 1"]
  weight: 60    # 60% de chance

- commands: ["give %player% minecraft:netherite_ingot 1"]
  weight: 30    # 30% de chance

- commands: ["give %player% minecraft:dragon_egg 1"]
  weight: 10    # 10% de chance
```



---

## 🚀 Commandes Administrateur

### Gestion des Défis

```bash
# Donner un défi à un joueur
/challenge give <joueur> <rareté>

# Recharger la configuration
/challenge reload

# Afficher les informations du mod
/challenge info

# Voir les statistiques d'un joueur
/challenge stats <joueur>
```

### Commandes de Debug

```bash
# Tester la progression d'un objectif
/challenge debug test <joueur> <objectif> <cible> <quantité>

# Réinitialiser les statistiques d'un joueur
/challenge debug reset <joueur>
```

### Commandes Joueur

```bash
# Vérifier le défi tenu en main
/challenge check

# Récupérer les récompenses du défi tenu
/challenge claim
```

---

## 📝 Conseils de Configuration

### 🎯 Équilibrage des Défis

1. **Défis Communs** : Objectifs simples (10-50 actions)
2. **Défis Peu Communs** : Objectifs moyens (25-100 actions)
3. **Défis Rares** : Objectifs difficiles (50-200 actions)
4. **Défis Épiques** : Objectifs très difficiles (100-500 actions)
5. **Défis Légendaires** : Objectifs multiples et complexes

### 🎁 Équilibrage des Récompenses

- Utilisez des poids appropriés pour contrôler la rareté
- Évitez les récompenses trop puissantes pour les défis faciles
- Pensez à l'économie de votre serveur

### 🔧 Personnalisation

- Adaptez les messages à votre serveur
- Utilisez des couleurs cohérentes avec votre thème
- Testez les changements avec `/challenge reload`

### ⚠️ Sécurité des Récompenses

Le mod valide automatiquement les commandes de récompense pour éviter les commandes potentiellement dangereuses pour la stabilité du serveur.

---

## 🐛 Résolution de Problèmes

### Problèmes Courants

1. **Les défis ne se chargent pas** :
   - Vérifiez la syntaxe YAML
   - Consultez les logs du serveur
   - Utilisez `/challenge reload`

2. **Les objectifs ne progressent pas** :
   - Vérifiez que le type d'objectif existe
   - Activez `debug_mode: true` pour plus de logs
   - Testez avec `/challenge debug test`

3. **Les récompenses ne fonctionnent pas** :
   - Vérifiez que les commandes sont valides
   - Testez les commandes manuellement
   - Consultez les logs d'erreurs

### Activation du Debug

```yaml
debug_mode: true
log_progression_events: true
```

Puis relancez avec `/challenge reload` pour voir les logs détaillés.

---

## 📊 Exemple de Configuration Complète

### Défi Personnalisé

```yaml
- id: "cobblemon_master"
  name: "Maître Cobblemon"
  description: "Devenez un expert en capture et combat"
  objectives:
    - type: "CATCH_POKEMON"
      target: "any"
      amount: 50
    - type: "CATCH_SHINY_POKEMON"
      target: "any"
      amount: 3
    - type: "WIN_BATTLES"
      target: "any"
      amount: 25
    - type: "EVOLVE_POKEMON"
      target: "any"
      amount: 10
```

### Récompenses Correspondantes

```yaml
- commands:
    - "give %player% cobblemon:master_ball 3"
    - "give %player% minecraft:nether_star 1"
    - "crate key give legendarycrate 1 %player%"
    - "money give %player% 10000"
    - "say §6%player% est devenu un Maître Cobblemon !"
    - "title %player% title {\"text\":\"MAÎTRE\",\"color\":\"gold\"}"
  weight: 100
```

---

*Cette documentation couvre toutes les fonctionnalités du mod Cobblemon Challenge. Pour plus d'aide, consultez les logs du serveur ou contactez le support.*
