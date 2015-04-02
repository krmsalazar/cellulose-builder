# Compression Methods #

There are several different [compression algorithms](https://en.wikipedia.org/wiki/Compression_algorithm), and several software applications for compressing and decompressing data according to those algorithms, among them `lzma`, `gzip`, `rar`, `tar` and `zip`. Typically `tar` and `gzip` are available on Linux systems without need of installation. On most Linux systems one can have `lzma`, `rar` or `zip` installed using `apt-get`, `synaptic`, `aptitude`, `yum` or equivalent package management software.


# Extracting `cellulose-builder` #
After [downloading](http://code.google.com/p/cellulose-builder/downloads/list) one of the four `cellulose-builder` archive files available, navigate into the directory that contains it, for instance
```
cd Downloads
```
and extract according to the instructions you will find below.
If you wish to have `cellulose-builder`'s parent directory in a different location in your directory tree you may move the archive file to that location before extracting it, or you may extract first and then move the extracted directory, it doesn't matter which you do first.
Depending on which archive file you choose to download you will need different command lines to extract it, as exemplified below.
<a href='Hidden comment: 
#Navigate into the directory containing the cellulose-builder archive file you #have downloaded and type the appropriate commands according to the archive file
#format
'></a>

## .tar.gz ##
```
tar -zxvf cellulose-builder_month_year.tar.gz
```

## .tar.lzma ##
Install `lzma`, then
```
unlzma cellulose_builder_month_year.tar.lzma
tar -xvf cellulose_builder_month_year.tar
```

## .rar ##
Install `rar`, then
```
rar x cellulose_builder_month_year.rar
```

## .zip ##
For this you will need `zip`'s companion program `unzip`.
```
unzip cellulose_builder_month_year.zip
```

> After extracting `cellulose-builder`'s directory from its archive file, follow
> the [User Guide](http://code.google.com/p/cellulose-builder/#User_Guide) to install
> dependencies.