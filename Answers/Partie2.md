# Youssef Bouslama
## Reponse Partie II
### Questions Générales

1. **C'est quoi Git ? Et la différence entre Git et SVN ?**  
   Git est pour gérer les versions de projet.  
   - **Git** : Système distribué, peut travailler sans Internet.  
   - **SVN** : Système centralisé, besoin du serveur.

2. **A quoi sert composer.lock ?**  
   Il garde les versions exactes des dépendances.  
   - Evite les surprises quand on installe sur d'autres machines.

3. **Différence entre require et require-dev ?**  
   - **require** : Dépendances pour l'application.  
   - **require-dev** : Dépendances pour dev/test.

4. **Object Pool Pattern c'est quoi ?**  
   Réutilise des objets au lieu d'en créer à chaque fois. Évite la perte de ressources.

5. **git diff sert à quoi ?**  
   Montre les différences entre fichiers ou commits.

6. **Différence entre git rebase et git merge ?**  
   - **merge** : Combine branches, garde l'historique.  
   - **rebase** : Fusionne, mais rend l'historique plus propre.

---

### Javascript

1. **CORS c'est quoi ?**  
   Permet ou bloque des requêtes entre sites différents.

2. **Différence entre == et === ?**  
   - **==** : Compare avec conversion automatique.  
   - **===** : Compare sans conversion.

3. **Résultat de if ("0" == "true") ?**  
   false, car "0" devient 0 et "true" devient 1.

4. **this c'est quoi ?**  
   C'est le contexte d'exécution. Ex : objet global, ou objet qui appelle.

5. **Asynchronisme et Promises ?**  
   - Asynchrone : exécute des tâches sans bloquer.  
   - Promises : pour gérer le résultat.  
   - async/await : syntaxe plus simple.

---

### CSS

1. **Différence inline/block ?**  
   - **inline** : Pas de retour à la ligne.  
   - **block** : Occupe toute la largeur.

2. **Faire responsive sans media queries ?**  
   Oui, avec `grid`, `%`, ou `clamp()`.

3. **inline-block, flex, float : avantages/inconvénients ?**  
   - **inline-block** : Simple, mais limité.  
   - **flex** : Puissant et moderne.  
   - **float** : Vieux et parfois compliqué.

4. **::before et ::after ?**  
   Ajout de contenu ou styles avant/après un élément HTML.

---

### PHP

1. **Programme qui affiche de 1 à 100 :**
    ```php
    for ($i = 1; $i <= 100; $i++) {
        if ($i % 3 == 0 && $i % 5 == 0) echo "DevOps\n";
        elseif ($i % 3 == 0) echo "Dev\n";
        elseif ($i % 5 == 0) echo "Ops\n";
        else echo "$i\n";
    }
    ```

2. **Fonction pour nombre premier :**
    ```php
    function isPrime($num) {
        if ($num <= 1) return false;
        for ($i = 2; $i <= sqrt($num); $i++) {
            if ($num % $i == 0) return false;
        }
        return true;
    }
    echo isPrime(73) ? 'Prime' : 'Composite';
    ```

3. **Code PHP avec tableau :**
    ```php
    $array = [3, 8, -4, 0, 2, -9];
    foreach ($array as &$item):
        $item = ($item >= 0) ? $item : pow($item, 2);
    endforeach;
    print_r($array);
    ```
   Résultat : `[3, 8, 16, 0, 2, 81]`.

---

### DATABASE

1. **Nombre d'inscriptions par jour :**
    ```sql
    SELECT DATE(create_at), COUNT(*) 
    FROM employee 
    GROUP BY DATE(create_at);
    ```

2. **Employés inscrits le 03/10/2021 :**
    ```sql
    SELECT * FROM employee WHERE DATE(create_at) = '2021-10-03';
    ```

3. **Emails débutant par consonne + chiffre avant @ :**
    ```sql
    SELECT * 
    FROM employee 
    WHERE email REGEXP '^[^aeiouAEIOU]' AND email REGEXP '[0-9]+@';
    ```

4. **Mettre noms en lowercase :**
    ```sql
    UPDATE employee SET first_name = LOWER(first_name), last_name = LOWER(last_name);
    ```

5. **Renommer colonne create_at :**
    ```sql
    ALTER TABLE employee CHANGE create_at date_creation DATETIME;
    ```

6. **Différence entre DELETE et TRUNCATE ?**
   - **DELETE** : Supprime avec condition, annulable.  
   - **TRUNCATE** : Tout supprime, irréversible.

7. **Employés avec salaire > somme des 2 salaires mini :**
    ```sql
    SELECT * 
    FROM employee 
    WHERE salaire > (
        SELECT SUM(salaire) 
        FROM (SELECT salaire FROM employee ORDER BY salaire ASC LIMIT 2) AS min_salaries
    );
    ```
