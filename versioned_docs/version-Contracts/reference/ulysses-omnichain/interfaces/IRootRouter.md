---
id: IRootRouter
title: IRootRouter
---

**Author:**
MaiaDAO

Base Branch Contract for interfacing with Root Bridge Agents.
This contract for deployment in the Root Chain of the Ulysses Omnichain System,
additional logic can be implemented to perform actions before sending cross-chain
requests to Branch Chains, as well as in response to remote requests.

## Functions

### anyExecuteResponse

Function to execute Branch Bridge Agent system initiated requests with no asset deposit.

```solidity
function anyExecuteResponse(bytes1 funcId, bytes memory encodedData, uint24 fromChainId)
    external
    payable
    returns (bool success, bytes memory result);
```

**Parameters**

| Name          | Type     | Description                               |
| ------------- | -------- | ----------------------------------------- |
| `funcId`      | `bytes1` | 1 byte called Router function identifier. |
| `encodedData` | `bytes`  | data received from messaging layer.       |
| `fromChainId` | `uint24` | chain where the request originated from.  |

### anyExecute

Function responsible of executing a crosschain request without any deposit.

```solidity
function anyExecute(bytes1 funcId, bytes memory encodedData, uint24 fromChainId)
    external
    payable
    returns (bool success, bytes memory result);
```

**Parameters**

| Name          | Type     | Description                              |
| ------------- | -------- | ---------------------------------------- |
| `funcId`      | `bytes1` | 1 byte Router function identifier.       |
| `encodedData` | `bytes`  | data received from messaging layer.      |
| `fromChainId` | `uint24` | chain where the request originated from. |

### anyExecuteDepositSingle

Function responsible of executing a crosschain request which contains cross-chain deposit information attached.

```solidity
function anyExecuteDepositSingle(
    bytes1 funcId,
    bytes memory encodedData,
    DepositParams memory dParams,
    uint24 fromChainId
) external payable returns (bool success, bytes memory result);
```

**Parameters**

| Name          | Type            | Description                                   |
| ------------- | --------------- | --------------------------------------------- |
| `funcId`      | `bytes1`        | 1 byte Router function identifier.            |
| `encodedData` | `bytes`         | execution data received from messaging layer. |
| `dParams`     | `DepositParams` | cross-chain deposit information.              |
| `fromChainId` | `uint24`        | chain where the request originated from.      |

### anyExecuteDepositMultiple

Function responsible of executing a crosschain request which contains cross-chain deposit information for multiple assets attached.

```solidity
function anyExecuteDepositMultiple(
    bytes1 funcId,
    bytes memory encodedData,
    DepositMultipleParams memory dParams,
    uint24 fromChainId
) external payable returns (bool success, bytes memory result);
```

**Parameters**

| Name          | Type                    | Description                                   |
| ------------- | ----------------------- | --------------------------------------------- |
| `funcId`      | `bytes1`                | 1 byte Router function identifier.            |
| `encodedData` | `bytes`                 | execution data received from messaging layer. |
| `dParams`     | `DepositMultipleParams` | cross-chain multiple deposit information.     |
| `fromChainId` | `uint24`                | chain where the request originated from.      |

### anyExecuteSigned

Function responsible of executing a crosschain request with msg.sender without any deposit.

```solidity
function anyExecuteSigned(bytes1 funcId, bytes memory encodedData, address userAccount, uint24 fromChainId)
    external
    payable
    returns (bool success, bytes memory result);
```

**Parameters**

| Name          | Type      | Description                                   |
| ------------- | --------- | --------------------------------------------- |
| `funcId`      | `bytes1`  | 1 byte Router function identifier.            |
| `encodedData` | `bytes`   | execution data received from messaging layer. |
| `userAccount` | `address` | user account address.                         |
| `fromChainId` | `uint24`  | chain where the request originated from.      |

### anyExecuteSignedDepositSingle

Function responsible of executing a crosschain request which contains cross-chain deposit information and msg.sender attached.

```solidity
function anyExecuteSignedDepositSingle(
    bytes1 funcId,
    bytes memory encodedData,
    DepositParams memory dParams,
    address userAccount,
    uint24 fromChainId
) external payable returns (bool success, bytes memory result);
```

**Parameters**

| Name          | Type            | Description                                   |
| ------------- | --------------- | --------------------------------------------- |
| `funcId`      | `bytes1`        | 1 byte Router function identifier.            |
| `encodedData` | `bytes`         | execution data received from messaging layer. |
| `dParams`     | `DepositParams` | cross-chain deposit information.              |
| `userAccount` | `address`       | user account address.                         |
| `fromChainId` | `uint24`        | chain where the request originated from.      |

### anyExecuteSignedDepositMultiple

Function responsible of executing a crosschain request which contains cross-chain deposit information for multiple assets and msg.sender attached.

```solidity
function anyExecuteSignedDepositMultiple(
    bytes1 funcId,
    bytes memory encodedData,
    DepositMultipleParams memory dParams,
    address userAccount,
    uint24 fromChainId
) external payable returns (bool success, bytes memory result);
```

**Parameters**

| Name          | Type                    | Description                                   |
| ------------- | ----------------------- | --------------------------------------------- |
| `funcId`      | `bytes1`                | 1 byte Router function identifier.            |
| `encodedData` | `bytes`                 | execution data received from messaging layer. |
| `dParams`     | `DepositMultipleParams` | cross-chain multiple deposit information.     |
| `userAccount` | `address`               | user account address.                         |
| `fromChainId` | `uint24`                | chain where the request originated from.      |

## Errors

### UnrecognizedBridgeAgentExecutor

```solidity
error UnrecognizedBridgeAgentExecutor();
```
