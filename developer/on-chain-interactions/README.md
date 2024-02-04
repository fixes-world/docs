---
description: Welcome to FIXeS on-chain interactions documentation
---

# On-chain Interactions

## Overview

In this section, we provide detailed instructions on interacting with the FIXeS contract on the blockchain. To effectively interact with the FIXeS contract, users should possess a basic understanding of blockchain technology, smart contracts, and the Flow blockchain that the FIXeS contract is deployed on.

***

## Getting Started

You can get the contract address of FIXeS here: [#contracts](../../concepts/fixes-inscription.md#contracts "mention")

For front-end or NodeJS projects, we have prepared a more user-friendly way of integration. You can follow this guide to get started.

### Requirements

* Node version `v16.0.0 or higher`.
* FCL(Flow Client Library) installation: [Official Doc](https://developers.flow.com/tools/clients/fcl-js)

### Dependencies Installation

Install FIXeS contracts to your application via `npm`,  `yarn,` or `pnpm`

```bash
npm i @fixes/contracts
```

```bash
yarn add @fixes/contracts
```

```bash
pnpm add @fixes/contracts
```

### Include \*.cdc assets for your project

Interacting with the Flow blockchain requires using [transactions](https://developers.flow.com/tools/clients/fcl-js/transactions)/[scripts](https://developers.flow.com/tools/clients/fcl-js/scripts), and all necessary ones are included in `@fixes/contracts` package. However, to use them in your application, you need to make sure that your building tool can recognize this file extension first.

Using [Vite](https://vitejs.dev/) as an example, you need to add this field in [vite.config.js](https://vitejs.dev/config/shared-options.html#assetsinclude):&#x20;

```javascript
{
    assetsInclude: ["**/*.cdc"],
}
```

### How to quickly set up FCL ?

> FCL is an all-in-one JS library to interact with Flow blockchain, If you are not familiar with it, you can refer to the code below.

Here is an independent wrapped class of FCL :

```typescript
/// This is a TypeScript example
/// If some type is not found, you can directly change it to any

import * as fcl from "@onflow/fcl";
import type { Account, TransactionStatus } from "@onflow/typedefs";

export type NetworkType = "mainnet" | "testnet" | "emulator";

let isGloballyInited = false;
let globallyPromise = null;

export class FlowService {
  public readonly network: NetworkType;
  private readonly flowJSON: object;

  /**
   * Initialize the Flow SDK
   */
  constructor(flowJSON: object) {
    this.network =
      (import.meta.env.PUBLIC_FLOW_NETWORK as NetworkType) ?? "emulator";
    this.flowJSON = flowJSON;
  }

  async onModuleInit() {
    if (isGloballyInited) return;

    const cfg = fcl.config();
    // Required
    await cfg.put("flow.network", this.network);
    // Set the maximum of gas limit
    await cfg.put("fcl.limit", 9999);

    // Note: If you don't need to be compatible with an FCL-compatible wallet
    // you don't need to configure these two parameters.
    await cfg.put("app.detail.title", "App Title");
    await cfg.put("app.detail.icon", "App Icon URL");

    switch (this.network) {
      case "mainnet":
        // Required
        await cfg.put(
          "accessNode.api",
          import.meta.env.PUBLIC_MAINNET_ENDPOINT ??
            "https://mainnet.onflow.org"
        );

        // Note: If you don't need to be compatible with an FCL-compatible wallet
        // you don't need to configure these two following parameters.
        await cfg.put(
          "discovery.wallet",
          "https://fcl-discovery.onflow.org/authn"
        );
        await cfg.put(
          "discovery.authn.endpoint",
          "https://fcl-discovery.onflow.org/api/authn"
        );
        break;
      case "testnet":
        // Required
        await cfg.put("accessNode.api", "https://testnet.onflow.org");

        // Note: If you don't need to be compatible with an FCL-compatible wallet
        // you don't need to configure these two following parameters.
        await cfg.put(
          "discovery.wallet",
          "https://fcl-discovery.onflow.org/testnet/authn"
        );
        await cfg.put(
          "discovery.authn.endpoint",
          "https://fcl-discovery.onflow.org/api/testnet/authn"
        );
        break;
      case "emulator":
        // Required
        await cfg.put("accessNode.api", "http://localhost:8888");

        // Note: If you don't need to be compatible with an FCL-compatible wallet
        // you don't need to configure these following parameters.
        await cfg.put("discovery.wallet", "http://localhost:8701/fcl/authn");
        break;
      default:
        throw new Error(`Unknown network: ${String(this.network)}`);
    }

    // Load Flow JSON
    await cfg.load({ flowJSON: this.flowJSON });

    isGloballyInited = true;
  }

  /**
   * Ensure the Flow SDK is initialized
   */
  private async ensureInited() {
    if (isGloballyInited) return;
    if (!globallyPromise) {
      globallyPromise = this.onModuleInit();
    }
    return await globallyPromise;
  }

  /**
   * Authenticate for current user
   * Only supported on the front-end.
   */
  async authenticate() {
    await this.ensureInited();
    fcl.authenticate();
  }

  /**
   * Logout
   * Only supported on the front-end.
   */
  unauthenticate() {
    fcl.unauthenticate();
  }

  /**
   * Get the current logged-in
   * Only supported on the front-end.
   */
  get currentUser() {
    return fcl.currentUser;
  }

  /**
   * Get account information
   */
  async getAccount(addr: string): Promise<Account> {
    await this.ensureInited();
    return await fcl.send([fcl.getAccount(addr)]).then(fcl.decode);
  }

  /**
   * General method of sending transaction
   */
  async sendTransaction(
    code: string,
    args: fcl.ArgumentFunction,
    mainAuthz?: fcl.FclAuthorization,
    extraAuthz?: fcl.FclAuthorization[]
  ) {
    await this.ensureInited();
    if (typeof mainAuthz !== "undefined") {
      return await fcl.mutate({
        cadence: code,
        args: args,
        proposer: mainAuthz,
        payer: mainAuthz,
        authorizations:
          (extraAuthz?.length ?? 0) === 0
            ? [mainAuthz]
            : [mainAuthz, ...extraAuthz],
      });
    } else {
      return await fcl.mutate({
        cadence: code,
        args: args,
      });
    }
  }

  /**
   * Get transaction status
   */
  async getTransactionStatus(
    transactionId: string
  ): Promise<TransactionStatus> {
    await this.ensureInited();
    return await fcl.tx(transactionId).onceExecuted();
  }

  /**
   * Get chain id
   */
  async getChainId() {
    await this.ensureInited();
    return await fcl.getChainId();
  }

  /**
   * Send transaction with single authorization
   */
  async onceTransactionSealed(
    transactionId: string
  ): Promise<TransactionStatus> {
    await this.ensureInited();
    return fcl.tx(transactionId).onceSealed();
  }

  /**
   * Get block object
   * @param blockId
   */
  async getBlockHeaderObject(blockId: string): Promise<fcl.BlockHeaderObject> {
    await this.ensureInited();
    return await fcl
      // eslint-disable-next-line @typescript-eslint/no-unsafe-argument
      .send([fcl.getBlockHeader(), fcl.atBlockId(blockId)])
      .then(fcl.decode);
  }

  /**
   * Send script
   */
  async executeScript<T>(
    code: string,
    args: fcl.ArgumentFunction,
    defaultValue: T
  ): Promise<T> {
    await this.ensureInited();
    try {
      const queryResult = await fcl.query({
        cadence: code,
        args,
      });
      return (queryResult as T) ?? defaultValue;
    } catch (e) {
      console.error(e);
      return defaultValue;
    }
  }
}
```

If you don't need to use an FCL-compatible wallet for on-chain interactions, you can use this `Signer` class:

```typescript
import elliptic from "elliptic";
import { SHA3 } from "sha3";
import * as fcl from "@onflow/fcl";

import { FlowService } from "./flow.service";
// Here is the configuration file for fixes.
import flowJSON from "@fixes/contracts/flow.json" assert { type: "json" };

const ec = new elliptic.ec("p256");

export default class FlowSigner {
  private readonly flowService: FlowService;

  constructor(
    private readonly address: string,
    private readonly privateKeyHex: string,
    private readonly accountIndex: string
  ) {
    this.flowService = new FlowService(flowJSON);
  }

  /**
   * Send a transaction
   * @param code Cadence code
   * @param args Cadence arguments
   */
  async sendTransaction(code: string, args: fcl.ArgumentFunction) {
    return await this.flowService.sendTransaction(
      code,
      args,
      this._buildAuthorization()
    );
  }

  /**
   * Execute a script
   * @param code Cadence code
   * @param args Cadence arguments
   */
  async executeScript<T>(
    code: string,
    args: fcl.ArgumentFunction,
    defaultValue: T
  ): Promise<T> {
    return await this.flowService.executeScript(code, args, defaultValue);
  }

  /**
   * Build authorization
   */
  private _buildAuthorization() {
    const address = this.address;
    const accountIndex = this.accountIndex;
    const privateKey = this.privateKeyHex;
    return async (account) => {
      return {
        ...account,
        tempId: `${address}-${accountIndex}`,
        addr: fcl.sansPrefix(address),
        keyId: Number(accountIndex),
        signingFunction: (signable) => {
          return {
            addr: fcl.withPrefix(address),
            keyId: Number(accountIndex),
            signature: this._signWithKey(privateKey, signable.message),
          };
        },
      };
    };
  }

  /**
   * Sign a message with a private key
   */
  private _signWithKey(privateKey: string, msg: string) {
    const key = ec.keyFromPrivate(Buffer.from(privateKey, "hex"));
    const sig = key.sign(this._hashMsg(msg));
    const n = 32;
    const r = sig.r.toArrayLike(Buffer, "be", n);
    const s = sig.s.toArrayLike(Buffer, "be", n);
    return Buffer.concat([r, s]).toString("hex");
  }

  /**
   * Hash a message
   */
  private _hashMsg(msg: string) {
    const sha = new SHA3(256);
    sha.update(Buffer.from(msg, "hex"));
    return sha.digest();
  }
} 
```

#### How to send a transaction to Flow blockchain or query data from Flow blockchain?

Here are some example codes. [learn more from the official doc](https://developers.flow.com/tools/clients/fcl-js/api#mutate)

> In the following documentation, `flow` means an instence of `flowSigner` or `flowService` as the subject of function calls.

```typescript
// FIXeS configure
import flowJSON from "@fixes/contracts/flow.json" assert { type: "json" };
// FIXeS Transactions
import txHeartbeatStaking from "@fixes/contracts/transactions/staking/heartbeat-staking.cdc?raw";
// FIXeS Scripts
import scResolveName from "@fixes/contracts/scripts/utils/resolve-name.cdc?raw";

import { FlowService } from "./flow.service";
import FlowSigner from "./Signer";

async function heartbeat(tickerName: string): Promise<string> {
    const flowSigner = new FlowSigner(signerAddr, signerPrivKey, signerKeyId);
    // If you want to directly use FCL-compatible wallets on the frontend,
    // you can also use flowService here, but you need to connect the wallet 
    // first using flowService.authenticate
    const txid = await flowSigner.sendTransaction(
      txHeartbeatStaking,
      (arg, t) => [arg(tickerName, t.String)]
    );
    return txid;
}

async function resolveAddressName(addr: string): Promise<string> {
    const flowService = new FlowService(flowJSON);
    return await flowService.executeScript(
        scResolveName,
        (arg, t) => [arg(addr, t.Address)]
        addr
    )
}
```

***

### 𝔉rc20 Interactions

{% content-ref url="rc20/" %}
[rc20](rc20/)
{% endcontent-ref %}

### Fixes Inscription Interactions

{% content-ref url="fixes-inscription/" %}
[fixes-inscription](fixes-inscription/)
{% endcontent-ref %}
