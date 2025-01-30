```python
from tensorflow.keras.models import Model
from tensorflow.keras.layers import Input, Dense, concatenate

# Définir la première entrée
input1 = Input(shape=(10,), name="Input_1")
x1 = Dense(32, activation="relu")(input1)

# Définir la deuxième entrée
input2 = Input(shape=(15,), name="Input_2")
x2 = Dense(32, activation="relu")(input2)

# Combiner les deux entrées
combined = concatenate([x1, x2])

# Ajouter des couches communes
x = Dense(64, activation="relu")(combined)
output = Dense(1, activation="sigmoid", name="Output")(x)

# Créer le modèle
model = Model(inputs=[input1, input2], outputs=output)

# Compiler le modèle
model.compile(optimizer="adam", loss="binary_crossentropy", metrics=["accuracy"])

# Résumé du modèle
model.summary()

# Exemple d'entraînement
import numpy as np
data1 = np.random.rand(1000, 10)  # Données pour Input_1
data2 = np.random.rand(1000, 15)  # Données pour Input_2
labels = np.random.randint(0, 2, 1000)  # Labels (binaire)

model.fit([data1, data2], labels, epochs=10, batch_size=32)

```


```python
from tensorflow.keras.models import Model
from tensorflow.keras.layers import Input, Dense, Concatenate
import numpy as np

# 1. Définir les entrées
input1 = Input(shape=(10,), name="Input_1")  # Premier tableau (10 colonnes)
input2 = Input(shape=(15,), name="Input_2")  # Deuxième tableau (15 colonnes)

# 2. Ajouter des couches pour traiter chaque entrée
x1 = Dense(32, activation="relu")(input1)  # Traite Input_1 avec 32 neurones
x2 = Dense(32, activation="relu")(input2)  # Traite Input_2 avec 32 neurones

# 3. Combiner les deux entrées
combined = Concatenate()([x1, x2])  # Combine les deux branches

# 4. Ajouter des couches pour produire la sortie
x = Dense(64, activation="relu")(combined)  # Couche cachée avec 64 neurones
output = Dense(1, activation="sigmoid", name="Output")(x)  # Sortie binaire (0 ou 1)

# 5. Créer le modèle
model = Model(inputs=[input1, input2], outputs=output)

# 6. Compiler le modèle
model.compile(optimizer="adam", loss="binary_crossentropy", metrics=["accuracy"])

# 7. Afficher un résumé
model.summary()

# 8. Générer des données aléatoires pour l'exemple
data1 = np.random.rand(1000, 10)  # 1000 exemples, 10 colonnes (Input_1)
data2 = np.random.rand(1000, 15)  # 1000 exemples, 15 colonnes (Input_2)
labels = np.random.randint(0, 2, 1000)  # 1000 étiquettes (0 ou 1)

# 9. Entraîner le modèle
model.fit([data1, data2], labels, epochs=10, batch_size=32)

# 10. Faire des prédictions
test_data1 = np.random.rand(5, 10)  # 5 nouveaux exemples pour Input_1
test_data2 = np.random.rand(5, 15)  # 5 nouveaux exemples pour Input_2

predictions = model.predict([test_data1, test_data2])
print("Prédictions :", predictions)

```