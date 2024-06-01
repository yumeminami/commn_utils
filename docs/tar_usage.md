## TAR USAGE


### 1. Create a tar archive

```bash
tar -cvf archive.tar directory_or_file
```

-c : Create a new .tar archive file.
-v : Verbose, show the progress of the archive creation.
-f : File name type of the archive file.

### 2. Create a tar archive with gzip compression

```bash
tar -czvf archive.tar.gz directory_or_file
```

-z : Compress the archive file with gzip compression.

### 3. Extract a tar archive

```bash
tar -xvf archive.tar
```

-x : Extract the archive file.
-v : Verbose, show the progress of the archive extraction.
-f : File name type of the archive file.

### 4. Extract a tar archive with gzip compression

```bash
tar -xzvf archive.tar.gz
```

-z : Decompress the archive file with gzip compression.

### 5. Extract a tar archive to a specific directory

```bash
tar -xvf archive.tar -C /path/to/directory
```

-C : Extract the archive file to the specified directory.