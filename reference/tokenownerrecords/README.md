---
description: These represent the accounts that hold the tokens for a wallet
---

# TokenOwnerRecords

### Fetch All Token Owner Records

{% code overflow="wrap" %}
```typescript
getAllTokenOwnerRecords(connection: Connection, programId: PublicKey, realmPk: PublicKey): Promise<ProgramAccount<TokenOwnerRecord>[]>
```
{% endcode %}

{% hint style="info" %}
One thing to note, is that if a member has a council and community token, they will have \*2\* token owner records. This is because each record keeps track of a members state for each mint (community/council) of the dao.&#x20;
{% endhint %}
