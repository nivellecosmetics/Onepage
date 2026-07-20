# Debug Session: booking-submit-error
- **Status**: [OPEN]
- **Issue**: Beim Klick auf "Jetzt buchen" erscheint eine Fehlermeldung statt einer erfolgreichen Buchung.
- **Debug Server**: Not started yet
- **Log File**: .dbg/trae-debug-log-booking-submit-error.ndjson

## Reproduction Steps
1. Website lokal in der Vorschau oeffnen.
2. Name, E-Mail, Telefonnummer, Behandlung, Datum und Uhrzeit auswaehlen.
3. Auf "Jetzt buchen" klicken.
4. Fehlermeldung beobachten.

## Hypotheses & Verification
| ID | Hypothesis | Likelihood | Effort | Evidence |
|----|------------|------------|--------|----------|
| A | Supabase lehnt `select` oder `insert` fuer `bookings` ab | High | Low | Pending |
| B | EmailJS `sendForm()` schlaegt mit Konfigurations- oder Template-Fehler fehl | Medium | Low | Pending |
| C | Der Versand an `formsubmit.co` scheitert lokal durch Netzwerk/CORS oder Service-Fehler | Medium | Low | Pending |
| D | Ein Pflichtfeld wie `booking_date` oder `booking_time` ist beim Submit leer | Low | Low | Pending |

## Log Evidence
- Browser-Konsole: `SUCCESS! All systems go.`
- Browser-Konsole: `Gebuchte Termine geladen: [02.07.2026 13:30, 02.07.2026 12:00]`
- Netzwerkanfragen erfolgreich:
  - `POST https://api.emailjs.com/api/v1.0/email/send-form`
  - `POST https://formsubmit.co/ajax/nivellecosmetics@gmail.com`
  - `POST https://bcxxtbdjsnjowzrgfcpd.supabase.co/rest/v1/bookings?columns=%22booking_date_str%22`

## Verification Conclusion
- Aktuelle Reproduktion erfolgreich.
- Hypothese A: vorerst verworfen bei aktueller Reproduktion.
- Hypothese B: vorerst verworfen bei aktueller Reproduktion.
- Hypothese C: vorerst verworfen bei aktueller Reproduktion.
- Hypothese D: verworfen, da `selectedTime` und `bookingDate` vor dem Submit gesetzt waren.
