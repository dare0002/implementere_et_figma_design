# Refleksion af Implementere et Figma-design

Jeg ønsker, at jeg havde startet med at sætte BaseLayout, variabler, CSS osv. korrekt op fra begyndelsen uden at stresse mig igennem, fordi jeg følte mig bagud. Jeg har nu lært at det er en bedre arbejdsmetode at tage mig tid og få al basen på plads, før jeg begynder at kode på komponenter, sider osv. 

Jeg har lært utrolig meget om teknikker og principper og fået en bedre forståelse, når jeg f.eks. har failet med ting og efterfølgende fået tingene forklaret for mig. Jeg synes også at jeg har blevet bedre på at spørge om hjælp og forstå at det er okay at fejle. 

Mit mål fremover er at blive bedre på at kode generelt, da det har været en udfordning for mig. Jeg vil gerne blive bedre på at kode, så alt bliver responsivt med f.eks. container queries, bruge clamp for at opnp korrekt konstistens og rød tråd, blive bedre til at vide, hvordan jeg skal opdele elementer ud fra en skabelon samt at bruge nesting i min CSS. 

Jeg synes at undervisningen har været god, der har været meget information, men det er selvfølgelig forståeligt, da vi skal nå så meget :) Og hjælpen jeg har fået til vejledning har været mega god, så mange tak for det! 


# Udfordninger

- At kode responsivt med container queries

- At bruge og forstå hvordan @layers fungerer 

- Fetching ("singleview" er lige nu på Case Study, og er ikke blevet fetchet. Men mit mål er at lære mig det til næste projekt og forstå processen bedre). 

- Et generelt problem, jeg har, er at jeg synes, jeg har udfordringer med at starte et projekt. Jeg ved ikke altid hvor jeg skal begynde, eller hvad jeg skal fokusere på. Det tager lang tid for mig at lære og forstå nye ting. Men efter dette projekt er det blevet lidt mere tydeligt, hvad jeg skal starte med næste gang, da jeg har fået så god hjælp til lektionerne. 


# Successer

- Jeg har lært at læse mockups fra Figma og forsøge implementere dem selv og at efterligne det. 
- Fået en bedre forståelse af container queries
- Lært mig nesting (jeg har dok ikke implementeret det på hele min CSS, men det vil jeg gøre fremover, da det er virkelig smart måde at arbejde på)
- Fået en bedre forståelse for Flow-Space, og hvorfor det er smart at andvende
- Jeg synes, at jeg forstod fetching bedre denne gang i dette projekt. Selvom jeg ikke fik lavet single view, er jeg glad, for at jeg prøvde med EmployeeSection och EmployeeCard. 
- Jeg har blevet bedre på at bruge Astro


# Teknikker & principper 

- Container queries: 

Jeg har fået en bedre forståelse af container queries. Jeg synes stadig, at det er svært, men jeg forstår det bedre nu og vil forsøge at implementere det fremover på mine projekter. 


Her er et eksempel på hvordan jeg har implementeret det i min kode: 

```css
@layer components {
    li {
      
    }
    article {
      container: employeecard / inline-size;
      color: var(--body-text);
      background: var(--bg-card);

      .card {
        display: grid;
        gap: .5rem;

        @container employeecard (width > 400px) {
          grid-template-columns: 1fr 1fr;
        }
      }
    }
}

Her har jeg defineret article elementet som en container ved navn employeecard, som skal baseres på inline-size. 

.card definerer "stilarter" for elementer med klassen .card inde i article. F.eks. at .card- elementet skal bruge grid og gap. 

@container sektionen gør, at det bliver en responsiv regel, der gælder for .card-elementet, hvis article (employeecard) har en bredde, der er større end 400px. Når bredden er større end 400px, skal employeecard opdeles i 2 kolonner (1fr 1fr). 

```

- Nesting: 

Jeg har brugt teknikken nesting på visse steder i min kode. 

```css
@layer components {
        main{
            background: #FBC336;

        .container {
            display: flex;
            padding: 8rem;
            gap: 2rem;
        }

        .btn-experience {
            background: #fff;
            border-radius: 1.25rem;
        }

        .content-text p{
            font-size: 1.125rem;
            color: #181818;
        }
        }
    }

Her er stilarterne for mine klasser nestet ind i main elementet, for at skabe en mere organiseret - og en vedligeholdelsesvenlig kode/struktur. 


```

- Layer: 

Jeg har brugt @layer for at organisere og kontrollere dette projekts CSS, da det hjælper mig at styre hvilken rækkefølge/prioritet de forskellige stilarter skal have. 

```css

@layer reset, global, components, overrides;

@import url("./reset.css") layer(reset);
@import url("./overrides.css") layer(overrides);


@layer global {
    html {
        --primary-text: #595566; 
        --title-card: #FFF;
        --heading-font: "Cabin", sans-serif;
        --primaryfont: "Lato", sans-serif;


        --black: #181818;
        --white: #fff;
        --lightgray: #F5F5F5;
        --yellow: #FFCC4A;
        --green: #4EAF4E;

        color: var(--body-text);
        line-height: 1.5;

        max-width: 120rem;
    }
}

Her bliver overrides andvendt først, efterfølgt af components, global og til sidst reset. 

Overrides indeholder stilarter der skal overskrive tidligere stilarter. 

Components indeholder stilarter for specifikke komponenter.

Global indeholder stilarter der anvendes på tværs af hele sitet. 

Reset indeholder basis stilarter for at nulstille CSS fra de forskellige browsers. 


```

- Flow Space: 

Jeg har brugt flow-space for at skabe en konstistent layout og responsivitet. 


```html

<div class="flow">

Her er et eksempel på hvordan jeg har brugt det i min html- kod. 

```

```css
.flow {
    >*+* {
        margin-top: var(--flow-space, 1em);
    }

    h2 {
        --flow-space: 2rem;
    }

    p {
        --flow-space: 1rem;
    }

    hr {
        --flow-space: 2rem;
    }

    h6 {
        --flow-space: 3rem;
    }
}

Denne kode er fra @layer overrides hvor jeg har tilpasset --flow-space for forskellige elementer, der gør at jeg kan styre afstanden mellem disse elementer uden at skulle definere marginer per hvert element. 
```
