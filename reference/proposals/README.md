# Proposals

### Fetch Realm Proposals

{% code overflow="wrap" %}
```typescript
getAllProposals(connection: Connection, programId: PublicKey, realmPk: PublicKey): Promise<ProgramAccount<Proposal>[][]>
```
{% endcode %}

#### Example

{% code overflow="wrap" %}
```typescript
// default spl-governance program id, most dao's use this
const realmProgramId = new PublicKey("GovER5Lthms3bLBqWub97yVrMmEogzX7xNjdXpPPCVZw");
// Grape dao realm id
const realmPublicKey = new PublicKey("By2sVGZXwfQq6rAiAM3rNPJ9iQfb5e2QhnF4YjJ4Bip")
const proposals = await getAllProposalas(
    connection,
    // public key of program id must be the program that the DAO was set up with.
    realmProgramId,
    // Unique public key of realm 
    realmPublicKey
);
```
{% endcode %}
