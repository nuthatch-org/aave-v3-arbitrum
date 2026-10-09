# aave-v3-arbitrum

A [nuthatch](https://github.com/nuthatch-org/nuthatch) nest: **Aave V3 on Arbitrum**.

As `aave-v3`, re-pointed at Arbitrum.

One binary, one config file, no graph-node, no gateway, no query fees.

## What it indexes

**Chain:** `arbitrum-one`. **1 contract**, **15 tables**.

| alias | address |
|---|---|
| `c0` | `0x794a61358d6845594f94dc1db02a252b5b4814ad` |

## Verified

Indexed blocks **496,878,106 to 497,273,932** and sealed **19,144 events**. Every table below is generated from the vendored ABIs, and the run above is what this nest actually decoded, not an estimate.

## Read this before trusting it

- Event set is **identical** to the Ethereum deployment's, despite different implementation bytecode.

## Run it

```sh
nuthatch init --from https://github.com/nuthatch-org/aave-v3-arbitrum
cd aave-v3-arbitrum
nuthatch dev --dir . --backfill 50000 --seal-direct
nuthatch sql --dir . "SELECT count(*) FROM \"c0__borrow\""
```

The endpoint in `nuthatch.toml` is keyless and public, so this file is publishable: a `nuthatch.toml` is pinned into the nest's content address and must never carry a credential. It is enough to follow the tip. A **backfill** wants archive depth it may not have: pass your own with `--rpc`, and check it first with `nuthatch doctor --rpc <url>`.

## Tables

```
c0__borrow
c0__deficit_covered
c0__deficit_created
c0__flash_loan
c0__liquidation_call
c0__minted_to_treasury
c0__position_manager_approved
c0__position_manager_revoked
c0__repay
c0__reserve_data_updated
c0__reserve_used_as_collateral_disabled
c0__reserve_used_as_collateral_enabled
c0__supply
c0__user_e_mode_set
c0__withdraw
```
