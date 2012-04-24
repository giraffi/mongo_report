# Usage

    rake repo db_name=giraffi_staging col_name=external_data
    rake chanks db_name=giraffi_staging

# Output
## repo
    ------------------------------------------------
    Status of giraffi_staging.external_data
    -------------------------------------------------
    TotalStatus:
      count: 206709
            size: 46 MBytes
            storageSize: 626 MBytes
            totalIndexSize: 45 MBytes
      avgObjSize:  234.97250724448378 Bytes
      sharded: true
    
    ShardMemberStatus:
      Shard: s01
        count: 84428
        size: 19 MBytes
        storageSize: 130 MBytes
        totalIndexSize: 20 MBytes
      Shard: s02
        count: 0
        size: 0 MBytes
        storageSize: 236 MBytes
        totalIndexSize: 0 MBytes
      Shard: s03
        count: 122281
        size: 27 MBytes
        storageSize: 259 MBytes
        totalIndexSize: 24 MBytes

## chanks
    ----------------------------------------------------
    giraffi_staging chanks count.
    ----------------------------------------------------
    giraffi_staging.external_data chunks:
           s03     10
           s01     7
           s02     8
