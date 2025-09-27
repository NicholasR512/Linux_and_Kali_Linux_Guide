## Purpose
Working with archives and compressed files is a must in both CTFs and real-world environments. Many files are shared in compressed formats to save space or bundle multiple files together. Knowing how to create, extract, and compress archives allows you to quickly work with data, whether you’re grabbing CTF challenge files, downloading logs, or handling backups.

## Core Commands
```bash
$ tar -cvf archive.tar file1.txt file2.txt
#Creates "archive.tar" Containing file1.txt and file2.txt | -c = create, -v = verbose, -f = filename

$ tar -xvf archive.tar
#Extracts the Contents of "archive.tar"

$ tar -czvf archive.tar.gz file1.txt file2.txt
#Creates a Gzipped Archive "archive.tar.gz" Containing file1.txt and file2.txt | -z = gzip compression

$ tar -xzvf archive.tar.gz
#Extracts a Gzipped Archive "archive.tar.gz"

$ gzip file.txt
#Compresses "file.txt" Into "file.txt.gz" and Removes Original File

$ gunzip file.txt.gz
#Decompresses "file.txt.gz" Back Into "file.txt"

$ zip archive.zip file1.txt file2.txt
#Creates a Zip Archive "archive.zip" Containing file1.txt and file2.txt

$ unzip archive.zip
#Extracts the Contents of "archive.zip"
```

!!! note "Archives & Compression Basics"  
	- `tar` is used for bundling multiple files together; `gzip` adds compression on top of it.  
	- `tar.gz` (aka “tarball”) is very common in Linux distributions.  
	- `zip/unzip` are more common in Windows environments but still widely used in Linux.  
	- Always check what type of archive you’re working with before extracting.

### [[Linux Basics#11 - Archives and Compression|Archives and Compression Commands]]