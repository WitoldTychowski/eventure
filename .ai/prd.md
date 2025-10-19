# Dokument wymagań produktu (PRD) - Eventure

## 1. Przegląd produktu  
Eventure to aplikacja webowa mobile-first (desktop, tablet, mobile) umożliwiająca mieszkańcom szybkie odkrywanie lokalnych i darmowych wydarzeń w ich mieście. Użytkownik przegląda listę i mapę eventów, filtruje je wg typu i ceny oraz zagląda w szczegóły każdego wydarzenia.

## 2. Problem użytkownika  
Mieszkańcy nie wiedzą, jakie darmowe lub lokalne wydarzenia odbywają się w ich okolicy w dowolnym dniu tygodnia i tracą czas na wyszukiwanie informacji w rozproszonych źródłach.

## 3. Wymagania funkcjonalne  
- Lista wydarzeń z paginacją 20 pozycji + infinite scroll  
- Widok mapy z punktami wydarzeń (latitude, longitude, dokładny adres)  
- Filtry MVP: typ wydarzenia (kultura, sport, edukacja, rozrywka) oraz cena (darmowe vs płatne)  
- Szczegóły wydarzenia: id, nazwa, opis (HTML + zdjęcia), adres, współrzędne, link do źródła  
- Geolokalizacja automatyczna z fallbackiem: pole wpisania lokalizacji lub wybór miasta  
- Obsługa błędów:  
  - empty state z sugestiami zmiany filtrów  
  - uniwersalny banner błędu API z przyciskiem odśwież  
- Analizy: zdarzenie „wejście na stronę szczegółów” jako główny KPI  
- Responsywność: mobilka ≤767 px, tablet 768–1023 px, desktop ≥1024 px  
- Frontend implementuje proxy/API routes (Astro serverless) do Eventbrite i miejskich open data

## 4. Granice produktu  
- Out of scope w MVP: rezerwacje/bilety, konta użytkowników, powiadomienia push  
- Ograniczenie API: maks. 20 eventów na request, kolejne po infinite scroll  
- Brak mechanizmów płatności, rejestracji czy logowania

## 5. Historyjki użytkowników  

- ID: US-001  
  Tytuł: Automatyczne ustalenie lokalizacji użytkownika  
  Opis: Jako użytkownik chcę zezwolić na geolokalizację, aby zobaczyć listę i mapę wydarzeń w mojej okolicy.  
  Kryteria akceptacji:  
    • Po udzieleniu zgody system odczytuje współrzędne i pokazuje eventy w promieniu miasta.  
    • Lista i mapa odświeżają się automatycznie.

- ID: US-002  
  Tytuł: Ręczne wpisanie lub wybór lokalizacji  
  Opis: Jako użytkownik chcę wpisać adres lub wybrać miasto z listy, gdy geolokalizacja jest zablokowana.  
  Kryteria akceptacji:  
    • UI pokazuje pole tekstowe oraz listę miast.  
    • Po wprowadzeniu lokalizacji lista i mapa odświeżają się zgodnie z wyborem.

- ID: US-003  
  Tytuł: Filtrowanie wydarzeń wg typu i ceny  
  Opis: Jako użytkownik chcę filtrować listę wydarzeń po typie (kultura, sport, edukacja, rozrywka) i cenie (darmowe vs płatne).  
  Kryteria akceptacji:  
    • Interfejs umożliwia wybór typu i przełącznik darmowe/wszystkie.  
    • Lista aktualizuje się natychmiast po zmianie filtrów.

- ID: US-004  
  Tytuł: Infinite scroll w liście eventów  
  Opis: Jako użytkownik chcę przewijać listę i ładować kolejne 20 wydarzeń, aby nie musieć ręcznie paginować.  
  Kryteria akceptacji:  
    • Przy dojściu do końca listy pojawia się spinner ładowania.  
    • Po pobraniu kolejnych eventów spinner znika i nowe pozycje są dopisane.  
    • Po wyczerpaniu wyników wyświetla się komunikat „brak więcej wyników”.

- ID: US-005  
  Tytuł: Wejście na stronę szczegółów wydarzenia  
  Opis: Jako użytkownik chcę kliknąć wydarzenie, żeby zobaczyć jego pełne dane (opis HTML, zdjęcia, adres, link źródłowy).  
  Kryteria akceptacji:  
    • Kliknięcie karty otwiera widok szczegółów.  
    • Wszystkie wymagane pola (opis, zdjęcie, adres, GPS) są widoczne.

- ID: US-006  
  Tytuł: Wyświetlenie empty state przy braku wyników  
  Opis: Jako użytkownik chcę zobaczyć przyjazny komunikat i sugestie zmiany filtrów, gdy nie ma pasujących wydarzeń.  
  Kryteria akceptacji:  
    • UI pokazuje grafikę/tekst „Brak wydarzeń” i przyciski do resetu filtrów.  
    • Daje wskazówki, jak rozbudować wyszukiwanie.

- ID: US-007  
  Tytuł: Obsługa błędu API  
  Opis: Jako użytkownik chcę zobaczyć banner błędu i przycisk odświeżenia, jeśli pobieranie danych nie powiedzie się.  
  Kryteria akceptacji:  
    • W razie błędu HTTP lub timeoutu wyświetla się banner z komunikatem.  
    • Kliknięcie „Odśwież” ponawia próbę pobrania wydarzeń.

## 6. Metryki sukcesu  
- Czas od wejścia na listę do kliknięcia w szczegóły < 30 s  
- Liczba odsłon strony szczegółów (wejść) jako główny KPI  
- Wskaźnik błędów API i pustych list < 5%  
- Czas ładowania pierwszych 20 eventów ≤ 2 s  