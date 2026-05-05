## Exercici 5: Els trucs magistrals de nivell (Utility Types integrats)

**Context:** Acabant els fons d'aprenentatge del Món, no cal redibuixar manualment un univers o interfície completament des del centre de dades: *My Hero Academia* demostra fets de passar poder de forma segmentada. `One For All` passa les cendres de molts factors trossejats al successor sense transferir vides senceres inicials amb la capacitat requerida.
A l'equipatge intern, el nucli del TypeScript ja porta incloses per tu diverses macros genèriques pròpies.

Una d'absolutament important en APIs d'actualització és el tipus prefabricat `Partial<T>`. Consisteix a donar qualsevol classe de base a aquest, ell en llegeix l'estat i et subministra de bracet al resultat la mateixa Interface, però assignant a tot el contingut de dins el caràcter tancat 'opcional'.

**Objectiu Magistral:** Fixa aquest clímax eliminant els ponts duplicats o secundaris d'aquest codi reduint-lo al factor original gràcies a l'utilitària `Partial<T>`.

**Codi a estilitzar:**
```ts
interface HeroAccount {
  id: number;
  alias: string;
  level: number;
  isRegistered: boolean;
}

// ⚠️ Per què declarar de nou un model sencer on només hi ha la variant que és "?", si ja ve heretat?
interface HeroAccountUpdate {
  alias?: string;
  level?: number;
  isRegistered?: boolean;
}

// ⬇️ REESCRIVIU AQUEST PARÀMETRE 'updates'⬇️
// Elimineu completament la declaració d''HeroAccountUpdate' fent servir sobre el camp la crida genèrica 'Partial' connectada sobre el HeroAccount com a T.
function updateHero(id: number, updates: HeroAccountUpdate) {
  // Aquí aniria el mecanisme de canvi cap a dades remotes...
}

// D'aquesta manera això funcionarà perfectament perquè nomes passarem un sol bloc reduït!
updateHero(7, { level: 99 });
```

*Amb aquesta preparació final al vostre manual d'armes, teniu el destí de les futures aplicacions modernes directament domades per la vostra fluïdesa de teclat. Sort i programació renyida!*
