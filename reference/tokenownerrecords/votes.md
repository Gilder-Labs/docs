---
description: Get an individual members votes
---

# Votes

### Fetch a members votes

{% code overflow="wrap" %}
```typescript
getVoteRecordsByVoter(connection: Connection, programId: PublicKey, voter: PublicKey): Promise<ProgramAccount<VoteRecord>[]>
```
{% endcode %}

#### Example

```typescript
import { PublicKey, ConfirmedSignatureInfo, Connection } from "@solana/web3.js";
import {
  getVoteRecordsByVoter, 
} from "@solana/spl-governance";


const memberVotes = await getVoteRecordsByVoter(
  connection,
  new PublicKey(realm.governanceId), // change this based on the dao program id
  new PublicKey(member.walletId)
);
```
