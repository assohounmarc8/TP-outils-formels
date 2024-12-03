
### Rapport du TP : Système de Contrôle d'Accès

#### **Introduction**

Dans ce travail pratique, l'objectif était de créer un **système de contrôle d'accès** en Java qui permet à un utilisateur d'entrer un **numéro de carte** et un **code secret** pour valider l'accès à un système sécurisé. Si les informations sont correctes, l'accès est accordé. Si elles sont incorrectes, l'accès est refusé. Le système doit également gérer les **tentatives incorrectes** et activer une **alarme** après trois erreurs. Ce rapport explique comment le système a été conçu et les étapes suivies pour atteindre ces objectifs.

---

### **1. Spécifications Initiales**

Le système devait permettre aux utilisateurs de :
1. Entrer un **numéro de carte** et un **code secret**.
2. Vérifier si les informations saisies sont correctes.
3. Accorder l'accès si le **numéro de carte** et le **code** sont valides.
4. Refuser l'accès si l'une des informations est incorrecte.
5. Après trois tentatives incorrectes, **activer l'alarme** et **réinitialiser le système** après un délai de **10 secondes**.

Les règles logiques étaient donc simples :
- **Accès accordé** si les deux informations sont correctes.
- **Accès refusé** si l'une des informations est incorrecte.
- Après **trois tentatives incorrectes**, l'alarme se déclenche.

---

### **2. Description du Code**

#### **Automate**

Le système est basé sur un automate qui gère les **états** du contrôle d'accès. Les états sont les suivants :
1. **AttenteCarte** : L'utilisateur doit insérer une carte.
2. **VerificationCode** : Le système vérifie le code secret après l'insertion de la carte.
3. **AccesAccorde** : L'accès est accordé si la carte et le code sont corrects.
4. **AccesRefuse** : L'accès est refusé si l'une des informations est incorrecte.

Dans la classe `Automate`, nous avons défini ces états et créé des **transitions** entre eux en fonction de la validité du numéro de carte et du code secret. Les transitions sont effectuées par les méthodes `VerifCarte` et `VerifCode`.

#### **Vérification de la Carte et du Code**

Le programme commence par demander à l'utilisateur de saisir un **numéro de carte** et un **code secret**. Ensuite, il vérifie ces informations avec les **valeurs prédéfinies** (ici `VraiNumCarte` et `VraiCode`). Si les informations sont correctes, l'accès est **accordé**. Si elles sont incorrectes, l'accès est **refusé**, et l'utilisateur peut réessayer jusqu'à trois fois.

#### **Gestion des Tentatives Incorrectes et de l'Alarme**

Une fois que l'utilisateur a fait trois tentatives incorrectes, le système **active l'alarme**, attend **10 secondes**, puis **réinitialise** le système pour permettre une nouvelle tentative.

#### **Interaction avec l'Utilisateur**

Le programme propose un menu simple où l'utilisateur peut entrer son **numéro de carte** et **code secret**. Le programme vérifie ensuite la validité de ces informations. Si elles sont incorrectes, l'utilisateur peut réessayer jusqu'à trois fois avant que l'alarme ne soit déclenchée.

---

### **3. Défis Rencontrés et Solutions Apportées**

#### **Défis rencontrés :**

1. **Gestion des erreurs de saisie :**
   - Lors de la mise en œuvre de la logique de contrôle d'accès, j'ai rencontré des difficultés pour bien gérer les tentatives incorrectes. Initialement, je pensais que le programme devrait gérer les tentatives incorrectes de manière plus complexe, mais en fin de compte, une gestion simple avec un compteur de tentatives a suffi.
   
2. **Réinitialisation du système :**
   - Lorsque l'alarme se déclenche après trois tentatives incorrectes, il a fallu ajouter un délai de **10 secondes** avant de réinitialiser le système. Cela a nécessité l'utilisation de la fonction `Thread.sleep(10000)` pour faire une pause de 10 secondes. La gestion du délai a été simple, mais il a fallu être vigilant pour ne pas perturber le reste de l'exécution du programme.

#### **Solutions apportées :**

1. **Simplification de la gestion des erreurs :**
   - J'ai choisi de garder la gestion des tentatives incorrectes simple, avec un compteur de tentatives et un retour direct à la demande du numéro de carte et du code. Cela a permis de réduire la complexité tout en respectant les spécifications.

2. **Réinitialisation avec délai :**
   - Pour la réinitialisation du système, j'ai utilisé `Thread.sleep(10000)` pour introduire un délai de 10 secondes après l'activation de l'alarme. Cela a bien fonctionné pour respecter le délai imposé par les spécifications.

---

### **4. Résultats et Vérification**

Le programme fonctionne comme prévu :
- Lorsqu'un utilisateur entre les bonnes informations (numéro de carte et code), l'accès est accordé.
- Si l'une des informations est incorrecte, l'accès est refusé, et l'utilisateur peut réessayer jusqu'à trois fois.
- Après trois tentatives incorrectes, le système déclenche une alarme, attend 10 secondes, puis réinitialise le système pour permettre une nouvelle tentative.

---

### **5. Conclusion**

Ce travail pratique m'a permis de mieux comprendre la mise en œuvre des **automates finis** et la gestion des **états** dans un système de contrôle d'accès. En utilisant la **logique conditionnelle** et les **boucles**, j'ai pu créer un système simple mais fonctionnel qui vérifie les informations d'accès et gère les erreurs et les tentatives incorrectes de manière efficace.

Le système respecte bien les spécifications du TP et est flexible pour de futures extensions, comme l'ajout d'un plus grand nombre de cartes ou la gestion d'un utilisateur avec plusieurs informations d'accès.

Enfin, l'utilisation d'un délai de réinitialisation et d'une alarme après trois erreurs m'a permis de m'assurer que le système répond bien aux contraintes de sécurité. Ce TP a été une bonne occasion d'apprendre à structurer un programme en utilisant des concepts tels que les **automates**, les **états**, et la **gestion d'événements**.

---

### **Perspectives d'Amélioration**

1. **Gestion des utilisateurs multiples** : Le système pourrait être étendu pour gérer plusieurs utilisateurs avec des cartes et des codes différents.
2. **Sécurité améliorée** : Ajouter des mécanismes de sécurité supplémentaires, comme une gestion des tentatives d'accès avec une période de blocage plus longue.
3. **Interface graphique** : Le programme pourrait être amélioré en ajoutant une interface graphique pour rendre le système plus convivial.

En résumé, ce travail pratique a permis de concevoir un système simple mais efficace de contrôle d'accès avec des vérifications, des tentatives incorrectes, et une alarme, en utilisant des concepts de programmation importants tels que les automates et la gestion d'événements.
