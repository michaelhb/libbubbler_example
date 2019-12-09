An basic example of how to link against BubbleProfiler from an external code, and call the API to caluclate bounce solutions. 

Instructions for use:
1. Install BubbleProfiler - usual procedure from BubbleProfiler directory:
 - mkdir build/
 - cd build/
 - cmake ..
 - make 
 - sudo make install

2. Build this example
 - navigate to source directory
 - mkdir build/
 - cd build/
 - cmake .. && make

If successful, the executable file bin/gaussian will be created. Test it with:

 gaussian --gamma 1.7 --lambda 5 --n_fields 2

The expected output is:

Alpha: 0.518419
Action: 12338.7  

Note 1: This is "old-style" CMake, i.e. I have provided an example Findlibbubbler.cmake file in the cmake/ directory. It is likely we will refactor the build system for v2 to take advantage of the exported targets / transitive dependency managment / etc provided by modern CMake. The intention in providing this example was to show how the existing version of BubbleProfiler can be used in external codes, with the caveat that users will likely have to modify their build systems when version 2 is released.

Note 2: The provided example uses the "perturbative" algorithm. This algorithm is mainly used for N > 1 field potentials. Users who are only interested in solving 1D problems will probably want to use the "shooting" algorithm, which is faster but doesn't work for more than one field. For an example of the API calls required to do this, see e.g. examples/logarithmic in BubbleProfiler. 

Please direct any questions about this example to me: Michael.Bardsley@monash.edu
