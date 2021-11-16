# Multiplication

Prise en main de angular

Niveau : Deuxième année de BTS SIO SLAM

## Objectif 

Concevoir une application web qui affiche une table de multiplication (1 à 10), selon
une valeur soumise par l’utilisateur.

## Partie 1

Application mono-page qui fait usage d'un composant table-multiplication (conçu avec 'ng generate component components/table-multiplication').
Le composant utilise la methode Multiplication

```ts
  multiplication(): number[] {

    let table: number[] = [];
    if (this.chiffre) {
      for (let i = 1; i <= 10; i++) {
        let x = this.chiffre * i;
        table.push(x);
      }
      return table;
    }
    return table;
  }
```
les parametre :

```ts

 constructor() { }
  @Input() chiffre!: number;
  resultat: number[] = [];
   
```

## Création du formulaire 
 
J'ai crée un formulaire avec ident comme dans le cours et je l'ai paramétrer on m'inspirant du tp

```html

<section class="section">
    <div class="container">
        <div class="columns is-centered">
            <div class="column is-half">
                <form [formGroup]="identForm" (ngSubmit)="choix()">
                    <div class="field">
                        <label class="label">Entrez un nombre</label>
                        <div class="control">
                            <input  type="number" placeholder="chiffre" value="" formControlName="chiffre">
                        </div>
                    </div>
                    <div class="field is-grouped">
                        <div class="control">
                            <button class="button is-link" type="submit">Soumettre</button>
                        </div>
                    </div>
                </form>
            </div>
        </div>
    </div>
</section>

```

```ts


  identForm!: FormGroup;
  @Output() leChiffre = new EventEmitter<number>();
  @Output() nbTable = new EventEmitter<number>();
  constructor() { }

  ngOnInit(): void {
    this.identForm = new FormGroup({
      chiffre: new FormControl(''),
      nbTables: new FormControl('')
    });
  }

```


## Partie 2

Pour la partie 2 j'ai crée un autre composant tables-multiplication qui a une methode Counter

```ts
  counter(i: number) {
    return new Array(i);
  }
```
Pour créer le nombre de tableau et j'ai initialiser une valeur 10 Pour qu'il m'affiche 10 tableau comme dans les consigne 

```html
<app-ident  (leChiffre)="onChiffreAdded($event)" (nbTable)="nbTableAdded($event)"></app-ident>
<app-table-multiplication [chiffre]="chiffre" ></app-table-multiplication>
<app-tables-multiplication [nbTable]="nbtables"></app-tables-multiplication>
```

le html du 2eme composent son parent
```html

<table>
    <td *ngFor='let in of counter(nbTable + 1) ;let i = index'>
        <app-table-multiplication [chiffre]="i"></app-table-multiplication>
    </td>
</table>
```

## Defaut
~ Pas assez organiser
~ Pas assez compris angular
~ Pas assez investis 

### UML
j'ai pas eu assez de temps désoler monsieurs

Besoin de plus de cours et d'explication, j'aime bien la filière mais j'ai trop de mal c'est ça qui me bloque.
Mais j'aimerais bien devenir fort en developpement, j'espère que je vais y arriver au pire des cas je changerais de filiè.
Mes salutation distinguer.

Bonne correction 