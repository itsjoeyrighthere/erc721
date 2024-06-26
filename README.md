# ERC-721 Buggy Token



## Structure

All contracts and tests are in the [src](src/) folder. There are multiple implementations and you can select between:

- [`nf-token.sol`](src/contracts/tokens/nf-token.sol): This is the base ERC-721 token implementation (with support for ERC-165).
- [`nf-token-metadata.sol`](src/contracts/tokens/nf-token-metadata.sol): This implements optional ERC-721 metadata features for the token contract. It implements a token name, a symbol and a distinct URI pointing to a publicly exposed ERC-721 JSON metadata file.
- [`nf-token-enumerable.sol`](src/contracts/tokens/nf-token-enumerable.sol): This implements optional ERC-721 support for enumeration. It is useful if you want to know the total supply of tokens, to query a token by index, etc.

Other files in the [tokens](src/contracts/tokens) and [utils](src/contracts/utils) directories named `erc*.sol` are interfaces and define the respective standards.

[buggy_nft](./src/contracts/buggy_nft.sol) is a buggy implementation of ERC721

## Bugs
1. burn 调用之后，totalSupply 不会减一
2. 没有 Approve 权限也可以通过 safeTransferFrom 转移别人的 NFT
3. 调用 transferFrom 和 safetransferFrom 之后，owner不会改变
4. mint 和 burn 调用之后，用户的 balance 不会改变
