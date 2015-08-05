This project provides a tool to synchronize remote FTP and local directory trees in both directions. The tool is provided as a Python script (`ftpsync.py`) that can be useful for uploading new/modified files to a homepage host using FTP. The tool can also be used to download new/modified files (such as wiki pages) for backup or mirroring purposes.

In both usage cases, the tool requires write access to FTP server to
create .listing files that are used to accelerate the synchronization process.

## Download and installation ##

You can download the python script `ftpsync.py` from [here](https://ftpsync2d.googlecode.com/svn/trunk/ftpsync.py). For installation, just copy the file to a directory that is in the PATH environment variable and make it executable (eg `chmod +x ftpsync.py`).

## Usage ##

To learn about the options of the `ftpsync.py` script, run
```
sh> ftpsync.py --help
```
that will display
```
Usage: ftpsync.py [options] <remote path> <local path>

 ftpsync.py is tool to synchronize remote and local directory trees using FTP
protocol (see http://ftpsync2d.googlecode.com/ for updates). Both directions
are supported. Write access to FTP server is required.  To skip processing
remote directories that one does not have read or write access, use --skip
option. When a new file was added to FTP server by other means than using
ftpsync.py, use --listing to update .listing files.  Remote path must be given
in the following form: [ftp://][username[:password]@]hostname[<remote
directory>]

Options:
  --version             show program's version number and exit
  -h, --help            show this help message and exit
  -u, --upload          enable uploading files
  -d, --download        enable downloading files
  -s SKIP_PATH, --skip=SKIP_PATH
                        skip listing specified remote (absolute) path
  -l, --listing         update remote .listing files
  -r REMOVE_PATHS, --remove=REMOVE_PATHS
                        remove specified files and directories
```

For example, to syncronize remote directory `rdir` in the FTP server `ftp.example.com` with the local directory `ldir`, run
```
ftpsync.py ftp://ftp.example.com/rdir ldir --download
```
When username and password is required, the script will ask.
When there are files that are changed locally and should be uploaded, add
`--upload` option to the command line.

### Important note ###

Before using `ftpsync.py`, backing up data is highly recommended.

## Feedback ##

Bug reports and feature requests should be reported to [ftpsync2d issues](http://code.google.com/p/ftpsync2d/issues/).
For general discussion, usage questions and suggestions, please use [ftpsync2d mailing list](http://groups.google.com/group/ftpsync2d).