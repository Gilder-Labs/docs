---
description: Realms are equivalent to DAOs on other chains
---

# 🏰 Realms (daos)

### Fetch Realms

```typescript
getRealms(connection: Connection, programId: PublicKey): Promise<ProgramAccount[]>
```

#### Example

```javascript
import { getRealms } from "@solana/spl-governance";
let DEFAULT_SPL_GOVERNANCE_ID = new PublicKey("GovER5Lthms3bLBqWub97yVrMmEogzX7xNjdXpPPCVZw");
const realms = await getRealms(connection, DEFAULT_SPL_GOVERNANCE_ID);
```

{% hint style="info" %}
While this call will get most DAO's that exist for Solana, it will be missing some like Mango for example. This is because DAO's are able to fork the spl-governance program and have their own instance. This gives them final authority over their own DAO program. \
\
To get other DAO instances, you need to fetch by the program ID they set their DAO up with. For example mango's spl-governance program ID is "GqTPL6qRf5aUuqscLh8Rg2HTxPUXfhhAXDptTLhp1t2J"
{% endhint %}

### Fetch Single Realm

```typescript
function getRealm(connection: Connection, realm: PublicKey): Promise<ProgramAccount>// Fetch a single realm by realmId
```

#### Example

```typescript
import { getRealm } from "@solana/spl-governance";
let DEFAULT_SPL_GOVERNANCE_ID = new PublicKey("GovER5Lthms3bLBqWub97yVrMmEogzX7xNjdXpPPCVZw");
const realms = await getRealms(connection, DEFAULT_SPL_GOVERNANCE_ID);
```

### Fetch Realm Program IDs

{% swagger method="get" path=" " baseUrl="https://app.realms.today/api/splGovernancePrograms" summary="Returns a list of program ID's of spl-governance instances deployed on Solana" %}
{% swagger-description %}
This is a community maintained list. To add your instance, make a PR on

[ ](https://github.com/solana-labs/governance-ui)



[https://github.com/solana-labs/governance-ui](https://github.com/solana-labs/governance-ui)


{% endswagger-description %}

{% swagger-response status="200: OK" description="Returns list of spl-governance program ID's" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}
{% endswagger %}

