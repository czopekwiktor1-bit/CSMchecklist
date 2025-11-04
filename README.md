# CSM Checklist - Kierunek Pielęgniarstwo

Aplikacja webowa (PWA) umożliwiająca wykładowcom wypełnianie checklisty potrzebnych materiałów i rzeczy na zajęcia dla studentów pielęgniarstwa. Po wypełnieniu checklisty administrator otrzymuje email z listą potrzebnych materiałów.

## 🚀 Funkcjonalności

- ✅ Formularz checklisty dla wykładowców
- ✅ Dynamiczne dodawanie/usuwanie elementów listy
- ✅ Walidacja formularza
- ✅ Automatyczne wysyłanie emaili do administratora
- ✅ Przechowywanie danych w bazie SQLite
- ✅ Nowoczesny, responsywny interfejs użytkownika
- ✅ **PWA (Progressive Web App) - instalacja na telefonie**
- ✅ **Działa offline (service worker)**
- ✅ **Optimized dla urządzeń mobilnych**

## 📋 Wymagania

- Node.js (v14 lub wyższa)
- npm lub yarn
- Konto email z dostępem SMTP (np. Gmail)

## 🔧 Instalacja

1. **Sklonuj repozytorium lub pobierz pliki**

2. **Zainstaluj zależności:**
```bash
npm run install:all
```

3. **Skonfiguruj email (wymagane):**

   Skopiuj plik `server/env.example` do `server/.env`:

**W PowerShell:**
```powershell
cd server
Copy-Item env.example .env
```

**Lub w Command Prompt:**
```cmd
cd server
copy env.example .env
```

Następnie edytuj `server/.env` i uzupełnij:
- `SMTP_USER` - Twój adres email
- `SMTP_PASS` - Hasło aplikacji (dla Gmail: hasło aplikacji, nie zwykłe hasło)
- `ADMIN_EMAIL` - Email, na który będą przychodzić powiadomienia

**Dla Gmail:**
- Musisz wygenerować hasło aplikacji: https://myaccount.google.com/apppasswords
- Użyj tego hasła jako `SMTP_PASS`

4. **Uruchom aplikację:**

```bash
npm run start:all
```

Lub osobno:
```bash
# Terminal 1 - Backend
npm run server

# Terminal 2 - Frontend
npm run client
```

Aplikacja będzie dostępna pod adresem:
- Frontend: http://localhost:3000
- Backend API: http://localhost:5000

## 📁 Struktura projektu

```
checklista-wykladowcow/
├── server/                 # Backend (Express.js)
│   ├── index.js           # Główny plik serwera
│   ├── routes/            # Routing
│   │   └── checklist.js   # Endpointy checklisty
│   ├── services/          # Serwisy
│   │   └── emailService.js # Wysyłanie emaili
│   ├── database.sqlite    # Baza danych (tworzona automatycznie)
│   └── .env               # Konfiguracja (do utworzenia)
├── client/                # Frontend (React)
│   ├── src/
│   │   ├── App.js         # Główny komponent
│   │   ├── components/    # Komponenty React
│   │   └── ...
│   └── public/
└── package.json           # Główny plik konfiguracyjny
```

## 🎯 Użycie

1. Otwórz aplikację w przeglądarce (http://localhost:3000)
2. Wypełnij formularz:
   - Imię i nazwisko wykładowcy
   - Email wykładowcy
   - Nazwa przedmiotu
   - Data potrzebna
   - Dodaj elementy checklisty (materiały/rzeczy)
   - Opcjonalnie: dodatkowe uwagi
3. Kliknij "Wyślij checklistę"
4. Administrator otrzyma email z listą potrzebnych materiałów

## 🔌 API Endpoints

- `POST /api/checklist/create` - Tworzenie nowej checklisty
- `GET /api/checklist/all` - Pobieranie wszystkich checklist
- `GET /api/checklist/:id` - Pobieranie checklisty po ID
- `GET /api/health` - Sprawdzenie statusu serwera

## 📧 Konfiguracja Email

Aplikacja używa Nodemailer do wysyłania emaili. Obsługiwane są różne dostawcy SMTP:

- Gmail
- Outlook
- Inne serwery SMTP

Przykładowa konfiguracja dla różnych dostawców:

**Gmail:**
```
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
```

**Outlook:**
```
SMTP_HOST=smtp-mail.outlook.com
SMTP_PORT=587
```

## 🛠️ Rozwój

### Dodatkowe funkcjonalności, które można dodać:

- Panel administracyjny do przeglądania checklist
- Status checklist (pending, completed, etc.)
- Export checklist do PDF/Excel
- Powiadomienia email dla wykładowcy (potwierdzenie)
- Kalendarz z terminami
- Historia zmian

## 📝 Licencja

ISC

## 📱 Instalacja na telefonie (PWA)

Aplikacja może być zainstalowana jako aplikacja mobilna:

### Android:
1. Otwórz aplikację w Chrome
2. Kliknij menu → "Dodaj do ekranu głównego"
3. Aplikacja pojawi się jako ikona

### iOS:
1. Otwórz aplikację w Safari
2. Kliknij przycisk "Udostępnij" → "Dodaj do ekranu głównego"

### Generowanie ikon PWA:

**Metoda 1 - HTML Generator:**
Otwórz `client/public/create-icons.html` w przeglądarce - ikony zostaną automatycznie pobrane.

**Metoda 2 - Ręczne:**
Utwórz ikony o rozmiarach 192x192 i 512x512 px i zapisz jako:
- `client/public/icon-192.png`
- `client/public/icon-512.png`

## 🌐 Wdrożenie (hosting online)

Zobacz szczegółową instrukcję w pliku [DEPLOY.md](DEPLOY.md)

**Najszybsze opcje:**
- **Vercel** - darmowe, łatwe wdrożenie frontend
- **Render.com** - darmowe dla frontend i backend
- **Netlify** - darmowe dla frontend

## 👤 Autor

Stworzono dla kierunku pielęgniarstwa

