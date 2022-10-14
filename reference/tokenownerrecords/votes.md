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

const membersWalletAddress = new PublicKey("EVa7c7XBXeRqLnuisfkvpXSw5VtTNVM8MNVJjaSgWm4i");
const DEFAULT_SPL_GOVERNANCE_ID = new PublicKey("GovER5Lthms3bLBqWub97yVrMmEogzX7xNjdXpPPCVZw");


const memberVotes = await getVoteRecordsByVoter(
  connection,
  // this arg needs to be the spl-governance program id of the realm
  DEFAULT_SPL_GOVERNANCE_ID, // change this based on the dao program id
  membersWalletAddress
);
```
