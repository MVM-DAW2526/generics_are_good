## Exercici 1: La Resposta del Sistema Universal (Guiat)

**Context:** A *Sword Art Online*, el Sistema Cardinal de la màquina et contesta constantment quan fas peticions: ja sigui per veure el perfil d'un jugador, extreure un inventari d'un monstre, o conèixer el mapa de la planta on et trobes. 
A la feina, les APIs (cridar informació d'un servidor web) funcionen igual. El backend retorna sempre un embolcall amb el `status` HTTP i un atribut `data` variable. Si has de crear una interfície (contracte) individual per cada resultat imaginable del servidor, repetiràs l'estructura base desenes de vegades a la teva App.

**Codi repetitiu (sense generics):**
```ts
interface PlayerResponse {
  statusCode: number;
  data: { username: string; level: number };
}

interface ItemResponse {
  statusCode: number;
  data: { itemName: string; durability: number };
}
```

### Resolució pas a pas

1. **Troba el patró:** Veiem que `statusCode` (i la pròpia estructura d'embolcall) es repeteix totalment igual i en sincronia. El que realment és mutant és el tipus inserit a `data`.
2. **Crea la "Caixa Base" (La Interfície Genèrica):**
3. **Aplica-ho magistralment:** Aïllarem els tipus de les dures dades i ens limitarem a unir parts. Així faràs que tot resulti hiper-elegant.

> [!TIP] EL CONSELL DE L'EXPERT
> Aquest és **el costum i model més comú** com a programador Full-Stack o Front-end: Mai no desxifraràs una API escrivint un únic model pel lliureament. Empreu les *Response Envelopes Generics* (`ApiResponse<T>`).
