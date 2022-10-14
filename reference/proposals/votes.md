---
description: Votes on proposals by members
---

# Votes

### Fetch Votes

{% code overflow="wrap" %}
```typescript
getVoteRecords({ connection, programId, proposalPk, }: Args): Promise<None | Some<ProgramAccount<VoteRecord>[]>>
```
{% endcode %}

#### Example

<pre class="language-javascript"><code class="lang-javascript"><strong>
</strong><strong>const DEFAULT_SPL_GOVERNANCE_ID = new PublicKey("GovER5Lthms3bLBqWub97yVrMmEogzX7xNjdXpPPCVZw");
</strong>const proposalId = new PublicKey("2PwgCid6JCFXLvcqHiCTaMHJLHR65EqwvboTycFiZM69");

const votes = await getVoteRecords({
    connection: connection,
    // the program id needs to be the program Id the realm used
    programId: DEFAULT_SPL_GOVERNANCE_ID,
    proposalPk: proposalId,
});</code></pre>
