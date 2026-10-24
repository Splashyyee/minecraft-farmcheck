# Minecraft Farm-Checkliste

## Funktionen
- Alle 70 Items deiner Liste
- Mengen mit `+1`, `+64`, `−1`, `−64` ändern oder per Checkbox als vollständig markieren
- Suche, Filter, Fortschrittsanzeige und gemeinsame Listen-Codes
- Supabase-Synchronisierung für Freunde ohne eigenes Konto

## Für gemeinsame Nutzung einrichten
1. Erstelle ein Projekt auf https://supabase.com/
2. Öffne **SQL Editor → New query**, füge `setup.sql` ein und führe es aus.
3. In Supabase unter **Project Settings → API** kopierst du die **Project URL** und den öffentlichen **anon/publishable key**. Niemals den `service_role`-Key verwenden.
4. Öffne `index.html` und füge direkt vor `const original=__ITEMS__;` (in der fertigen Datei steht dort die Item-Liste) diese Zeile ein. Ersetze die Platzhalter durch deine echten Werte:
   `window.SUPABASE_CONFIG = { url: 'DEINE_PROJECT_URL', key: 'DEIN_PUBLIC_ANON_KEY' };`
   Wichtig: Diese Zeile muss vor `const original=...` und vor `setup()` stehen.
5. Lade `index.html` in ein GitHub-Repository hoch. Unter **Settings → Pages** aktiviere die Veröffentlichung aus dem `main`-Branch, Ordner `/ (root)`.
6. Öffne die veröffentlichte Seite, gib einen gemeinsamen Code ein und klicke **Liste öffnen**. Schicke allen Freunden denselben Seitenlink mit `?room=DEIN-CODE`, z. B. `https://DEINNAME.github.io/REPO/?room=team-2026`.

## Sicherheit
Die SQL-Policies sind offen, damit alle ohne Anmeldung mitmachen können. Jeder, der Projekt-URL und öffentlichen Key kennt, kann Daten ändern. Der Listen-Code trennt Listen in der Oberfläche, ist aber keine echte Zugriffskontrolle. Nur für unkritische Minecraft-Projektlisten verwenden. Ohne Supabase-Konfiguration ist die Seite nur eine lokale Vorschau und Änderungen werden nicht mit Freunden synchronisiert.

Die Startmengen werden anhand deiner Spalte `Missing` als bereits erledigt = `Total - Missing` vorbelegt. `Available` wurde nicht zusätzlich verrechnet.
