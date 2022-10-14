---
description: Fetch on chain comments for a proposal
---

# Comments

### Fetch Comments

{% code overflow="wrap" %}
```typescript
getGovernanceChatMessages(connection: Connection, chatProgramId: PublicKey, proposal: PublicKey): Promise<ProgramAccount<ChatMessage>[]>
```
{% endcode %}

#### Example

```javascript
import { PublicKey } from "@solana/web3.js";

import {
  getGovernanceChatMessages,
  GOVERNANCE_CHAT_PROGRAM_ID,
} from "@solana/spl-governance";

const proposalPublicKey = new PublicKey("2PwgCid6JCFXLvcqHiCTaMHJLHR65EqwvboTycFiZM69");

const proposalComments = await getGovernanceChatMessages(
  connection,
  GOVERNANCE_CHAT_PROGRAM_ID,
  proposalPublicKey
);
```
