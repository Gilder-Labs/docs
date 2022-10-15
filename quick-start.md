# 🏎 Quick Start

## Install the library

Use the official `spl-governance` library to start interacting with DAO's on solana

```
# Install via NPM/yarn
yarn add @solana/spl-governance @solana/web3.js
or 
npm install @solana/spl-governance @solana/web3.js
```

{% embed url="https://www.npmjs.com/package/@solana/spl-governance" %}

```javascript
import { getRealms } from '@solana/spl-governance';
import { Connection, PublicKey } from '@solana/web3.js';

const connection = new Connection("https://api.mainnet-beta.solana.com", 'recent');
const programId = new PublicKey('GovER5Lthms3bLBqWub97yVrMmEogzX7xNjdXpPPCVZw');

const realms = getRealms(connection, programId);
```
