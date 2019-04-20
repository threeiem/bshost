# BSHost - Bash Script Hosting Support

## Bash Script, the "BS" (bin/)

This is the location of the helper bash scripts (The BS in bshost).
You must sudo as root to run these because of file permissions with the apache server (deal with it).

### Archive (bin/archive)

Command that archives performs a tar and bzip2 on the files in the site.

```
sudo bin/archive
```

### Backup (bin/backup) 

Command that dumps the database and tars everything up. 
**Only the most recent database dump is included.**
Remove `archive/db` from the exclude array in `host.conf` to backup old database dumps.
The `--verify` flag will check the archive file when it is complete.

```
sudo bin/backup [--verify]
```

### Maria DB Dump (bin/dbdump)

Command that dumps the database to `archive/db/`.
These files are excluded by default, but the most recent is saved with `bin/archive`.
Returns the database backup filename when successful. 

```
sudo bin/dbdump
```

### BS Host Setup

Command for setting up host and generating the host.conf file.
Setup does not require the `root` user.
```
bin/setup
```



## Archive (archive/)

This is the location of the back-up files. Often before updates it's important to back that shit up.
This is the location of the archived artifacts from the site.

```
archive/
```

### Maria DB Archive

This is the location of the Maria DB database dump files.

```
archive/db/
```

### Backup Tar File Archive

Tar archive files that are bzip2 files created by bshost are stored here.

```
archive/tar/
```

## Operating System Specific

### Debian 9

#### Install LAMP Stack (PHP 7.3)
To help get going quickly there are install scripts to load a VPS, Respbian, Ubuntu, etc. with a LAMP stack (Linux, Apache2, MariaDB, PHP).
This is the script from reading countless how-to articles and examples.

```
sudo bin/install-debian-lamp
```

#### Parallel Bzip2

BSHost can use parallel bzip2 `pbzip2` and bunzip2 `pbunzip2` if they are installed.

```
sudo apt-get install pbzip2
```

### CentOS 7

#### Parallel Bzip2

BSHost can use parallel bzip2 `pbzip2` and bunzip2 `pbunzip2` if they are installed.

```
sudo yum install pbzip2
```
