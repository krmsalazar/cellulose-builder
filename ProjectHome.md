**`cellulose-builder`** readily enables one to build several cellulose polymorph's crystallites of arbitrary size and shape in XYZ and PDB formats. Those files can be used, for instance, as starting configuration files for molecular dynamics (MD) simulations of systems containing cellulose crystalline domains.

This program has originally been published  in the following paper. Please cite this paper in published work if `cellulose-builder` has been in any way useful to you:

[Thiago C. F. Gomes, Munir S. Skaf, Journal of Computational Chemistry 2012, Volume 33, Issue 14, pages 1338-1346. DOI: 10.1002/jcc.22959 ](http://onlinelibrary.wiley.com/doi/10.1002/jcc.22959/abstract)

That paper contains a thorough description of `cellulose-builder`'s capabilities, usage examples and figures, and is to be regarded as a major component of the program's documentation. Below, we provide a brief User Guide on the installation and usage of `cellulose-builder`.



# User Guide #

This program is written in the Bash programming language so it does not require compilation. It should run at the Bash prompt on any Linux Ubuntu and supposedly on any other Linux, POSIX-standard, Unix, Unix-like, or BSD operational system, or within the Cygwin environment on Windows systems.

## Download and Installation ##

You may download `cellulose-builder` [here](http://code.google.com/p/cellulose-builder/downloads/list) or from the [FTP mirror](ftp://ftp.iqm.unicamp.br/pub/cellulose-builder) at the [Institute of Chemistry](http://www.iqm.unicamp.br/) at the State University of Campinas ([UNICAMP](http://www.unicamp.br)). You may choose to download any one of the four archive files you'll find, their contents are identical. The only difference is in their compression protocols (`lzma`, `gzip`, `rar`, `zip`). After downloading the chosen archive and extracting its contents, you should have a directory named `cellulose-builder_month_year`, were _month_ and _year_ indicate the date of release.

### Installing Dependencies ###

Even though `cellulose-builder` does not require compilation, it depends on a few tools to work properly, among them:

  * Octave
  * VMD
  * psfgen

On most Linux systems, one can readily have [Octave](http://www.gnu.org/software/octave/) installed using `apt-get`, `synaptic`, `aptitude`, `yum` or equivalent package management software. On BSD systems, one can get Octave via FreeBSD Ports.

To get [VMD](http://www.ks.uiuc.edu/Research/vmd/) installed on your system, you must [download it](http://www.ks.uiuc.edu/Development/Download/download.cgi?PackageName=VMD) and follow instructions for installation. You don't have to build (compile) VMD from its source code, just get the binary (executable) that fits your operational system.

To obtain the [psfgen](http://www.ks.uiuc.edu/Research/vmd/plugins/psfgen/ug.pdf) executable, [download](http://www.ks.uiuc.edu/Development/Download/download.cgi?PackageName=NAMD) the compiled [NAMD](http://www.ks.uiuc.edu/Research/namd/) tarball that best fits your operational system (again, no need to build from source code), extract its contents and add the extracted directory to your PATH. Under that directory there must be the psfgen executable.

**It is never enough to stress that all dependencies' executables must be in your [PATH](http://en.wikipedia.org/wiki/PATH_(variable)).** ( There is no need for the `cellulose-builder` parent directory itself to be in the PATH, though. See Usage below.)

## Usage ##

Navigate to `cellulose-builder` parent directory,
```
cd cellulose-builder_month_year
```

and try running on a Bash shell prompt , for instance, the following command line

```
./cellulose-builder.sh fibril 5
```

if everything goes all right, you should get a directory named `crystal`, under which there
should be a `crystal.pdb` file. If you can load that PDB file on VMD with no errors,

```
vmd crystal/crystal.pdb
```

or on your favorite PDB structure viewing program, then `cellulose-builder` is probably running correctly on your system. If you cannot get there, please [report us](http://groups.google.com/group/cellulose-builder).

### Command line arguments ###

There are three different sets of command line `cellulose-builder` will accept:

  1. ` ./cellulose-builder <integer> <integer> <integer> `
  1. ` ./cellulose-builder fibril <integer> `
  1. ` ./cellulose-builder origin|center|monolayer <integer> <integer> `

The first set generates crystals we from now on denote as _parallelepiped_ crystals. Three integer numbers must be supplied by the user. They stand for the number of unit cell replications in each crystallographic direction, therefore the crystal size is explicitly set by the user. The first two integers must be greater than one whereas the last integer must be greater than zero.

The second set builds 36-chain-fibrils. One must provide the string `fibril` as first argument whilst providing an integer greater than zero as second argument, which stands for the number of cellobiosyl residues in each cellulose chain. Thus, the degree of polymerization of the resulting fibril can be directly controlled by the user via command line.

The third set delivers mono-layers of specific cellulose chain types. The user must type either `origin`, `center` or `monolayer` as first argument, followed by two integers greater than one. Those integers stand for the number of cellulose chains comprised in the mono-layer and the number of cellobiosyl residues in each chain, respectively.

### Input file (input.inp) ###

`cellulose-builder` supports several crystalline cellulose polymorphs, as well as special features regarding crystallite translational symmetry and periodic covalent bonding. All those properties can be controlled by editing the input file `input.inp`.

### Resulting files ###

After a successful run, `cellulose-builder` will generate under its own parent directory a subdirectory named `crystal`, within which there should be the following files:

  * crystal.pdb
  * crystal.psf
  * crystal.xyz
  * psfgen.sh
  * psfgen.log