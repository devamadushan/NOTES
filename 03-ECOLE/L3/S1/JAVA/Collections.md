

| LIST       | SET        | QUEUE      | MAP           |
| ---------- | ---------- | ---------- | ------------- |
| ArrayList  | HashSet    | ArrayDeque | HashMap       |
| LinkedList | LinkedList |            | linkedHashMap |
## **1. Interface `List`**

### **Caractéristiques :**

- Une **collection ordonnée** d'éléments.
- Les **doublons sont autorisés.**
- Accès aux éléments par **index**.
- Les éléments sont ajoutés dans un **ordre défini.**

### **Méthodes clés :**

1. **Manipulation d'éléments par index :**
    
    - `E get(int index)` : Retourne l'élément à une position donnée.
    - `E set(int index, E element)` : Remplace l'élément à une position donnée.
    - `void add(int index, E element)` : Insère un élément à une position donnée.
    - `E remove(int index)` : Supprime l'élément à une position donnée.
2. **Recherche :**
    
    - `int indexOf(Object o)` : Retourne l'index de la première occurrence d'un élément.
    - `int lastIndexOf(Object o)` : Retourne l'index de la dernière occurrence d'un élément.
3. **Sous-liste :**
    
    - `List<E> subList(int fromIndex, int toIndex)` : Retourne une vue de la liste entre deux index.

---

## **2. Interface `Set`**

### **Caractéristiques :**

- Une collection **non ordonnée**.
- Les **doublons ne sont pas autorisés.**
- Garantit l'unicité des éléments.

### **Méthodes clés :**

1. **Ajout et suppression :**
    
    - `boolean add(E e)` : Ajoute un élément au `Set`. Renvoie `false` si l'élément existe déjà.
    - `boolean remove(Object o)` : Supprime un élément du `Set`.
2. **Vérification :**
    
    - `boolean contains(Object o)` : Vérifie si un élément est présent dans le `Set`.
3. **Opérations sur les ensembles :**
    
    - Hérite des méthodes de `Collection`, comme `addAll`, `retainAll`, et `removeAll` pour manipuler plusieurs éléments.

---

## **3. Interface `Queue`**

### **Caractéristiques :**

- Organise les éléments selon un **ordre spécifique** (généralement FIFO, mais peut être basé sur des priorités).
- Utilisée pour modéliser des files d'attente.

### **Méthodes clés :**

1. **Ajout d'éléments :**
    
    - `boolean offer(E e)` : Ajoute un élément à la file. Renvoie `false` si l'ajout échoue.
    - `boolean add(E e)` : Ajoute un élément. Lance une exception si l'ajout échoue.
2. **Accès à l'élément en tête :**
    
    - `E peek()` : Retourne l'élément en tête sans le supprimer. Renvoie `null` si la file est vide.
    - `E element()` : Similaire à `peek()`, mais lance une exception si la file est vide.
3. **Suppression de l'élément en tête :**
    
    - `E poll()` : Supprime et retourne l'élément en tête. Renvoie `null` si la file est vide.
    - `E remove()` : Similaire à `poll()`, mais lance une exception si la file est vide.

---

## **4. Interface `Map`**

### **Caractéristiques :**

- Associe des **clés uniques** à des **valeurs**.
- Chaque clé ne peut apparaître qu'une seule fois.
- Les valeurs peuvent être dupliquées.

### **Méthodes clés :**

1. **Ajout et mise à jour :**
    
    - `V put(K key, V value)` : Ajoute ou met à jour une paire clé/valeur.
    - `void putAll(Map<? extends K,? extends V> m)` : Copie toutes les paires clé/valeur d'un autre `Map`.
2. **Accès aux données :**
    
    - `V get(Object key)` : Retourne la valeur associée à une clé.
    - `boolean containsKey(Object key)` : Vérifie si une clé est présente.
    - `boolean containsValue(Object value)` : Vérifie si une valeur est présente.
3. **Suppression :**
    
    - `V remove(Object key)` : Supprime une paire clé/valeur.
4. **Vues des clés, valeurs et entrées :**
    
    - `Set<K> keySet()` : Retourne un `Set` contenant toutes les clés.
    - `Collection<V> values()` : Retourne une collection contenant toutes les valeurs.
    - `Set<Map.Entry<K,V>> entrySet()` : Retourne un `Set` contenant toutes les paires clé/valeur sous forme d'objets `Map.Entry`.

---

## **5. Classe `ArrayList` (Implémentation de `List`)**

### **Caractéristiques :**

- Basée sur un **tableau dynamique**.
- Permet un **accès rapide** aux éléments par index (`O(1)`).
- Ajout ou suppression d'éléments en **milieu/début** est coûteux (`O(n)`).

### **Méthodes spécifiques :**

- `ensureCapacity(int minCapacity)` : Augmente la capacité interne si nécessaire.
- `trimToSize()` : Réduit la capacité interne pour correspondre au nombre d'éléments.

---

## **6. Classe `LinkedList` (Implémentation de `List` et `Deque`)**

### **Caractéristiques :**

- Basée sur une **liste chaînée doublement liée**.
- Ajout ou suppression d'éléments en **début/milieu** est rapide (`O(1)` pour le début).

### **Méthodes spécifiques :**

- `void addFirst(E e)` et `void addLast(E e)` : Ajout au début/fin de la liste.
- `E getFirst()` et `E getLast()` : Accès au premier/dernier élément.
- `E removeFirst()` et `E removeLast()` : Suppression du premier/dernier élément.

---

## **7. Classe `HashMap` (Implémentation de `Map`)**

### **Caractéristiques :**

- Basée sur une **table de hachage**.
- Les clés ne sont pas triées ni ordonnées.
- Recherches, insertions, et suppressions rapides (`O(1)` en moyenne).

### **Méthodes spécifiques :**

- Hérite des méthodes de `Map`.

---

## **8. Classe `LinkedHashMap` (Implémentation de `Map`)**

### **Caractéristiques :**

- Basée sur une **table de hachage**.
- Conserve l'**ordre d'insertion** des paires clé/valeur.

### **Méthodes spécifiques :**

- `protected boolean removeEldestEntry(Map.Entry<K,V> eldest)` : Méthode redéfinissable pour supprimer automatiquement les entrées les plus anciennes.

---

### **Différences clés entre `List`, `Set`, `Queue`, et `Map` :**

1. **Stockage :**
    
    - **`List`** : Ordonnée, éléments indexés, doublons autorisés.
    - **`Set`** : Non ordonnée (ou triée dans certaines implémentations), éléments uniques.
    - **`Queue`** : Ordre spécifique, souvent FIFO.
    - **`Map`** : Paires clé/valeur, clés uniques.
2. **Ordre :**
    
    - **`List`** : Conserve l'ordre des éléments.
    - **`Set`** : Pas d'ordre garanti (sauf `LinkedHashSet`).
    - **`Queue`** : Ordre basé sur FIFO ou priorité.
    - **`Map`** : Clés non ordonnées (sauf `LinkedHashMap` ou `TreeMap`).
3. **Doublons :**
    
    - **`List`** : Doublons autorisés.
    - **`Set`** : Pas de doublons.
    - **`Queue`** : Doublons autorisés.
    - **`Map`** : Doublons dans les valeurs, mais pas dans les clés.