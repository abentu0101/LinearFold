LinearFold: Linear-Time Prediction for RNA Secondary Structures
============================================

This repository contains the C++ source code for the LinearFold project,
the first linear-time prediction algorithm/software for RNA secondary structures.

Preprint:
LinearFold: Linear-Time Prediction of RNA Secondary Structures

Dezhong Deng, Kai Zhao, David Hendrix, David Mathews, and Liang Huang*

*corresponding author

doi: https://doi.org/10.1101/263509

Web server: http://linearfold.eecs.oregonstate.edu

#### To Compile
LinearFold can be compiled with ```cmake``` with following commands:

```
mkdir build
cd build
cmake ..
make linearfold
```

Note that there are two external libraries stated in ```CMakeLists.txt``` file:

1. ```-lprofiler``` is from Google Performance Tools, and is used to profile the parser, which is turned __off__ by default.
2. ```-ltcmalloc``` is also from Google Performance Tools, which replaces the default ```malloc``` from ```glibc``` and can bring ~5% speedup.

A minimum gcc version of 4.9.0 is required. 

#### To Run
The LinearFold parser can be run with:
```
echo "SEQUENCE" | linearfold [OPTIONS]

OR

cat SEQ_OR_FASTA_FILE | linearfold [OPTIONS]
```

Both FASTA format and pure-sequence format are supported for input. 

OPTIONS: 

> -b --beam_size

The beam size (default 100). Use 0 for infinite beam. 

> -V --Vienna

Switches LinearFold-C (by default) to LinearFold-V. 

> -v --verbose

Prints out energy of each loop in the structure . (default False)

> -s --simpleprint

The simplest output (two lines: sequence and structure) only. Can be used for pipe. (default False)

For example:
#### Example Run
```
cat ../testseq | ./linearfold 

echo "GGGCUCGUAGAUCAGCGGUAGAUCGCUUCCUUCGCAAGGAAGAGGCCCUGGGUUCAAAUCCCAGCGAGUCCACCA" | ./linearfold -b 20 -Vv

echo "GGGCUCGUAGAUCAGCGGUAGAUCGCUUCCUUCGCAAGGAAGAGGCCCUGGGUUCAAAUCCCAGCGAGUCCACCA" | ./linearfold -s
```
