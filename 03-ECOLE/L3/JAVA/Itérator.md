
````
import java.util.Iterator;

public class MyCollection<T> implements Iterable<T> {
    private T[] elements;
    private int size;

    // Constructeur de la collection
    @SuppressWarnings("unchecked")
    public MyCollection(int capacity) {
        elements = (T[]) new Object[capacity]; // Créer un tableau générique
        size = 0;
    }

    // Méthode pour ajouter un élément à la collection
    public void add(T element) {
        if (size < elements.length) {
            elements[size++] = element;
        } else {
            System.out.println("Collection pleine !");
        }
    }

    // Retourne la taille de la collection
    public int getSize() {
        return size;
    }

    // Implémentation de la méthode iterator()
    @Override
    public Iterator<T> iterator() {
        return new MyCollectionIterator();
    }

    // Classe interne qui implémente Iterator<T>
    private class MyCollectionIterator implements Iterator<T> {
        private int currentIndex = 0;

        // Vérifie s'il y a un élément suivant
        @Override
        public boolean hasNext() {
            return currentIndex < size;
        }

        // Retourne l'élément suivant et avance l'index
        @Override
        public T next() {
            if (!hasNext()) {
                throw new IllegalStateException("Pas d'élément suivant !");
            }
            return elements[currentIndex++];
        }

        // (Optionnel) Méthode pour supprimer un élément (non implémentée ici)
        @Override
        public void remove() {
            throw new UnsupportedOperationException();
        }
    }
}

````