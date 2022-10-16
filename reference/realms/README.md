---
description: Realms are equivalent to DAOs on other chains
---

# 🏰 Realms

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
// Mango dao public key
let realmId = new PublicKey("DPiH3H3c7t47BMxqTxLsuPQpEC6Kne8GA9VXbxpnZxFE");
const realm = await getRealm(connection, realmId);
```

