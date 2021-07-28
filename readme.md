|Warning| It is up to the user to provide a correct block device for testing.
|---|---|

|NOTE|It BLOCK_DEVICE is not a block device, the tests exits with rc=2 silently
|---|---|

# Prepare test device

* Create a block device on unallocated space
```bash
TEST_DEVICE=/dev/null BLOCK_DEVICE=/dev/mmcblk2 source ./dev.test
```

# Performance test
```
BLOCK_DEVICE=${TEST_DEVICE} ./bdp.test
```

# Integrity test
All the md5sup patterns must be the same
* Test first 128 mega of the media
```
LOOPS=128 PATTERN_SIZE=2048 BLOCK_DEVICE=${TEST_DEVICE} ./bdi.test
```
* Test the entire media with the pattern size of 16 mega
```
PATTERN_SIZE=$((2048*16)) BLOCK_DEVICE=${TEST_DEVICE} ./bdi.test
```

# Clean up
* Remove the created `${TEST_DEVICE}`
```bash
TEST_DEVICE=${TEST_DEVICE} BLOCK_DEVICE=/dev/mmcblk2 source ./dev.test
```
