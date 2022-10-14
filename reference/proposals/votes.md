---
description: Votes on proposals by members
---

# Votes

### Fetch All Votes on a Proposal

{% code overflow="wrap" %}
```typescript
getVoteRecords({ connection, programId, proposalPk, }: Args): Promise<None | Some<ProgramAccount<VoteRecord>[]>>
```
{% endcode %}

#### Example

<pre class="language-javascript"><code class="lang-javascript"><strong>const DEFAULT_SPL_GOVERNANCE_ID = new PublicKey("GovER5Lthms3bLBqWub97yVrMmEogzX7xNjdXpPPCVZw");
</strong>const proposalId = new PublicKey("2PwgCid6JCFXLvcqHiCTaMHJLHR65EqwvboTycFiZM69");

const proposalVotes = await getVoteRecords({
    connection: connection,
    // the program id needs to be the program Id the realm used
    programId: DEFAULT_SPL_GOVERNANCE_ID,
    proposalPk: proposalId,
});</code></pre>

```typescript
// Code taken from governance-ui github repo. Not yet a part of spl-governance 
// npm package
import { Connection, PublicKey } from "@solana/web3.js";
import { pubkeyFilter, VoteRecord } from "@solana/spl-governance";
import { none, map, some } from "fp-ts/Option";
import { pipe } from "fp-ts/function";
import {
    getGovernanceAccounts,
    GovernanceAccount,
    GovernanceAccountClass,
    ProgramAccount,
    MemcmpFilter,
} from "@solana/spl-governance";

interface Args {
  connection: Connection;
  proposalPk: PublicKey;
  programId: PublicKey;
}

export async function getVoteRecords({
  connection,
  programId,
  proposalPk,
}: Args) {
  const filter = pubkeyFilter(1, proposalPk);

  if (!filter) {
    return none;
  }

  const accounts = await getAccountsByFilters<VoteRecord>({
    connection,
    programId,
    accountClass: VoteRecord,
    filters: [filter],
  });

  return pipe(
    accounts,
    map((accounts) => Object.values(accounts))
  );
}

interface Args {
  accountClass: GovernanceAccountClass;
  connection: Connection;
  filters: MemcmpFilter[];
  programId: PublicKey;
}

export function getAccountsByFilters<AccountType extends GovernanceAccount>({
  accountClass,
  connection,
  filters,
  programId,
}: Args) {
  return pipe(
    tryCatch(
      () =>
        getGovernanceAccounts(
          connection,
          programId,
          accountClass as unknown as new (args: any) => AccountType,
          filters
        ),
      (error) =>
        error instanceof Error ? error : new Error("Could not fetch accounts")
    ),
    map((accounts) =>
      accounts.reduce((acc, account) => {
        acc[account.pubkey.toBase58()] = account;
        return acc;
      }, {} as { [address: string]: ProgramAccount<AccountType> })
    ),
    match((error) => {
      console.error(error);
      return none;
    }, some)
  )();
}


```
