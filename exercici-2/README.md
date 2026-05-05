## Exercici 2: L'Estat del Temps Temporal (Pràctica autònoma)

**Context:** A *Steins;Gate*, Okarin emmagatzema memòries d'una versió del món, i la recupera (llegeix i emmotlla variables d'Estat) freqüentment fins alterar la Línia de Temps. 
Els actuals programadors en *React* o interfícies dominals (DOM) basades en esdeveniments, creen `Hooks` molt pràctics tipus `useState` completament genèrics per poder iniciar blocs d'estat de memòria.

**El teu repte sobre el codi base:**
Modifica el mètode original de JavaScript a base de TypeScript en la funció per obtenir la llista `[ get, set ]`.

```ts
// ⚠️ Desafiament: Aquesta funció JS no té model de retorn i el tipus està amagat. Converteix-la en Funcionalitat Genèrica <T> !
function createMemory(initialValue) {
  let memory = initialValue;
  
  const getMemory = () => memory;
  const setMemory = (newValue) => {
    memory = newValue;
  };

  return [getMemory, setMemory];
}

// Hauria de permetre a l'escriptori deduir / forçar que:
// const timeline = createMemory<number>(1);
// const status = createMemory<string>("El Psy Kongroo");
// retornin tuples amb les funcions totalment assegurades en la seva natura.
```

**Objectiu:** 
Transformar la funció afegint els paràmetres T `<T>` al nom, a `initialValue`, `newValue` i el model de retorn general com a una tupla!
