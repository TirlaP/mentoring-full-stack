# CSS Selectors - Ghid Complet

## Introducere
Imaginează-ți că ai o cutie plină cu jucării diferite și vrei să găsești anumite jucării. CSS Selectors sunt ca niște "reguli de căutare" care te ajută să găsești exact jucăriile (elementele HTML) pe care vrei să le modifici.

## 1. Selectori de Bază

### 1.1 Selector Universal (*)
```css
* {
    margin: 0;
    padding: 0;
}
```
- Selectează TOATE elementele
- Folosit de obicei pentru reset CSS
- Ca și cum ai spune "vreau să afectez tot ce există pe pagină"
- **Atenție**: Folosește-l cu grijă pentru că poate afecta performanța

### 1.2 Selector de Element (Tag)
```css
p {
    color: blue;
}

h1 {
    font-size: 24px;
}
```
- Selectează toate elementele de acel tip
- E ca și cum ai spune "vreau toate paragrafele să fie albastre"
- **Utilizare comună**: 
  - Stilizare de bază pentru text
  - Resetare stiluri default ale browser-ului
  - Definirea stilurilor generale ale site-ului

### 1.3 Selector de Clasă (.)
```css
.button {
    background-color: blue;
    color: white;
    padding: 10px 20px;
}

.button-secondary {
    background-color: gray;
}
```
- Începe cu punct (.)
- Poate fi aplicat mai multor elemente
- Același element poate avea mai multe clase
- **Exemplu HTML**:
```html
<button class="button">Buton Primary</button>
<button class="button button-secondary">Buton Secondary</button>
```
- **Utilizare comună**:
  - Stiluri reutilizabile
  - Componente UI (butoane, carduri, etc.)
  - Modificatori de stil

### 1.4 Selector de ID (#)
```css
#header {
    position: fixed;
    top: 0;
    width: 100%;
}

#main-logo {
    width: 150px;
}
```
- Începe cu diez (#)
- Trebuie să fie UNIC pe pagină
- Are specificitate mai mare decât clasele
- **Exemplu HTML**:
```html
<header id="header">
    <img id="main-logo" src="logo.png" alt="Logo">
</header>
```
- **Utilizare comună**:
  - Elemente unice în pagină (header, footer)
  - Ancore pentru navigare
  - JavaScript targeting

## 2. Selectori Combinați

### 2.1 Selector Descendent (spațiu)
```css
.container p {
    margin-bottom: 15px;
}

nav ul li {
    display: inline-block;
}
```
- Selectează elementele care sunt ÎN INTERIORUL altui element
- Nu contează cât de adânc sunt nested
- **Exemplu HTML**:
```html
<div class="container">
    <div>
        <p>Acest paragraf va fi afectat</p>
    </div>
    <p>Și acest paragraf la fel</p>
</div>
<p>Acest paragraf NU va fi afectat</p>
```

### 2.2 Selector de Copil Direct (>)
```css
.container > p {
    font-weight: bold;
}
```
- Selectează DOAR copiii direcți
- Nu afectează elementele nested mai adânc
- **Exemplu HTML**:
```html
<div class="container">
    <p>Acest paragraf VA FI afectat</p>
    <div>
        <p>Acest paragraf NU va fi afectat</p>
    </div>
</div>
```

### 2.3 Selector de Frate Adiacent (+)
```css
h2 + p {
    font-size: 18px;
}
```
- Selectează elementul care vine IMEDIAT după
- Trebuie să fie la același nivel
- **Exemplu HTML**:
```html
<h2>Titlu</h2>
<p>Acest paragraf VA FI afectat</p>
<p>Acest paragraf NU va fi afectat</p>
```

### 2.4 Selector de Frați Generali (~)
```css
h2 ~ p {
    color: gray;
}
```
- Selectează TOATE elementele care urmează
- Trebuie să fie la același nivel
- **Exemplu HTML**:
```html
<h2>Titlu</h2>
<p>Acest paragraf va fi gri</p>
<div>Alt conținut</div>
<p>Și acest paragraf va fi gri</p>
```

## 3. Selectori de Atribute

### 3.1 Selector de Atribut Basic
```css
[disabled] {
    opacity: 0.5;
}

[type="text"] {
    padding: 5px;
}
```
- Selectează elemente bazat pe existența sau valoarea unui atribut
- **Exemplu HTML**:
```html
<button disabled>Buton dezactivat</button>
<input type="text" placeholder="Scrie aici...">
```

### 3.2 Selectori de Atribut Avansați
```css
/* Începe cu... */
[class^="icon-"] {
    background-size: 20px;
}

/* Se termină cu... */
[href$=".pdf"] {
    color: red;
}

/* Conține... */
[class*="btn"] {
    cursor: pointer;
}
```

## 4. Pseudo-clase și Pseudo-elemente

### 4.1 Pseudo-clase Comune
```css
/* Hover state */
.button:hover {
    background-color: darkblue;
}

/* Focus state */
input:focus {
    border-color: blue;
}

/* First and last child */
li:first-child {
    border-top: none;
}

li:last-child {
    border-bottom: none;
}

/* Nth child */
tr:nth-child(even) {
    background-color: #f2f2f2;
}
```

### 4.2 Pseudo-elemente
```css
/* First letter */
p::first-letter {
    font-size: 200%;
    font-weight: bold;
}

/* First line */
p::first-line {
    color: blue;
}

/* Before and After */
.quote::before {
    content: """;
}

.quote::after {
    content: """;
}
```

## Exerciții Practice

### 1. Exercițiu Basic: Stilizare Text
```html
<div class="content">
    <h1>Titlu Principal</h1>
    <p class="intro">Paragraf introductiv</p>
    <p>Paragraf normal</p>
    <p>Alt paragraf normal</p>
    <div class="important-box">
        <p>Paragraf important</p>
    </div>
</div>
```

Sarcini:
1. Fă toate paragrafele gri (`color: #666`)
2. Fă paragraful introductiv mai mare și bold
3. Fă paragrafele din `important-box` roșii
4. Adaugă o linie sub titlu
5. Fă primul paragraf după titlu italic

### 2. Exercițiu Intermediar: Navigation Menu
```html
<nav class="main-nav">
    <ul>
        <li><a href="#home">Acasă</a></li>
        <li><a href="#about" class="active">Despre</a></li>
        <li><a href="#services">Servicii</a></li>
        <li><a href="#contact">Contact</a></li>
    </ul>
</nav>
```

Sarcini:
1. Elimină bullet points din listă
2. Stilizează link-urile să nu fie subliniate
3. Adaugă hover effect pe link-uri
4. Fă link-ul activ să aibă altă culoare
5. Adaugă o linie sub link-ul peste care trecem cu mouse-ul

### 3. Exercițiu Advanced: Card Component
```html
<div class="card">
    <div class="card-header">
        <h3>Titlu Card</h3>
        <span class="badge">Nou</span>
    </div>
    <div class="card-body">
        <p>Conținut card...</p>
        <button class="btn" disabled>Buton Dezactivat</button>
        <button class="btn btn-primary">Buton Activ</button>
    </div>
    <div class="card-footer">
        <a href="#" class="link">Mai mult</a>
    </div>
</div>
```

Sarcini:
1. Stilizează cardul cu umbră și colțuri rotunjite
2. Adaugă spațiere internă diferită pentru header, body și footer
3. Fă badge-ul să apară în colțul din dreapta sus
4. Stilizează butoanele diferit în funcție de stare (normal/disabled)
5. Adaugă efecte de hover pe butonul activ și link

### 4. Exercițiu Expert: Form Styling
```html
<form class="contact-form">
    <div class="form-group">
        <label for="name">Nume:</label>
        <input type="text" id="name" required>
    </div>
    <div class="form-group">
        <label for="email">Email:</label>
        <input type="email" id="email" required>
    </div>
    <div class="form-group">
        <label for="message">Mesaj:</label>
        <textarea id="message"></textarea>
    </div>
    <div class="form-actions">
        <button type="reset" class="btn-secondary">Reset</button>
        <button type="submit" class="btn-primary">Trimite</button>
    </div>
</form>
```

Sarcini:
1. Stilizează inputurile cu focus state distinct
2. Adaugă stiluri pentru starea de validare (valid/invalid)
3. Creează un layout responsive pentru form
4. Adaugă iconițe în inputuri folosind pseudo-elemente
5. Creează animații pentru hover și focus states

## Sfaturi și Trucuri

### 1. Specificitate
- ID > Class > Element
- Mai mulți selectori = specificitate mai mare
- !important suprascrie tot (folosește cu grijă!)

### 2. Best Practices
- Evită selectori prea specifici
- Folosește clase pentru reutilizare
- Grupează selectori similari
- Menține un sistem de denumire consistent

### 3. Debugging
- Folosește DevTools să vezi ce selectori se aplică
- Verifică specificitatea când stilurile nu se aplică
- Testează pe diferite browsere

## Exerciții de Verificare
La finalul acestei secțiuni, ar trebui să poți:
1. Selecta orice element de pe pagină
2. Înțelege și folosi specificitatea
3. Crea selectori eficienți și reutilizabili
4. Debug-ui probleme comune de CSS
