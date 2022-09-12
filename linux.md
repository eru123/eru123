### Clear cache
To free pagecache:
```bash
echo 1 > /proc/sys/vm/drop_caches
```

To free dentries and inodes:
```bash
echo 2 > /proc/sys/vm/drop_caches
```

To free pagecache, dentries and inodes:
```bash
echo 3 > /proc/sys/vm/drop_caches
```

OR
```bash
free && sync && echo 3 > /proc/sys/vm/drop_caches && free
```
