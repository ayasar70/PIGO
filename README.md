# PIGO: a Parallel Graph Input and Output library

PIGO is a library built to assist you with common sparse graph or matrix
input, output, and preprocessing. It supports easily loading a variety of
graph formats rapidly in parallel, performing standard preprocessing, and
saving results and intermediate representations.

PIGO is built in C++ and its releases are single header-only files.  It is
designed to be simple to integrate into many projects.

## Quick Start Guide

First, download the PIGO release `pigo.hpp`. To compile a PIGO
application, you'll need to use OpenMP and ensure `pigo.hpp` is in
a directory where the compiler can find it.

Here we provide a simple example program. Create the file `example.cpp` in
the same directory as `pigo.hpp`. Add the following to it:

```C++
#include "pigo.hpp"
#include <iostream>
using namespace std;
using namespace pigo;
int main(int argc, char** argv) {
    if (argc != 1) {
    	cerr << "Usage: " << argv[0] << " filename" << endl;
    	return 1;
    }
    
    Graph g { argv[1] };
    cout << "number of vertices: " << g.n() << endl;
    cout << "number of edges: " << g.m() << endl;
    
    cout << "vertex 0's neighbors:\n";
    for (auto n : g.neighbors(0))
        cout << n << endl;
    return 0;
}
```

Finally, compile the program with
`g++ -O3 -o example example.cpp -fopenmp`.

You can now run the example program to print out the size of the graph and
the neighbors of vertex 0.

For example, create the file `toy.el`:

```
0 4
4 3
0 5
0 9
```

`./example toy.el` should now print:

```
number of vertices: 10
number of edges: 4
vertex 0's neighbors:
4
5
9
```

## Documentation

* [Python 3](https://www.python.org/downloads/)
* [Pip](https://pip.pypa.io/en/stable/installing/)
* [Doxygen](https://www.doxygen.nl/download.html)

Additionally run `pip install -r docs/requirements.txt` for python dependencies in the project root.

Now running `make docs` in build directory will create documentations under `build/docs/sphinx`

## Running Tests

Unit tests are controlled using CMake. To use them, you will need a modern
version of CMake. You can do the following: `cd build; cmake ..; ctest`.

## License

Please see [`LICENSE.md`](LICENSE.md) for the license.

## Contributors

* [Kasimir Gabert](https://kasimir.co)
* [Umit V. Catalyurek](https://cc.gatech.edu/~umit)

## Contact

For questions or support please either open an issue or contact
<tdalab@cc.gatech.edu>.
