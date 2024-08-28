# Java-Notions

Les *records* en Java sont une fonctionnalité introduite dans Java 14 (en tant que fonctionnalité en préversion) et rendue standard dans Java 16. Un *record* est une classe spéciale qui simplifie la création de classes immuables servant principalement à contenir des données. L'objectif des *records* est de réduire le code répétitif nécessaire pour écrire des classes qui sont principalement des porte-données, tout en fournissant automatiquement des méthodes comme `equals()`, `hashCode()`, et `toString()`.

### 1. **Définir un *Record* en Java :**

Pour définir un *record*, on utilise le mot-clé `record` suivi du nom du *record* et de ses champs entre parenthèses. Par exemple, pour un *record* qui représente une personne avec un nom et un âge :

```java
public record Person(String name, int age) {}
```

### 2. **Caractéristiques des *Records* :**

- **Immutabilité** : Les champs d'un *record* sont implicitement `final`, ce qui signifie qu'une fois initialisés, ils ne peuvent pas être modifiés.
- **Constructeur Canonique** : Un constructeur par défaut est fourni pour initialiser tous les champs.
- **Méthodes Automatiques** : Les méthodes `equals()`, `hashCode()`, et `toString()` sont automatiquement générées en fonction des champs définis.
- **Accesseurs** : Pour chaque champ, un accesseur (getter) est généré avec le nom du champ.

### 3. **Utilisation des *Records* :**

Voici un exemple concret de la définition et de l'utilisation d'un *record* :

```java
public class Main {
    public static void main(String[] args) {
        Person person = new Person("Alice", 30);
        
        // Utilisation des accesseurs
        System.out.println("Name: " + person.name());
        System.out.println("Age: " + person.age());
        
        // Utilisation de la méthode toString() générée automatiquement
        System.out.println(person.toString()); // Affiche : Person[name=Alice, age=30]
        
        // Utilisation de equals() et hashCode() générés automatiquement
        Person anotherPerson = new Person("Alice", 30);
        System.out.println(person.equals(anotherPerson)); // true
    }
}

public record Person(String name, int age) {}
```

### 4. **Ajout de Méthodes et Constructeurs Personnalisés :**

Vous pouvez ajouter vos propres méthodes et constructeurs à un *record* si nécessaire. Par exemple, pour ajouter une validation :

```java
public record Person(String name, int age) {
    public Person {
        if (age < 0) {
            throw new IllegalArgumentException("Age cannot be negative");
        }
    }
    
    public String greet() {
        return "Hello, my name is " + name;
    }
}
```

### 5. **Avantages des *Records* :**

- **Moins de Boilerplate** : Les *records* réduisent le code standard, ce qui rend le code plus concis et lisible.
- **Sémantique** : Le mot-clé `record` signale clairement qu'une classe est utilisée comme une simple collection de données, ce qui améliore la compréhension du code.
- **Immutabilité** : Encourage la programmation immuable, ce qui est bénéfique pour l'écriture de code concurrent et sécurisé.

### Conclusion



The power of REST lies in the way it references a Resource, and what the Request and Response look like for each CRUD operation. Let’s take a look at what our API will look like when we're done with this course:

For CREATE: use HTTP method POST.
For READ: use HTTP method GET.
For UPDATE: use HTTP method PUT.
For DELETE: use HTTP method DELETE.



Les *records* en Java sont une fonctionnalité puissante pour créer des classes immuables de manière concise. Ils sont parfaits pour les classes porte-données où les principales préoccupations sont le stockage et la manipulation de valeurs, sans nécessiter des méthodes complexes ou des comportements supplémentaires.
