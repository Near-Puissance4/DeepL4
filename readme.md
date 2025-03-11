# DeepL4

## **Description**
Ce composant implémente une intelligence artificielle capable d'apprendre à jouer au Puissance 4 en utilisant l'**apprentissage par renforcement**. L'IA s'entraîne en jouant contre elle-même et contre d'autres adversaires, améliorant progressivement ses décisions grâce à une fonction de récompense.

## **Technologies Utilisées**
- **Langage** : Python 3.x
- **Frameworks et Bibliothèques** :
  - TensorFlow / PyTorch (pour DQN si utilisé)
  - NumPy (calculs matriciels)
  - Gym/OpenAI (facultatif, pour l'environnement d'entraînement)
  - FastAPI (si API pour interaction avec le backend)

## **Architecture**
Le composant IA Apprentissage suit une approche basée sur **Q-Learning** ou **Deep Q-Networks (DQN)**.

### **Schéma général**
```plaintext
[Backend (NestJS)] <----> [IA Apprentissage (Python)]
```
L'IA reçoit la grille actuelle et retourne le meilleur coup à jouer.

### **Composants principaux**
1. **Agent d'apprentissage** : prend des décisions et met à jour ses connaissances.
2. **Environnement de jeu** : représente la grille et applique les règles du Puissance 4.
3. **Mémoire d'expérience** : stocke les parties pour entraîner le modèle.
4. **Modèle d'apprentissage** : réseau de neurones (DQN) ou table de Q-Learning.
5. **API de communication** : permet au backend d'interagir avec l'IA.

## **Installation et Configuration**
### **Prérequis**
Assurez-vous d'avoir Python installé ainsi que les dépendances nécessaires :
```bash
pip install numpy torch gym fastapi uvicorn
```

### **Lancer l'IA en mode entraînement**
```bash
python train.py
```

### **Lancer l'IA en mode jeu**
```bash
python play.py
```

## **Modes de Fonctionnement**
### **1. Entraînement**
- L'IA joue des milliers de parties contre elle-même.
- Elle met à jour ses poids de réseau neuronal en fonction des résultats.
- Elle ajuste ses décisions grâce à la fonction de récompense.

### **2. Mode de Jeu**
- L'IA reçoit un état de la grille et choisit un coup optimal selon sa politique d'action.
- L'API envoie le coup sélectionné au backend.

## **Fonctionnement de l'algorithme**
### **Q-Learning / DQN**
L'agent suit le cycle :
1. **Observer** l'état actuel de la grille.
2. **Sélectionner une action** en fonction d'une politique d'exploration/exploitation (ε-greedy).
3. **Appliquer l'action** et observer la récompense.
4. **Mettre à jour la valeur Q** pour apprendre du résultat.
5. **Répéter le processus** jusqu'à convergence.

## **API REST (Facultatif)**
Si l'IA expose une API pour le backend :
### **Endpoint : Jouer un coup**
```http
POST /play
```
**Payload :**
```json
{
  "grid": [[0,0,0,0,0,0,0],
           [0,0,0,0,0,0,0],
           [0,0,0,0,0,0,0],
           [0,0,0,0,0,0,0],
           [0,0,0,0,0,0,0],
           [0,0,0,1,2,0,0]]
}
```
**Réponse :**
```json
{
  "move": 3
}
```

## **Améliorations Futures**
- Implémentation de **Monte Carlo Tree Search (MCTS)** pour améliorer la prise de décision.
- Ajout d’un **mode de difficulté ajustable**.
- Optimisation des performances d’apprentissage.

---

🚀 **L'IA Apprentissage est prête à évoluer !**

