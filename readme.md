# Warning: It is up to the user to provide a correct block device for testing.
# It BLOCK_DEVICE is not a block device, the tests exits with rc=2 silently

# Performance test
BLOCK_DEVICE=/dev/mmcblk2p2 ./bdp.test

# Integrity test
LOOPS=32 PATTERN_SIZE=8192 BLOCK_DEVICE=/mmcblk2p2 ./bdi.test

bdi.test result is all the patterns' md5sun are the same
