= Implementation Plan: D-Vector Search

== Phase 1: Metric Functions
- Implement `cosine_similarity(float[] a, float[] b)` using `std.simd` or `mir-algorithm`.
- Implement `l2_distance`.

== Phase 2: Flat Index
- `struct FlatIndex`:
    - `float[][] vectors`: Store all embeddings.
    - `ulong[] ids`: Map vector index to external ID.
    - `search(query_vector, k)` -> Returns top k matches.
    - `add(vector, id)`.
    - `save(path)`.
    - `load(path)`.

== Phase 3: IVF (Inverted File) Index
- Implement k-means clustering (use `dstats` or write simple one).
- Partition vectors into lists based on nearest centroid.
- Implement search across `nprobe` lists.

== Optimization
- Parallelize brute-force search using `std.parallelism`.
