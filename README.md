# VDJ Sync

Aplikacja na macOS do przenoszenia biblioteki VirtualDJ między dwoma Macami przez pendrive lub dysk zewnętrzny.

**MacBook A → dysk zewnętrzny → MacBook B**

[Pobierz najnowszą wersję](https://github.com/mateuszbierkat/vdj-sync/releases/latest)

## Co robi program?

- Pozwala wybrać dysk zewnętrzny oraz jeden główny folder muzyki.
- Synchronizuje muzykę, bazę VirtualDJ, playlisty i ustawienia.
- Odtwarza położenie folderu na koncie Maca B i dopasowuje odwołania VirtualDJ przy różnych nazwach kont.
- Przenosi mapowania kontrolerów i klawiatury oraz definicje urządzeń i pady.
- Pokazuje podgląd zmian przed synchronizacją, postęp operacji i wynik weryfikacji.
- Po zakończeniu podaje liczbę nowych, zmienionych i przeniesionych do Kosza plików.
- Przenosi nadmiarowe pliki celu do systemowego Kosza.
- Pobiera i instaluje aktualizacje z poziomu aplikacji, bez tokenu GitHub.

Synchronizacja jest jednokierunkowa. MacBook A jest źródłem, a MacBook B otrzymuje jego stan. Zmiany wykonane wyłącznie na B nie są przenoszone na A. Pendrive służy do kolejnych aktualizacji tej samej kopii — nie trzeba go czyścić przed każdym użyciem.

## Pobieranie i instalacja

1. Otwórz [najnowsze wydanie](https://github.com/mateuszbierkat/vdj-sync/releases/latest).
2. W sekcji **Assets** pobierz plik `VDJ-Sync-macOS-<wersja>.zip`.
3. Rozpakuj ZIP i otwórz folder `VDJ-Sync`.
4. Przenieś **VDJ Sync.app** do folderu **Aplikacje** i uruchom.
5. Powtórz instalację na drugim Macu.

Paczka zawiera aplikację dla procesorów **Apple Silicon i Intel**. Do pobrania i aktualizacji nie jest potrzebne konto GitHub. Pozycje „Source code” w wydaniu są archiwum plików repozytorium, a instalator aplikacji znajduje się w paczce wskazanej powyżej.

Do automatycznej instalacji aktualizacji potrzebny jest zapis w folderze aplikacji. Jeśli folder systemowy jest niezapisywalny, umieść aplikację w folderze `~/Applications` swojego użytkownika.

## Wybór folderu muzyki — od wersji 1.5.0

Na MacBooku A wskaż dysk przyciskiem **Wybierz…** oraz główny folder muzyki przyciskiem **Wybierz folder…**.

Wybierz osobny folder wewnątrz swojego katalogu użytkownika, np. **Muzyka/Biblioteka DJ**. Nie wybieraj całego katalogu użytkownika ani całego systemowego folderu Muzyka, Dokumenty lub Pobrane. W tym wydaniu foldery poza katalogiem użytkownika i dowiązania symboliczne nie są obsługiwane.

Po eksporcie dysk przechowuje lokalizację biblioteki. MacBook B odczytuje ją automatycznie: folder **Muzyka/Biblioteka DJ** na A trafi do **Muzyka/Biblioteka DJ** na koncie użytkownika B. Konta mogą mieć różne nazwy. Program dopasowuje odwołania w bazie, playlistach i tekstowych ustawieniach VirtualDJ, a sam eksport pozostaje w postaci źródłowej.

Na B wybierz dysk i sprawdź wyświetlony **Folder muzyki na tym Macu**. Jeśli eksport został wykonany po otwarciu programu, kliknij **Odczytaj dysk**.

Kopiowane są pliki wewnątrz wybranego folderu. Utwory znajdujące się poza nim nie zostaną przeniesione. Zmiana głównego folderu na inną lokalizację nie usuwa automatycznie poprzedniego folderu muzyki na B.

**Przed kolejnym eksportem zaktualizuj oba Maci do 1.5.0.** Starsze wersje nie obsługują nowego formatu eksportu. Dotychczasowego dysku nie trzeba ponownie przypisywać. Niezmieniona muzyka na nim pozostaje i nie jest przesyłana od początku.

## Pierwsza konfiguracja dysku

1. Zamknij VirtualDJ przez **⌘Q**.
2. Podłącz dysk zewnętrzny do MacBooka A.
3. W VDJ Sync wybierz **MacBook A**, wskaż dysk i główny folder muzyki.
4. Użyj **Przypisz nowy dysk…** tylko przy pierwszej konfiguracji nowego dysku.
5. Wykonaj **Podgląd zmian**, sprawdź listę, a następnie wybierz **Synchronizuj**.

Dysk zostaje przypisany do komputera źródłowego. Ten sam dysk wykorzystuje się przy kolejnych synchronizacjach.

## Kolejne synchronizacje

### Na MacBooku A

1. Zamknij VirtualDJ przez **⌘Q** i podłącz przypisany dysk.
2. Wybierz **MacBook A** i sprawdź wybrany folder muzyki.
3. Kliknij **Podgląd zmian**, a po sprawdzeniu listy **Synchronizuj**.
4. Poczekaj na komunikat o gotowym eksporcie i wysuń dysk.

### Na MacBooku B

1. Zamknij VirtualDJ przez **⌘Q** i podłącz dysk z gotowym eksportem.
2. Wybierz **MacBook B**, wskaż dysk i sprawdź automatycznie odczytany folder docelowy.
3. Kliknij **Podgląd zmian**, a następnie **Synchronizuj**.
4. Po komunikacie o gotowym imporcie możesz uruchomić VirtualDJ.

Nie trzeba ręcznie tworzyć i przywracać backupu VirtualDJ. Program synchronizuje bezpośrednio zarządzane pliki profilu, w tym `database.xml`, `settings.xml`, listy i mapowania.

## Dziennik i aktualizacje

Dziennik podąża za nowymi wpisami. Po ręcznym przewinięciu w górę śledzenie zatrzymuje się. Przycisk ze strzałką w dół wraca do najnowszych wpisów i wznawia śledzenie.

Aby wyszukać nowe wydanie, wybierz **Aktualizacje → Sprawdź teraz**. Gdy aktualizacja jest dostępna, wybierz **Aktualizuj**. Aplikacja pobiera paczkę, sprawdza jej integralność, instaluje ją i uruchamia się ponownie.

## Zasady przechowywania danych

Usunięte ze źródła pliki są przy synchronizacji przenoszone z celu do systemowego Kosza. Program nie tworzy folderów „old” ani archiwum kolejnych stanów. Poprzednie wersje nadpisywanych plików nie są zachowywane. Synchronizacja nie zastępuje niezależnej kopii zapasowej komputera źródłowego.
