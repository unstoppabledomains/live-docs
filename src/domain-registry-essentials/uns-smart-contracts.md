[comment]: <> (! Note: Do not modify src/domain-registry-essentials/uns-smart-contracts.md directly. Edit templates/uns-smart-contracts-template.md instead following rules from README.)
# UNS smart contracts

Unstoppable Name Service (UNS) is built on Ethereum and is effectively a bundle of Solidity smart contracts. Their source code is hosted in the [UNS repository](https://github.com/unstoppabledomains/uns) and maintained by the Unstoppable Domains team. This page lists the smart contracts from that repository and gives a brief description of each along with links to the source code and deployment addresses. For high-level details about how UNS works, see [UNS Architecture overview](uns-architecture-overview.md).

This page is divided into sections, grouping contracts by the following categories:

- [User-facing contracts](uns-smart-contracts.md#user-facing-contracts)
- [Registry controllers](uns-smart-contracts.md#registry-controllers)
- [Interfaces](uns-smart-contracts.md#interfaces)
- [Utility contracts](uns-smart-contracts.md#utility-contracts)

## User-facing contracts

This section lists all the smart contracts that users can directly interact with.

### UNSRegistry


`Registry` is the most essential smart contract in UNS. This is the contract that defines ownership rules, how domains are minted, provides [ERC-721 token metadata](https://docs.openzeppelin.com/contracts/2.x/api/token/erc721#IERC721Metadata), and stores a metadata-enriched list of all domains. This is where domain owners store their data, such as cryptocurrency addresses, chat IDs, and IPFS hashes for decentralized websites.

Under the surface, Registry is effectively a map of domain namehashes to key-value dictionaries of records. This structure allows users to store arbitrary records, even those that aren't specified by the [Records reference](records-reference.md).

[comment]: <> (This is an auto-generated table with CNS smart-contract addresses. See README for more info.)
<table>
    <th>Network</th>
    <th>Contract address</th>
    <tr>
        <td>Mainnet</td>
        <td><a href="https://etherscan.io/address/0x049aba7510f45BA5b64ea9E658E342F904DB358D">0x049aba7510f45BA5b64ea9E658E342F904DB358D</a></td>
    </tr>
    <tr>
        <td>Rinkeby</td>
        <td><a href="https://rinkeby.etherscan.io/address/0x7fb83000B8eD59D3eAD22f0D584Df3a85fBC0086">0x7fb83000B8eD59D3eAD22f0D584Df3a85fBC0086</a></td>
    </tr>
    <tr>
        <td>Polygon mainnet</td>
        <td><a href="https://polygon mainnet.etherscan.io/address/0xa9a6A3626993D487d2Dbda3173cf58cA1a9D9e9f">0xa9a6A3626993D487d2Dbda3173cf58cA1a9D9e9f</a></td>
    </tr>
    <tr>
        <td>Polygon testnet (Mumbai)</td>
        <td><a href="https://polygon testnet (mumbai).etherscan.io/address/0x2a93C52E7B6E7054870758e15A1446E769EdfB93">0x2a93C52E7B6E7054870758e15A1446E769EdfB93</a></td>
    </tr>
</table>


**Source code:** [contracts/UnsRegistry.sol](https://github.com/unstoppabledomains/uns/blob/main/contracts/UNSRegistry.sol)

### ProxyReader

`ProxyReader` provides an interface that allows users to fetch information about domains from both `UNSRegistry` and CNS smart contracts in one call. For more details, see [Architecture overview - ProxyReader](architecture-overview.md#proxyreader).

[comment]: <> (This is an auto-generated table with CNS smart-contract addresses. See README for more info.)
<table>
    <th>Network</th>
    <th>Contract address</th>
    <tr>
        <td>Mainnet</td>
        <td><a href="https://etherscan.io/address/0xc3C2BAB5e3e52DBF311b2aAcEf2e40344f19494E">0xc3C2BAB5e3e52DBF311b2aAcEf2e40344f19494E</a></td>
    </tr>
    <tr>
        <td>Rinkeby</td>
        <td><a href="https://rinkeby.etherscan.io/address/0xE6729D224D00b3dd4FC731C4Ee3274E35Da06578">0xE6729D224D00b3dd4FC731C4Ee3274E35Da06578</a></td>
    </tr>
    <tr>
        <td>Polygon mainnet</td>
        <td><a href="https://polygon mainnet.etherscan.io/address/0xA3f32c8cd786dc089Bd1fC175F2707223aeE5d00">0xA3f32c8cd786dc089Bd1fC175F2707223aeE5d00</a></td>
    </tr>
    <tr>
        <td>Polygon testnet (Mumbai)</td>
        <td><a href="https://polygon testnet (mumbai).etherscan.io/address/0x332A8191905fA8E6eeA7350B5799F225B8ed30a9">0x332A8191905fA8E6eeA7350B5799F225B8ed30a9</a></td>
    </tr>
</table>
</br>
<table>
    <th>Network</th>
    <th>Legacy addresses</th>
    <tr>
        <td>Mainnet</td>
           <td><a 
                    href="https://etherscan.io/address/0xfEe4D4F0aDFF8D84c12170306507554bC7045878">0xfEe4D4F0aDFF8D84c12170306507554bC7045878</a>
               <a 
                    href="https://etherscan.io/address/0xa6E7cEf2EDDEA66352Fd68E5915b60BDbb7309f5">0xa6E7cEf2EDDEA66352Fd68E5915b60BDbb7309f5</a>
               <a 
                    href="https://etherscan.io/address/0x7ea9Ee21077F84339eDa9C80048ec6db678642B1">0x7ea9Ee21077F84339eDa9C80048ec6db678642B1</a>
            </td>
    </tr>
    <tr>
        <td>Rinkeby</td>
           <td><a 
                    href="https://rinkeby.etherscan.io/address/0x299974AeD8911bcbd2C61262605b89F591a53E83">0x299974AeD8911bcbd2C61262605b89F591a53E83</a>
               <a 
                    href="https://rinkeby.etherscan.io/address/0x9F19473F6a98a715176291c930558E1954fd3D1e">0x9F19473F6a98a715176291c930558E1954fd3D1e</a>
               <a 
                    href="https://rinkeby.etherscan.io/address/0x3A2e74CF832cbA3d77E72708d55370119E4323a6">0x3A2e74CF832cbA3d77E72708d55370119E4323a6</a>
            </td>
    </tr>
</table>


**Source code:** [contracts/ProxyReader.sol](https://github.com/unstoppabledomains/uns/blob/main/contracts/ProxyReader.sol)

### TwitterValidationOperator

`TwitterValidationOperator` is used when initiating Chainlink verification requests to link domain records with Twitter usernames.

[comment]: <> (This is an auto-generated table with CNS smart-contract addresses. See README for more info.)
<table>
    <th>Network</th>
    <th>Contract address</th>
    <tr>
        <td>Mainnet</td>
        <td><a href="https://etherscan.io/address/0x2F659766E3D08561CA3408FbAba7C0749ab2c402">0x2F659766E3D08561CA3408FbAba7C0749ab2c402</a></td>
    </tr>
    <tr>
        <td>Rinkeby</td>
        <td><a href="https://rinkeby.etherscan.io/address/0x9ea4A63184ebE9CBA55CD1af473D98075Aa02b4C">0x9ea4A63184ebE9CBA55CD1af473D98075Aa02b4C</a></td>
    </tr>
    <tr>
        <td>Polygon mainnet</td>
        <td><a href="https://polygon mainnet.etherscan.io/address/0x0000000000000000000000000000000000000000">0x0000000000000000000000000000000000000000</a></td>
    </tr>
    <tr>
        <td>Polygon testnet (Mumbai)</td>
        <td><a href="https://polygon testnet (mumbai).etherscan.io/address/0x0000000000000000000000000000000000000000">0x0000000000000000000000000000000000000000</a></td>
    </tr>
</table>
</br>
<table>
    <th>Network</th>
    <th>Legacy addresses</th>
    <tr>
        <td>Mainnet</td>
           <td><a 
                    href="https://etherscan.io/address/0xbb486C6E9cF1faA86a6E3eAAFE2e5665C0507855">0xbb486C6E9cF1faA86a6E3eAAFE2e5665C0507855</a>
            </td>
    </tr>
    <tr>
        <td>Rinkeby</td>
           <td><a 
                    href="https://rinkeby.etherscan.io/address/0x1CB337b3b208dc29a6AcE8d11Bb591b66c5Dd83d">0x1CB337b3b208dc29a6AcE8d11Bb591b66c5Dd83d</a>
            </td>
    </tr>
</table>


**Source code:** [contracts/operators/TwitterValidationOperator.sol](https://github.com/unstoppabledomains/uns/blob/main/contracts/operators/TwitterValidationOperator.sol)

## Registry controllers

The Unstoppable Domains team reserves the right to mint second-level domains and edit some `Registry` settings, such as token URI prefix. To avoid giving anyone absolute admin rights, `Registry` utilizes controllers that implement a limited set of admin actions.

### MintingManager

`MintingManager` defines an interface for minting second-level domains. This smart contract is primarily used by the Unstoppable Domains team, but its interface also supports delegating minting process to other parties via [Meta Transactions](../managing-domains/meta-transactions.md). All calls to `MintingManager` are proxied to the `UNSRegistry` via the [MintingManager](uns-smart-contracts.md#mintingmanager) smart contract.

[comment]: <> (This is an auto-generated table with CNS smart-contract addresses. See README for more info.)
<table>
    <th>Network</th>
    <th>Contract address</th>
    <tr>
        <td>Mainnet</td>
        <td><a href="https://etherscan.io/address/0x2a7084870bB724175a3C96Da8FaA55128fa3E19D">0x2a7084870bB724175a3C96Da8FaA55128fa3E19D</a></td>
    </tr>
    <tr>
        <td>Rinkeby</td>
        <td><a href="https://rinkeby.etherscan.io/address/0xdAAf99A920D31F4f5720e4667b12b24e54A03070">0xdAAf99A920D31F4f5720e4667b12b24e54A03070</a></td>
    </tr>
    <tr>
        <td>Polygon mainnet</td>
        <td><a href="https://polygon mainnet.etherscan.io/address/0x7be83293BeeDc9Eba1bd76c66A65F10F3efaeC26">0x7be83293BeeDc9Eba1bd76c66A65F10F3efaeC26</a></td>
    </tr>
    <tr>
        <td>Polygon testnet (Mumbai)</td>
        <td><a href="https://polygon testnet (mumbai).etherscan.io/address/0x428189346bb3CC52f031A1092fd47C919AC30A9f">0x428189346bb3CC52f031A1092fd47C919AC30A9f</a></td>
    </tr>
</table>


**Source code:** [contracts/MintingManager.sol](https://github.com/unstoppabledomains/uns/blob/main/contracts/MintingManager.sol)

## Interfaces

The following interfaces can be used as guidelines for the minimal implementation of custom smart contract versions. Also, Solidity developers can rely on them for making calls to the official CNS smart contracts.

### IDataReader

The `IDataReader` interface declares the methods that are unique to the `ProxyReader` smart contract, which returns combined data from the `Registry` and `Resolver` contracts.

**Source code:** [contracts/IDataReader.sol](https://github.com/unstoppabledomains/uns/blob/main/contracts/IDataReader.sol)

**Implemented by:**

- [ProxyReader](uns-smart-contracts.md#proxyreader)

### IMintingManager

The `IMintingManager` interface declares a set of methods for minting second level domains.

**Source code:** [contracts/IMintingManager.sol](https://github.com/unstoppabledomains/uns/blob/main/contracts/IMintingManager.sol)

**Implemented by:**

- [MintingManager](uns-smart-contracts.md#mintingmanager)

### IRecordReader

The `IRecordReader` interface declares read methods for resolution data.

**Source code:** [contracts/IRecordReader.sol](https://github.com/unstoppabledomains/uns/blob/main/contracts/IRecordReader.sol)

**Implemented by:**

- [ProxyReader](uns-smart-contracts.md#proxyreader)
- [UNSRegistry](uns-smart-contracts.md#unsregistry)

### IRecordStorage

The `IRecordStorage` interface declares write methods for resolution data.

**Source code:** [contracts/IRecordStorage.sol](https://github.com/unstoppabledomains/uns/blob/main/contracts/IRecordStorage.sol)

**Implemented by:**

- [UNSRegistry](uns-smart-contracts.md#unsregistry)

### IRegistryReader

The `IRegistryReader` interface declares only read-only `Registry` methods.

**Source code:** [contracts/IRegistryReader.sol](https://github.com/unstoppabledomains/uns/blob/main/contracts/IRegistryReader.sol)

**Implemented by:**

- [ProxyReader](uns-smart-contracts.md#proxyreader)

### IUNSRegistry

The `IUNSRegistry` interface declares all the `UNSRegistry` events and methods (both read and write).

**Source code:** [contracts/IUNSRegistry.sol](https://github.com/unstoppabledomains/uns/blob/main/contracts/IUNSRegistry.sol)

**Implemented by:**

- [UNSRegistry](uns-smart-contracts.md#unsregistry)

### ERC677Receiver

The `ERC677Receiver` interface declares an ERC-677 method for receiving smart contracts.

**Source code:** [contracts/util/ERC677Receiver.sol](https://github.com/unstoppabledomains/uns/blob/main/contracts/util/ERC677Receiver.sol)

**Implemented by:**

- [TwitterValidationOperator.sol](uns-smart-contracts.md#twittervalidationoperator)

## Utility contracts

Utility contracts are generally used to share common functionality between other smart contracts. This list also includes some contracts that are used internally by the Unstoppable Domains team.

### KeyStorage

`KeyStorage` implements functions for adding and retrieving a set of keys which can be resolved from a domain.

**Source code:** [contracts/KeyStorage.sol](https://github.com/unstoppabledomains/uns/blob/main/contracts/KeyStorage.sol)

**Used by:**

- [UNSRegistry](uns-smart-contracts.md#unsregistry)

### RecordStorage

`RecordStorage` implements functions for adding and retrieving records from a domain.

**Source code:** [contracts/RecordStorage.sol](https://github.com/unstoppabledomains/uns/blob/main/contracts/RecordStorage.sol)

**Used by:**

- [UNSRegistry](uns-smart-contracts.md#unsregistry)

### BulkWhitelistedRole

`BulkWhitelistedRole` is an extension of Open Zeppelin's `WhitelistedRole` that adds bulk operations for adding and removing whitelisted accounts.

**Source code:** [contracts/roles/BulkWhitelistedRole.sol](https://github.com/unstoppabledomains/uns/blob/main/contracts/roles/BulkWhitelistedRole.sol)

**Used by:**

- [WhitelistedMinter](uns-smart-contracts.md#whitelistedminter)

### CapperRole

`CapperRole` is an extension of Open Zeppelin's `AccessControlUpgradeable` that adds operations for adding and removing capper accounts.

**Source code:** [contracts/roles/CapperRole.sol](https://github.com/unstoppabledomains/uns/blob/main/contracts/roles/CapperRole.sol)

**Used by:**

- [TwitterValidationOperator.sol](uns-smart-contracts.md#twittervalidationoperator)

### MinterRole

`MinterRole` is an extension of Open Zeppelin's `AccessControlUpgradeable` that adds operations for adding and removing minting accounts.

**Source code:** [contracts/roles/MinterRole.sol](https://github.com/unstoppabledomains/uns/blob/main/contracts/roles/MinterRole.sol)

**Used by:**

- [MintingManager.sol](uns-smart-contracts.md#mintingmanager)

### WhitelistedRole

`WhitelistedRole` is an extension of Open Zeppelin's `AccessControlUpgradeable` that adds operations for adding and removing whitelisted accounts.

**Source code:** [contracts/roles/WhitelistedRole.sol](https://github.com/unstoppabledomains/uns/blob/main/contracts/roles/WhitelistedRole.sol)

**Used by:**

- [BulkWhitelistedRole.sol](uns-smart-contracts.md#bulkwhitelistedrole)
- [TwitterValidationOperator.sol](uns-smart-contracts.md#twittervalidationoperator)

### MultiSend

The `MultiSend` smart contract is used internally by the Unstoppable Domains team to fund worker accounts.

**Source code:** [contracts/util/MultiSend.sol](https://github.com/unstoppabledomains/uns/blob/main/contracts/util/MultiSend.sol)
