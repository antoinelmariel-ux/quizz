# Quiz Alchimiste

## Aperçu
"`quiz_alchemiste.html`" propose une expérience de quiz futuriste centrée sur un laboratoire d'alchimie quantique. L'interface affiche un écran de sélection de difficulté, un écran de chargement animé puis le plateau de jeu avec score, séries de bonnes réponses, potions collectées et minuterie.

## Organisation de l'interface
- **Sélection de la difficulté** – la grille `#difficultyGrid` est remplie dynamiquement par `showDifficultySelection()` à partir des niveaux déclarés dans `GAME_CONFIG`. Chaque carte présente icône, description et statistiques d'expérience. 【F:quiz_alchemiste.html†L7-L58】【F:quiz_alchemiste.html†L420-L470】
- **Écran de chargement** – la section `#loadingScreen` simule une initialisation (spinner et instructions clavier) avant de lancer la partie choisie. 【F:quiz_alchemiste.html†L16-L23】【F:quiz_alchemiste.html†L470-L520】
- **Plateau de jeu** – `#gameContainer` regroupe l'entête des statistiques, le panneau des ingrédients collectés, le chaudron animé avec anneau de minuterie et le panneau des questions/réponses. 【F:quiz_alchemiste.html†L25-L87】
- **Panneau d'explications** – `#explanationPanel` s'affiche après chaque réponse pour détailler la solution, avec une barre de progression automatique. 【F:quiz_alchemiste.html†L89-L99】【F:quiz_alchemiste.html†L1164-L1204】

## Gestion des données et des questions
- Les paramètres globaux (durée, bonus, paliers de niveau, couleurs de potions) sont centralisés dans `GAME_CONFIG`. 【F:quiz_alchemiste.html†L121-L155】
- `gameData` conserve l'état courant : score, série, niveau, difficulté, historique et pools de questions. 【F:quiz_alchemiste.html†L157-L186】
- `loadQuestionsFromXML()` parse le XML par catégorie, extrait texte, réponses, explications et détecte les difficultés disponibles, en loggant chaque étape. 【F:quiz_alchemiste.html†L210-L420】
- `initializeQuestionPool()` et `getNextIntelligentQuestion()` mélangent les questions par niveau, évitent les répétitions et maintiennent un historique tournant. 【F:quiz_alchemiste.html†L569-L643】

## Boucle de jeu et scoring
- `startGameWithDifficulty()` prépare les pools, masque la sélection puis déclenche chargement et première question. 【F:quiz_alchemiste.html†L470-L560】
- `loadNextQuestion()` choisit la question suivante, réinitialise l'état et démarre le compte à rebours. 【F:quiz_alchemiste.html†L640-L700】
- `startTimer()` et `updateTimerDisplay()` pilotent la minuterie circulaire et les avertissements visuels. 【F:quiz_alchemiste.html†L700-L760】
- `selectAnswer()` gèle les boutons, applique les styles `correct/incorrect`, affiche l'explication et bascule vers la question suivante. 【F:quiz_alchemiste.html†L760-L840】
- `handleCorrectAnswer()` augmente score, série, progression du chaudron, applique bonus de vitesse et déclenche animations/ingrédients. `handleIncorrectAnswer()` et `handleTimeout()` pénalisent et remettent les compteurs. 【F:quiz_alchemiste.html†L780-L910】
- `checkLevelUp()` et `showLevelUpNotification()` ajustent automatiquement la difficulté lorsque les paliers sont atteints. 【F:quiz_alchemiste.html†L910-L990】
- Les fonctions `addIngredient()`, `createPotion()` et `checkForPotion()` gèrent ingrédients, potions bonus et effets visuels associés. 【F:quiz_alchemiste.html†L926-L1030】

## Effets visuels et UX
- `createFloatingOrbs()` génère les orbes d'arrière-plan animés, tandis que `createCauldronEffects()` ajoute vapeur et étincelles dans la zone du chaudron. 【F:quiz_alchemiste.html†L311-L328】【F:quiz_alchemiste.html†L1081-L1154】
- `createExplosion()`, `createSpeedBonusEffect()` et `createIngredientEffect()` produisent les animations de feedback lors des réponses et collectes spéciales. 【F:quiz_alchemiste.html†L848-L979】【F:quiz_alchemiste.html†L1030-L1054】
- `showNotification()` affiche des messages temporisés en overlay pour chaque événement notable (bonus, erreurs, montée de niveau). 【F:quiz_alchemiste.html†L1224-L1250】
- Le listener clavier autorise les réponses rapides avec les touches `1` à `4`. 【F:quiz_alchemiste.html†L1252-L1263】

## Version
 Le pied de page `footer.app-footer` affiche désormais la version `v1.0.1` de l'application. Mettez à jour ce numéro à chaque évolution fonctionnelle et synchronisez la mention dans cette section. 【F:quiz_alchemiste.html†L1298-L1303】

