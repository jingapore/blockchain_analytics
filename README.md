# Introduction

A deconstruction of BlockSci library, applied to data retrieved from a Litecoin node.

# Parsing

In `tools/parser/chain_index.cpp`, we loop over `block_????.data` files spawning one thread per file up to 20 max threads, and read them. Then each thread acquires a lock and writes the block into `blockList`, which has type `std::unordered_map<blocksci::uint256, BlockType> blockList;`. (Question: Why use an unordered_map, which implies the requirement for random access by block number?)

After this, still in `tools/parser/chain_index.cpp`, we have `forwardHashes`.