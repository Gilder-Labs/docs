---
description: Get an individual members votes. This will get their votes across all daos.
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
  DEFAULT_SPL_GOVERNANCE_ID, // change this to based on the realms program id
  membersWalletAddress
);
```
