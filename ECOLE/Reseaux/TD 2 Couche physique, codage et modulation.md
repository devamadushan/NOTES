
#couche-physique 

### **Propagation du signal**
- **Onde** : Variation continue ou discontinue du signal dans le temps, exemple : sinusoïdale.
- **Amplitude (A)** : Valeur maximale (crête) de l’onde.
- **Fréquence (f)** : Nombre de répétitions par seconde (Hertz).
- **Période (T)** : Temps pour une répétition complète, T=1fT = \frac{1}{f}T=f1​.
- **Phase (ϕ)** : Décalage dans le temps de l’onde.


EX :
**Déterminer les composantes fréquentielles du signal**
- Analyser le signal ==s(t)=13sin⁡(2πf0t)+sin⁡(6πf0t)+13sin⁡(3⋅2πf0t)s(t) = \frac{1}{3} \sin(2 \pi f_0 t) + \sin(6 \pi f_0 t) + \frac{1}{3} \sin(3 \cdot 2 \pi f_0 t)s(t)=31​sin(2πf0​t)+sin(6πf0​t)+31​sin(3⋅2πf0​t)== pour en extraire ses différentes fréquences.
- Identifier combien de fréquences le composent et représenter graphiquement chacune de ces composantes sinusoïdales en les superposant pour voir la somme.
**Périodicité et période du signal s(t)s(t)s(t)**
- Vérifier si le signal s(t)s(t)s(t) est périodique en examinant si les fréquences présentes permettent une répétition cohérente dans le temps.
- Calculer la période TTT du signal si la périodicité est confirmée, en se basant sur la fréquence fondamentale f0f_0f0​.
### **Décomposition en séries de Fourier** :
- **Séries de Fourier** : Décomposition d’un signal périodique en somme de sinusoïdes.
- **Harmonique** : Fréquence multiple de la fréquence fondamentale.
- **Spectre fréquentiel** : Représentation des fréquences et amplitudes des harmoniques.
- **Bande passante** : Plage de fréquences transmises sans déformation significative.
### **Bande passante et codage** :
- **NRZ (Non Return to Zero)** : Codage binaire avec deux niveaux (ex. +1V et -1V).
- **Débit** : Vitesse de transmission (bits/s).
- **Fréquence fondamentale** : Fréquence de base du signal périodique.

### **Bruit et rapport signal/bruit (SNR)** :
- **Bruit** : Perturbation qui altère le signal.
- **Rapport Signal/Bruit (SNR)** : Mesure la qualité de la transmission (en dB).

### **Capacité du canal et loi de Shannon** :

- **Capacité (C)** : Débit binaire maximal théorique d’un canal bruité, C=Blog⁡2(1+PSPN)C = B \log_2 (1 + \frac{P_S}{P_N})C=Blog2​(1+PN​PS​​).
- **Bande passante (B)** : Plage de fréquences transmises par le canal.

### **Codage en ligne** :

- **Codage binaire à M-aire** : Transformation de bits en symboles.
- **Rapidité de modulation** : Vitesse de transmission des symboles (en bauds).
- **Codage Manchester** : Transition en milieu de période pour encoder les bits.
### **Modulation** :
- **Modulation d'amplitude (AM)** : Variation de l’amplitude du signal en fonction des données.
- **Modulation de phase (PM)** : Variation de la phase pour transmettre des informations.
- **QPSK, QAM** : Techniques combinant amplitude et phase (utilisées en ADSL, Wi-Fi).

### **Numérisation** :
- **Échantillonnage** : Prélèvement périodique pour convertir un signal continu en discret.
- **Théorème de Nyquist** : Fréquence d’échantillonnage doit être au moins 2 fois la fréquence maximale du signal.
- **Quantification** : Représentation de chaque échantillon par une valeur numérique.
- **MIC (Modulation par Impulsion et Codage)** : Codage avec un nombre défini de niveaux.