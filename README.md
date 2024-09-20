### **Passo 1: Inizializzare il repository**

**Crea una nuova cartella e inizializza un repository Git:**

```
mkdir progetto-git
cd progetto-git
git init
```

**Crea un file di testo (`appunti.txt`) e aggiungi del contenuto:**

```
echo "Questi sono gli appunti iniziali." > appunti.txt
```

**Aggiungi e fai il commit del file:**

```
git add appunti.txt
git commit -m "Aggiunti appunti iniziali"
```

### **Passo 2: Creare un branch e modificare il file**

**Crea un nuovo branch chiamato `nuovi-appunti`:**

```
git branch nuovi-appunti
```

**Spostati nel nuovo branch:**

```
git checkout nuovi-appunti
```

**Modifica il file `appunti.txt` nel branch `nuovi-appunti`:**

```
echo "Questi sono i nuovi appunti dal branch 'nuovi-appunti'." >> appunti.txt
```

**Aggiungi e fai il commit della modifica:**

```
git add appunti.txt
git commit -m "Aggiunti nuovi appunti nel branch 'nuovi-appunti'"
```

### **Passo 3: Tornare al branch principale e unire i cambiamenti**

**Spostati di nuovo nel branch principale (`main`):**

```
git checkout main
```

**Unisci il branch `nuovi-appunti` nel branch principale (`main`):**

```
git merge nuovi-appunti
```

**Verifica che il merge sia avvenuto correttamente visualizzando il contenuto del file:**

```
cat appunti.txt
```

Dovresti vedere il file con entrambe le versioni:

```
Questi sono gli appunti iniziali.
Questi sono i nuovi appunti dal branch 'nuovi-appunti'.
```

### **Passo 4: Creare un conflitto e risolverlo**

**Crea un'altra modifica sul branch principale (`main`):**

```
echo "Appunti modificati nel branch principale." >> appunti.txt
git add appunti.txt
git commit -m "Modificati appunti nel branch principale"
```

**Torna al branch `nuovi-appunti` e modifica lo stesso file:**

```
git checkout nuovi-appunti
echo "Altre modifiche nel branch 'nuovi-appunti'." >> appunti.txt
git add appunti.txt
git commit -m "Altre modifiche nel branch 'nuovi-appunti'"
```

**Torna nel branch principale e prova a unire nuovamente:**

```
git checkout main
git merge nuovi-appunti
```

**Verifica lo stato per vedere il conflitto:**

```
git status
```

Git ti dirà che ci sono conflitti nel file `appunti.txt`. Apri il file per vedere i conflitti:

```
<<<<<<< HEAD
Questi sono gli appunti iniziali.
Appunti modificati nel branch principale.
=======
Questi sono i nuovi appunti dal branch 'nuovi-appunti'.
Altre modifiche nel branch 'nuovi-appunti'.
>>>>>>> nuovi-appunti
```

**Risolvere il conflitto:** Modifica il file in modo che rifletta il risultato desiderato. Per esempio:

```
Questi sono gli appunti iniziali.
Appunti modificati nel branch principale.
Questi sono i nuovi appunti dal branch 'nuovi-appunti'.
Altre modifiche nel branch 'nuovi-appunti'.
```

**Aggiungi il file risolto e completa il merge:**

```
git add appunti.txt
git commit -m "Risolto conflitto tra 'main' e 'nuovi-appunti'"
```

### **Passo 5: Pulizia dei branch**

**Eliminare il branch `nuovi-appunti` una volta completato il merge:**

```
git branch -d nuovi-appunti
```