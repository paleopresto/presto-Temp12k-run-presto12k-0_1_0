# PReSto Temp12k run on PReSto12k 0_1_0

This repository runs the PReSto Temp12k reconstruction on the [PReSto12k 0_1_0](https://lipdverse.org/PReSto12k/0_1_0/) compilation: 1796 records.

- Membership comes only from the published compilation, read from the
  LiPDverse whole-database export
  [2026-10-27](https://lipdverse.org/dev/export/database-2026-10-27/)
  (`compilations` table) by presto-recipes `pools/compilation_pool.R`.
- `query_params.json` (`mode: bundle`) pins the bundle by URL and sha256:
  presto-recipes release
  [pools-2026-10-27-r2](https://github.com/paleopresto/presto-recipes/releases/tag/pools-2026-10-27-r2).
  Its files are the compilation's LiPD files, checked against the export's
  md5 values and trimmed to the member records, except one curator-fixed file
  used in place of the export's copy (listed under `patched` in the bundle
  manifest): SayramLake.Jiang.2013, whose all-zero primary age column was
  removed (LiPDverse changelog 1.0.5, 2026-10-28; see
  [pools/patches/2026-10-27](https://github.com/paleopresto/presto-recipes/tree/pools-2026-10-27-r2/pools/patches/2026-10-27)).
  On the r1 bundle, which had the export's copy, HoloceneDA failed on that
  axis.
- The code and algorithm config are those of
  [presto-Temp12k-run-presto12k-0_0_1](https://github.com/paleopresto/presto-Temp12k-run-presto12k-0_0_1)
  at 83b58b8, unchanged, so this run differs from that one only in its data:
  PReSto12k 0_1_0 instead of 0_0_1. The records added and removed are listed in
  [changes_from_0_0_1.csv](https://github.com/paleopresto/presto-recipes/blob/pools-2026-10-27-r1/pools/compilations/PReSto12k/0_1_0/changes_from_0_0_1.csv).

Committing `query_params.json` triggers the reconstruction workflow.
