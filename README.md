LinearFold: Linear-Time Prediction for RNA Secondary Structures
============================================

The source code of the LinearFold project, a linear-time RNA secondary structure prediction algorithm.

Paper:
LinearFold: Linear-Time Prediction of RNA Secondary Structures

Dezhong Deng, Kai Zhao, David Hendrix, David Mathews, Liang Huang

doi: https://doi.org/10.1101/263509

Our online web server is available at: http://linearfold.eecs.oregonstate.edu

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


#### To Run
The LinearFold parser can be run with:
```
linearfold -f sequence_file [-b beam_size] [-v]
```

1. -v switches LinearFold-C (by default) to LinearFold-V. 
2. The default beam_size is infinite.

For example:
#### Example Run
```
./linearfold -f ../testseq -b 100
```
