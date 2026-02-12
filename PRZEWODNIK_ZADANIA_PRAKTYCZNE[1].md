# PRAKTYCZNE ZADANIA NA ROZMOWĘ KWALIFIKACYJNĄ - BELIANI
## Przewodnik z rozwiązaniami i wyjaśnieniami

---

## ZADANIE 1: Podstawowy Newsletter HTML
**Poziom trudności:** ⭐⭐ (Podstawowy)
**Czas:** 20-30 minut

### 📋 Treść zadania:
"Stwórz prosty newsletter w HTML promujący nowy produkt - sofę. Newsletter powinien zawierać:
- Header z logo firmy
- Główny obrazek produktu
- Krótki opis produktu i cenę
- Przycisk CTA 'Zobacz produkt'
- 3 polecane produkty w jednym rzędzie
- Social media links
- Footer z danymi firmy

Wymagania:
- Użyj tabel HTML (nie div-ów)
- Inline CSS
- Szerokość: 600px
- Responsywny design nie jest wymagany"

### ✅ Kluczowe punkty do zapamiętania:

#### 1. **Struktura tabel dla emaili**
```html
<table width="600" cellpadding="0" cellspacing="0" border="0">
    <tr>
        <td>Zawartość</td>
    </tr>
</table>
```
**Dlaczego tabele?** Większość klientów email (zwłaszcza Outlook) nie wspiera nowoczesnego CSS, ale doskonale renderuje tabele.

#### 2. **Inline CSS**
```html
<td style="padding: 20px; background-color: #ffffff; color: #333333;">
```
**Dlaczego inline?** Niektóre klienty email usuwają sekcję `<style>` z head, więc bezpieczniej jest używać inline styles.

#### 3. **Przycisk jako tabela**
```html
<table cellpadding="0" cellspacing="0" border="0">
    <tr>
        <td style="background-color: #e74c3c; border-radius: 5px;">
            <a href="#" style="display: inline-block; padding: 16px 40px; color: #ffffff; text-decoration: none;">
                ZOBACZ PRODUKT
            </a>
        </td>
    </tr>
</table>
```
**Dlaczego nie `<button>`?** Buttony HTML są niespójnie renderowane w różnych klientach email.

#### 4. **Obrazki**
```html
<img src="url" alt="opis" width="600" style="width: 100%; max-width: 600px; height: auto; display: block;">
```
**Najlepsze praktyki:**
- Zawsze podawaj `width` i `height`
- Używaj `alt` text
- `display: block` usuwa niepotrzebne odstępy

---

## ZADANIE 2: Responsywny Newsletter z Media Queries
**Poziom trudności:** ⭐⭐⭐ (Średni)
**Czas:** 40-60 minut

### 📋 Treść zadania:
"Stwórz newsletter promocyjny 'Wyprzedaż Sezonowa', który będzie responsywny i dobrze wyglądać na urządzeniach mobilnych.

Wymagania:
- Newsletter musi być responsywny (mobile-first)
- Użyj media queries dla ekranów poniżej 600px
- 4 produkty w siatce 2x2 (desktop) → pionowo (mobile)
- Preheader text
- Banner promocyjny na górze
- Sekcja z opiniami klientów
- Ikony korzyści (darmowa dostawa, zwroty, bezpieczne płatności)"

### ✅ Kluczowe punkty:

#### 1. **Media Queries dla email**
```html
<style>
    @media only screen and (max-width: 600px) {
        .email-container {
            width: 100% !important;
        }
        
        .column {
            display: block !important;
            width: 100% !important;
        }
    }
</style>
```
**Uwaga:** Używamy `!important` żeby nadpisać inline styles.

#### 2. **Preheader**
```html
<div style="display: none; max-height: 0; overflow: hidden;">
    Tekst widoczny w podglądzie emaila, zanim użytkownik go otworzy
</div>
```

#### 3. **Responsywne kolumny**
```html
<!-- Desktop: 2 kolumny obok siebie -->
<td class="column" width="50%" style="padding: 10px;">
    Zawartość kolumny
</td>

<!-- Mobile: @media query zmienia na display: block, width: 100% -->
```

#### 4. **Ukrywanie elementów na mobile**
```html
<tr class="hide-mobile">
    <td>Ta sekcja nie będzie widoczna na mobile</td>
</tr>

<style>
@media only screen and (max-width: 600px) {
    .hide-mobile {
        display: none !important;
    }
}
</style>
```

---

## ZADANIE 3: Landing Page z Figma
**Poziom trudności:** ⭐⭐⭐⭐ (Zaawansowany)
**Czas:** 60-90 minut

### 📋 Treść zadania:
"Otrzymujesz projekt landing page w Figma. Twoim zadaniem jest przekształcić go na HTML/CSS.

Projekt zawiera:
- Navigation bar (sticky)
- Hero section z gradientem
- Sekcja Features (3 karty)
- Sekcja Products (grid produktów)
- Newsletter signup form
- Footer z 4 kolumnami

Wymagania:
- Semantyczny HTML5
- Nowoczesny CSS (flexbox/grid)
- Responsywny design
- Hover effects na elementach interaktywnych
- JavaScript dla smooth scroll i form validation"

### ✅ Kluczowe punkty:

#### 1. **Semantyczny HTML**
```html
<header>, <nav>, <main>, <section>, <article>, <footer>
```
Używaj odpowiednich tagów zamiast wszędzie `<div>`.

#### 2. **CSS Grid dla layoutu**
```css
.products-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 30px;
}
```
**Wyjaśnienie:**
- `repeat(auto-fit, ...)` - automatycznie dopasowuje ilość kolumn
- `minmax(280px, 1fr)` - minimum 280px, maksimum równo podzielona przestrzeń

#### 3. **Sticky Navigation**
```css
.header {
    position: sticky;
    top: 0;
    z-index: 1000;
}
```

#### 4. **Gradient Background**
```css
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
```

#### 5. **Hover Effects**
```css
.product-card:hover {
    transform: translateY(-3px);
    box-shadow: 0 5px 20px rgba(0,0,0,0.1);
}
```

#### 6. **JavaScript - Smooth Scroll**
```javascript
document.querySelectorAll('a[href^="#"]').forEach(anchor => {
    anchor.addEventListener('click', function (e) {
        e.preventDefault();
        const target = document.querySelector(this.getAttribute('href'));
        target.scrollIntoView({ behavior: 'smooth' });
    });
});
```

---

## DODATKOWE ZADANIE (możliwe): Debug istniejącego kodu

### 📋 Treść zadania:
"Ten newsletter ma kilka błędów. Znajdź i popraw je:

```html
<table width="100%">
    <tr>
        <td style="padding 20px">
            <h1>Witaj!</h1>
            <img src="image.jpg">
            <a href="#">
                <button>Kliknij tutaj</button>
            </a>
        </td>
    </tr>
</table>
```

### ❌ Błędy do znalezienia:

1. **Brak `:` w padding**
```css
/* Źle */
style="padding 20px"

/* Dobrze */
style="padding: 20px"
```

2. **Brak atrybutów dla tabeli**
```html
/* Źle */
<table width="100%">

/* Dobrze */
<table width="100%" cellpadding="0" cellspacing="0" border="0">
```

3. **Brak `alt` dla obrazka**
```html
/* Źle */
<img src="image.jpg">

/* Dobrze */
<img src="image.jpg" alt="Opis obrazka" width="600" style="display: block;">
```

4. **Użycie `<button>` w emailu**
```html
/* Źle */
<a href="#"><button>Kliknij tutaj</button></a>

/* Dobrze */
<a href="#" style="display: inline-block; padding: 15px 30px; background-color: #e74c3c; color: #ffffff; text-decoration: none;">
    Kliknij tutaj
</a>
```

---

## NAJCZĘSTSZE PUŁAPKI I JAK ICH UNIKAĆ

### 1. **Email HTML vs Web HTML**
| Email HTML | Web HTML |
|------------|----------|
| Tabele do layoutu | Div + CSS Grid/Flexbox |
| Inline CSS | External CSS |
| Proste selektory | Dowolne selektory CSS |
| Ograniczone media queries | Pełne wsparcie responsive |

### 2. **Testowanie**
- **Litmus** lub **Email on Acid** - narzędzia do testowania emaili
- Testuj w: Gmail, Outlook, Apple Mail, Mobile
- Sprawdź w trybie ciemnym (dark mode)

### 3. **Dostępność**
```html
<!-- Zawsze używaj alt text -->
<img src="sofa.jpg" alt="Nowoczesna szara sofa modułowa" width="600">

<!-- Dobre kontrasty kolorów -->
style="color: #333333; background-color: #ffffff;"

<!-- Odpowiedni rozmiar fontu (min 14px dla treści) -->
style="font-size: 16px;"
```

---

## CO MÓWIĆ PODCZAS WYKONYWANIA ZADANIA

### ✅ DOBRZE:
1. "Zacznę od struktury tabel, ponieważ to standard dla newsletterów"
2. "Używam inline CSS dla maksymalnej kompatybilności"
3. "Testuję w różnych klientach email, żeby upewnić się, że działa wszędzie"
4. "Dodaję preheader dla lepszego user experience"
5. "Dbam o semantyczny HTML i dostępność"

### ❌ ŹLE:
1. Milczenie przez całe zadanie
2. "Nie wiem dlaczego używamy tabel, to staromodne"
3. "Zrobię to tylko dla Chrome, reszta się dostosuje"
4. Nie pytanie o wymagania lub wątpliwości

---

## JAK PODEJŚĆ DO ZADANIA PRAKTYCZNEGO

### KROK 1: Zrozumienie wymagań (2-3 min)
- Przeczytaj dokładnie polecenie
- Zadaj pytania jeśli coś jest niejasne:
  - "Czy newsletter ma być wysyłany do wszystkich 19 krajów?"
  - "Czy są jakieś specyficzne brand guidelines dotyczące kolorów?"
  - "Czy mam używać prawdziwych obrazków czy placeholdery?"

### KROK 2: Planowanie (3-5 min)
- Naszkicuj strukturę (nawet na kartce)
- Pomyśl o kolejności elementów
- Zaplanuj responsywność

### KROK 3: Implementacja (40-60 min)
- Zacznij od struktury (tabele/HTML)
- Dodaj style
- Przetestuj w przeglądarce
- Dopracuj detale

### KROK 4: Testowanie (5-10 min)
- Sprawdź na różnych rozdzielczościach
- Kliknij wszystkie linki
- Sprawdź czy wszystko jest czytelne

### KROK 5: Prezentacja (2-3 min)
- Pokaż rezultat
- Wyjaśnij kluczowe decyzje:
  - "Użyłem tabel zamiast divów ze względu na kompatybilność z Outlook"
  - "Dodałem media queries dla lepszego wyświetlania na mobile"
  - "Preheader zwiększy open rate emaila"

---

## CHECKLISTA PRZED ODDANIEM ZADANIA

- [ ] Wszystkie wymagane sekcje są obecne
- [ ] Kod jest czysty i sformatowany
- [ ] Inline CSS dla emaili
- [ ] Obrazki mają `alt` text
- [ ] Przyciski działają (nawet jeśli prowadzą do #)
- [ ] Responsywność działa poprawnie
- [ ] Brak błędów w konsoli
- [ ] Kod jest semantyczny
- [ ] Dostępność jest zachowana (kontrast, rozmiar fontów)

---

## NAJWAŻNIEJSZE - NIE PANIKUJ!

### Jeśli coś nie wiesz:
1. **Powiedz wprost:** "Nie jestem pewna tej składni, ale wiem gdzie to sprawdzić"
2. **Pokaż proces myślenia:** "Myślę, że najlepszym rozwiązaniem byłoby..."
3. **Poproś o podpowiedź:** "Czy mogę sprawdzić w dokumentacji?"

### Pamiętaj:
- Rekruterzy wiedzą, że jesteś Junior
- Liczy się sposób myślenia, nie perfekcja kodu
- Pytania są OK - pokazują, że myślisz
- Jeśli popełnisz błąd i sam go znajdziesz - to PLUS

---

## KOŃCOWE WSKAZÓWKI

### Co zrobić dzień przed rozmową:
1. Przejrzyj te 3 przykłady
2. Otwórz kod w przeglądarce i zobacz jak działa
3. Spróbuj zmienić kolory/tekst - poczuj kod
4. Przećwicz głośne tłumaczenie co robisz

### Co zabrać na rozmowę:
- Laptopa (jeśli prosili)
- Notatnik i długopis
- Pozytywne nastawienie! 😊

### Co powiedzieć na początku zadania:
"Czy mogę zadać kilka pytań o wymagania przed rozpoczęciem?"
"Powiem na głos co robię, żebyście wiedzieli jak myślę"

---

**POWODZENIA! WIERZĘ W CIEBIE! 🚀**

Pamiętaj - zaprosili Cię na rozmowę, więc już widzą w Tobie potencjał.
Teraz tylko pokaż swoją motywację i chęć nauki!
