```bash
exiftool -Comment="$(cat komentar.txt)" nama_file
```

### Jika tidak ingin membuat backup
```bash
exiftool -overwrite_original -Comment="$(cat komentar.txt)" nama_file
```

### Jika ingin sekaligus menyimpan output di folder lain:
```bash
exiftool -overwrite_original -Comment="$(cat komentar.txt)" nama_file -o /path/to/output/
```
