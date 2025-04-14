# Atelier-6
## Exercice 1 
***Implémentation de la Classe Point en TypeScript***
### Description:
Cet exercice implémente une classe Point en TypeScript dans le cadre d'un exercice de programmation orientée objet. La classe représente un point dans un système de coordonnées 2D avec des coordonnées x et y, offrant la fonctionnalité de calculer la distance entre deux points.
### Objectif
L'objectif principal de ce travail pratique est de se familiariser avec les concepts de la Programmation Orientée Objet en TypeScript.
#### Détails d'implémentation
=> **Classe Point**
La classe Point est définie avec les attributs et fonctionnalités suivants :
Attributs

=> abs : Un attribut privé de type number représentant la coordonnée x

=> ord : Un attribut privé de type number représentant la coordonnée y

=> **Constructeur**

=> Prend deux paramètres (x, y) et initialise les coordonnées du point
```js
 constructor(x :number , y: number){
        this.abs=x;
        this.ord=y;
    }
```

=> **Méthodes d'accès**

=> Getters : getAbs() et getOrd() pour récupérer les valeurs des coordonnées
=> Setters : setAbs(abs) et setOrd(ord) pour modifier les valeurs des coordonnées
```js
 public getAbs(): number {
        return this.abs;

    }
    public getOrd(): number {
        return this.ord;
    }
    public setAbs(abs:number){
        this.abs=abs;
    }

    public setOrd(ord: number){
        this.ord=ord;

    }

```
#### Fonctionnalité

=> **calculerDistance(p: Point)** : Calcule la distance euclidienne entre le point courant (this) et un autre point p

=> Utilise la formule : distance = √((x2-x1)² + (y2-y1)²)

=> Implémente ceci en utilisant les fonctions de la bibliothèque Math de JavaScript : Math.sqrt() et Math.pow()
```js
 public calculerDistance(p: Point): number{
        const x = this.abs-p.getAbs();
        const y = this.ord-p.getOrd();

        return Math.sqrt(Math.pow(x,2)+ Math.pow(y,2)); 
    }
```

### Conclusion :
Cette implémentation de la classe Point démontre les principes fondamentaux de la programmation orientée objet en TypeScript, notamment l'encapsulation avec l'utilisation d'attributs privés et de méthodes d'accès. La fonctionnalité de calcul de distance illustre comment les méthodes d'une classe peuvent manipuler à la fois les données de l'instance courante et celles d'autres instances. Ce travail pratique fournit une base solide pour comprendre comment structurer des classes en TypeScript et comment implémenter des algorithmes mathématiques simples dans un contexte orienté objet.

## Exercice 2
***Système de Gestion de Personnes et Adresses en TypeScript***
### Description
Cet exercie implémente un système de gestion de personnes et d'adresses en TypeScript dans le cadre d'un exercice de programmation orientée objet. Le système est composé de trois classes principales permettant de manipuler des informations personnelles et de localisation.
### Objectif
L'objectif principal de ce travail pratique est de se familiariser avec les concepts avancés de la Programmation Orientée Objet en TypeScript, particulièrement les relations entre classes et la manipulation de collections d'objets.
### Structure du Projet
Le projet est organisé en quatre fichiers TypeScript principaux :

=> Adresse.ts - Définition de la classe Adresse

=> Personne.ts - Définition de la classe Personne

=> ListePersonnes.ts - Définition de la classe de gestion des collections de personnes

=> main.ts - Fichier principal contenant des exemples d'utilisation

#### Détails d'implémentation
**Classe Adresse**

=> La classe Adresse représente une adresse physique avec les attributs suivants :

rue : Attribut privé de type chaîne de caractères
ville : Attribut privé de type chaîne de caractères
codePostal : Attribut privé de type chaîne de caractères
```
    private rue : string;
    private ville : string;
    private codePostal : string;

```

=> La classe fournit des getters et setters pour tous ses attributs ainsi qu'un constructeur permettant d'initialiser une adresse complète.
```
   constructor(rue: string, ville: string, codePostal: string) {
        this.rue = rue;
        this.ville = ville;
        this.codePostal = codePostal;
    }

    public getRue(): string {
        return this.rue;
    }

    public setRue(rue: string): void {
        this.rue = rue;
    }
```
**Classe Personne**

=> La classe Personne représente un individu avec les attributs suivants :

nom : Attribut privé de type chaîne de caractères
sexe : Attribut privé de type chaîne de caractères (valeurs possibles : 'M' ou 'F')
adresses : Attribut privé de type tableau d'objets Adresse
```
private nom: string;
    private sexe: string;
    private adresses: Adresse[];
```

Cette classe implémente la relation "une personne peut avoir plusieurs adresses" à travers un tableau d'objets Adresse. Elle fournit également des getters et setters pour tous ses attributs.
```
 constructor(nom: string, sexe: string, adresses: Adresse[]) {
        this.nom = nom;
        this.sexe = sexe;
        this.adresses = adresses;
    }

    public getNom(): string {
        return this.nom;
    }

    public setNom(nom: string): void {
        this.nom = nom;
    }

```
**Classe ListePersonnes**

=> La classe ListePersonnes gère une collection de personnes avec l'attribut suivant :

personnes : Attribut privé de type tableau d'objets Personne
```
private personnes : Personne [];

    constructor(personnes: Personne[]) {
        this.personnes = personnes;
    }

```
=> Elle implémente les fonctionnalités suivantes :

***findByNom(s: string)*** : Recherche une personne par son nom et retourne le premier objet correspondant ou null si aucune correspondance n'est trouvée
```
 public findByNom(s: string): Personne | null {
        for (let personne1 of this.personnes) {
            if (personne1.getNom() === s) {
                return personne1;
            }
        }
        return null;
    }
```
***findByCodePostal(cp: string)***: Vérifie si au moins une personne possède une adresse avec le code postal spécifié et retourne un booléen
```
 public findByCodePostal(cp: string): boolean {
        for (let personne1 of this.personnes) {
            for (let a of personne1.getAdresses()) {
                if (a.getCodePostal() === cp) {
                    return true;
                }
            }
        }
        return false;
    }
```
***countPersonneVille(ville: string)*** : Calcule le nombre de personnes ayant au moins une adresse dans la ville spécifiée
```
 public countPersonneVille(ville: string): number {
        let count = 0;
        for (let personne1 of this.personnes) {
            if (personne1.getAdresses().some(a => a.getVille() === ville)) {
                count++;
            }
        }
        return count;
    }
```
### Utilisation

=> Le fichier main.ts démontre l'utilisation des classes en :

****Créant plusieurs objets Adresse****
****Créant plusieurs objets Personne avec leurs adresses associées****
****Créant une instance de ListePersonnes pour gérer ces personnes****
****Effectuant diverses recherches et opérations sur cette liste****

### Conclusion
Cette implémentation illustre les concepts fondamentaux de la programmation orientée objet en TypeScript, notamment l'encapsulation des données avec des attributs privés, l'utilisation de getters et setters, et les relations entre classes. Le projet démontre également comment manipuler des collections d'objets et effectuer des recherches et calculs sur ces collections.
Ce système offre une base solide pour comprendre comment structurer des applications plus complexes en TypeScript en utilisant les principes de la POO, et comment implémenter des fonctionnalités de recherche et d'analyse sur des ensembles de données.
