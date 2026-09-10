# Gestione-Cantieri-Edili

https://doci-git.github.io/Gestione-Cantieri-Edili/

## Sincronizzazione tra dispositivi

L'app supporta Firebase Cloud Firestore. Senza configurazione Firebase continua a funzionare con il salvataggio locale del browser.

1. Crea un progetto su [Firebase Console](https://console.firebase.google.com/).
2. Aggiungi un'app Web e copia l'oggetto `firebaseConfig` fornito da Firebase.
3. Apri `index.html` e sostituisci i valori `INSERISCI_...` nella costante `FIREBASE_CONFIG`.
4. In Firebase apri **Firestore Database**, crea il database e scegli la regione.
5. Per una prima prova, nelle regole Firestore usa temporaneamente:

```text
rules_version = '2';
service cloud.firestore {
	match /databases/{database}/documents {
		match /gestione-cantieri/{document} {
			allow read, write: if true;
		}
	}
}
```

La pagina salva i dati nel documento `gestione-cantieri/dati-condivisi` e aggiorna automaticamente tutti i dispositivi che hanno aperto il link. Le regole `allow read, write: if true` sono adatte solo per una prova: per pubblicare l'app è necessario aggiungere Firebase Authentication e regole basate sull'utente autorizzato.
