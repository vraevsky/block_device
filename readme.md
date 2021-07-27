|Warning| It is up to the user to provide a correct block device for testing.
|---|---|

|NOTE|It BLOCK_DEVICE is not a block device, the tests exits with rc=2 silently
|---|---|

# Performance test
```
BLOCK_DEVICE=/dev/mmcblk2p2 ./bdp.test
```

# Integrity test
All the md5sup patterns must be the same
* Test first 128 mega of the media
```
LOOPS=128 PATTERN_SIZE=2048 BLOCK_DEVICE=/dev/mmcblk2p2 ./bdi.test
```
* Test the entire media with the pattern size of 16M
```
PATTERN_SIZE=$((2048*16)) BLOCK_DEVICE=/dev/mmcblk2p2 ./bdi.test
```
