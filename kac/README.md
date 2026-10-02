# KAC_Race plugin allowlist

`baseline.tsv` is the human-readable reviewed list of plugin paths, sizes, and SHA-256 hashes. `manifest.json` carries the same entries in a signed payload and is the only file trusted by KAC_Race at runtime. Paths are audit metadata; KAC authorizes any DLL under `BepInEx/plugins` when its SHA-256 matches an entry. The KA SteamID whitelist at the repository root is independent.

The manifest uses ECDSA P-256 with SHA-256. KAC_Race embeds the public key (SPKI SHA-256 `B0F0BB69ECB37B0DABCD30D593AB83EFF78463E9C126BD504191A0780B067371`). Each update requires an incremented revision and a new signature from the local publisher key. A GitHub edit to this directory alone cannot authorize another DLL.

The current payload expires on 2027-10-01 UTC. Publish a new revision before that date. KAC_Race downloads the manifest once at startup and uses a previously verified, unexpired cache if the download fails. It continues checking loaded DLLs locally after startup.
