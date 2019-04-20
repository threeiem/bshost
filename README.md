# Bash Scripts, the "BS" (bin/)

This is the location of the helper bash scripts (The BS in bshost).
You must sudo as root to run these because of file permissions with the apache server (deal with it).

## Archive (bin/archive)

Command that archives performs a tar and bzip2 on the files in the site.

```
bin/archive
```

### Parallel Bzip2

BSHost can use parallel bzip2 `pbzip` and bunzip `pbunzip` if they are installed.

```
sudo apt-get install pbzip2
```

## Backup (bin/backup) 

Command that dumps the database and tars everything up. 
**Only the most recent database dump is included.**
Remove `archive/db` from the exclude array in `host.conf` to backup old database dumps.
The `--verify` flag will check the archive file when it is complete.

```
bin/backup [--verify]
```

## Maria DB Dump (bin/dbdump)

Command that dumps the database to `archive/db/`.
These files are excluded by default, but the most recent is saved with `bin/archive`.
Returns the database backup filename when successful. 

```
bin/dbdump
```

## BS Host Setup

Command for setting up host and generating the host.conf file.

```
bin/setup
```



# Archive (archive/)

This is the location of the back-up files. Often before updates it's important to back that shit up.
This is the location of the archived artifacts from the site.

```
archive/
```

## Maria DB Archive

This is the location of the Maria DB database dump files.

```
archive/db/
```

## Tar File Archive

Tar archive files that are bzip2 files created by bshost are stored here.

```
archive/tar/
```

# Operating System Specific

## Debian 9

To help get going quickly there are install scripts to load a VPS, Respbian, Ubuntu, etc. with a LAMP stack (Linux, Apache2, MariaDB, PHP).
This is the script from reading countless how-to articles and examples.

```
sudo bin/install-debian-lamp
```

# Adding a Apache 2 virtual host 

To add a new virtual host use the setup script to begin a new host/vanity host layout.

```
sudo bin/setup 
```
