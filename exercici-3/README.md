## Exercici 3: La Condició Irrevocable (Restriccions de Codi amb extends)

**Context:** Talment com a *Hunter x Hunter*, tu no pots recórrer als exèrcits lligats del teu Nen i executar conjurs espectaculars sense satisfer certes "condicions". 
Al món pur del desenvolupador, habitualment tens funcions de persistència i base de dades (ex. `updateEntity(...)`) que actualitzen "qualsevol unitat T" però que **com a requisit imperatiu necessiten que la entitat T de l'interior porti un camp ID innegociable** a fi de no carregar-se altres registres per error.

**Objectiu de resolució:**
Protegeix aquesta funció. Condiciona la T fent que "s'estengui" (hagi de ser obligatòriament capaç d'abastar) una interfície o clàusula on existeixi "id" (per exemple `string`).

**Codi Defectuós (Fix it!):**
```ts
// ⛔ TypeScript ens escridassa: "Property 'id' does not exist on type 'T'."
// Òbviament, li has dit que seria qualsevol T de lliure circulació. Posa-li restricció a dalt!
function updateDatabaseRecord<T>(record: T) {
  console.log("Updating record DB_ID: " + record.id);
}

// Després d'aplicar la restricció `extends`, el darrer crac de tipatge ha d'impedir la via "Gon":
updateDatabaseRecord({ name: "Gon" }); // No té id! ❌ Això MAI ha de compilar un cop purificat.

// Aquest de sota ha de poder ser compilat perfectament, ja que incorpora l'id.
updateDatabaseRecord({ id: "123xQ", name: "Killua Zoldyck" });
```

*Recordatori visual: Fixa una `interface HasId` o un objecte net interior `{id: string}` pel qual el T depengui aplicant `extends`.*
