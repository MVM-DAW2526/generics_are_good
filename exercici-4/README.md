## Exercici 4: Saber preveure l'Over-engineering (Quan NO fer ús de Generics)

**Context:** A *One Punch Man*, tothom adora tècniques sobrehumanes però a vegades no fa falta usar el famós cop "Sèrie Seriosa Dimensional" per matar el monstre més estúpid del carreró; ambdós casos acaben amb la mort directa, i amb un sol dit es fa més ràpid.
A la feina, passa al 90% dels enginyers quan acaben d'aprendre Generics: les fan servir ABSOLUTAMENT A TOT ARREU i compliquen innecessàriament un mètode perfectament senzill.

**Objectiu de resolució:**
Llegeix l'horrible patró a sota d'aquesta funció. Rep la funció... i **treu el Generic directament d'una escombrada**. Demostra que a TS se li dóna bé no ofuscar-se per res.

```ts
// 🚩 RED FLAG: Veure això al codi productiu et fa desconfiar perillosament! 
// Això és conegut com a "Generic Identity Anti-Pattern".
function logCharacterName<T extends { name: string }>(character: T): void {
  console.log("Benvingut/da al gremi, " + character.name);
}

logCharacterName({ name: "Genos", cyborgParts: 14 });
```

*Com ho destil·les? Pista: A tu t'interessa absolutament retenir el model sencer `T` per saber si aquest és humà, ciborg o heroi per recuperar-ho a l'exterior? En conseqüència no, perquè només assoleixes extreure el string (`.name`) per fer un log simple que al retornar fa ús de `void`. Canvia l'entrada exclusivament a un objecte simple `(character: { name: string })` i elimina'n la `T`.*
