# Dao membership

### Fetch a wallets dao membership

{% code overflow="wrap" %}
```typescript
getTokenOwnerRecordsByOwner(connection: Connection, programId: PublicKey, governingTokenOwner: PublicKey): Promise<ProgramAccount[]>Example
```
{% endcode %}

#### Example

```javascript
import { PublicKey, ConfirmedSignatureInfo, Connection } from "@solana/web3.js";
import { getTokenOwnerRecordsByOwner } from "@solana/spl-governance";

const DEFAULT_SPL_GOVERNANCE_ID = "GovER5Lthms3bLBqWub97yVrMmEogzX7xNjdXpPPCVZw";
const programId = new PublicKey(DEFAULT_SPL_GOVERNANCE_ID);
const walletId = new PublicKey("wallet address");

// Returns all token records for a given wallet address and 
// spl-governance program instance. 
const tokenOwnerRecordsbyOwner = await getTokenOwnerRecordsByOwner(
    connection,
    programId,
    walletId
);


// Make a unique list of all realmIds
const daosSet = new Set();
ownerRecordsbyOwner.map((realm) => {
    daosSet.add(realm.account.realm.toBase58());
});

// Now have an array of each realm the wallet address is in. 
const realmList = Array.from(daosSet);
```

{% hint style="info" %}
The code written above will only get the DAO's a user is in for the specificed governance id. To get all daos for a user for all spl-governance, you would need to iterate through each spl-governance program and get their records.&#x20;
{% endhint %}
