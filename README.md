[<img src="docs/images/cyclone-logo-04-header.png" alt="cyclone-scheme">](http://github.com/justinethier/cyclone)

Cyclone is a brand-new Scheme-to-C compiler that allows practical application development using R<sup>7</sup>RS Scheme. [Cheney on the MTA](http://www.pipeline.com/~hbaker1/CheneyMTA.html) is used by Cyclone's runtime to implement full tail recursion, continuations, and generational garbage collection. In addition, the Cheney on the MTA concept has been extended to allow execution of multiple native threads. An on-the-fly garbage collector is used to manage the second-generation heap and perform major collections without "stopping the world".

Cyclone is the first compiler written entirely in the latest R<sup>7</sup>RS Scheme language standard, with the intent to support as much of that language as possible.

Getting Started
---------------

1. To install Cyclone on your machine for the first time use [**cyclone-bootstrap**](https://github.com/justinethier/cyclone-bootstrap) to build a set of binaries. Instructions are provided for Linux, Mac, and Windows (via MSYS).

2. After installing you can run the `cyclone` command to compile a single Scheme file:

        $ cyclone examples/fac.scm
        $ examples/fac
        3628800
    
    And the `icyc` command to start an interactive interpreter:
    
        $ icyc
        
                      :@
                    @@@
                  @@@@:
                `@@@@@+
               .@@@+@@@      Cyclone
               @@     @@     An experimental Scheme compiler
              ,@             https://github.com/justinethier/cyclone
              '@
              .@
               @@     #@     (c) 2014 Justin Ethier
               `@@@#@@@.     Version 0.0.1 (Pre-release)
                #@@@@@
                +@@@+
                @@#
              `@.
        
        cyclone> (write 'hello-world)
        hello-world

   You can use [`rlwrap`](http://linux.die.net/man/1/rlwrap) to make the interpreter more friendly, EG: `rlwrap icyc`.

3. Read the documentation below for more information on how to use Cyclone.

Documentation
-------------

- The [User Manual](docs/User-Manual.md) covers in detail how to use Cyclone, and provides information and API documentation on the Scheme language features implemented by Cyclone.

- [Writing the Cyclone Scheme Compiler](docs/Writing-the-Cyclone-Scheme-Compiler-Revised-2017.md) provides high-level details on how the compiler was written and how it works.

- There is a [Development Guide](docs/Development.md) with instructions for common tasks when hacking on the compiler itself.

- Cyclone's [Garbage Collector](docs/Garbage-Collector.md) is documented at a high-level. This document includes details on extending Cheney on the MTA to support multiple stacks and fusing that approach with a tri-color marking collector.

- This [Benchmarks](http://ecraven.github.io/r7rs-benchmarks/benchmark.html) page by [ecraven](https://github.com/ecraven) compares the performance of Cyclone with other R<sup>7</sup>RS and R<sup>6</sup>RS Schemes using a common set of benchmarks.

- Finally, if you need another resource to start learning the Scheme language you may want to try a classic textbook such as [Structure and Interpretation of Computer Programs](https://mitpress.mit.edu/sicp/full-text/book/book.html).

Example Programs
----------------

Cyclone provides several example programs, including:

- [Tail Call Optimization](examples/tail-call-optimization.scm) - A simple example of Scheme tail call optimization; this program runs forever, calling into two mutually recursive functions.

- [Threading](examples/threading) - Various examples of multi-threaded programs.

- [Game of Life](examples/game-of-life) - The [Conway's game of life](https://en.wikipedia.org/wiki/Conway%27s_Game_of_Life) example program and libraries from R<sup>7</sup>RS.

- [Game of Life PNG Image Generator](examples/game-of-life-png) - A modified version of game of life that uses libpng to create an image of each iteration instead of writing it to console. This example also demonstrates basic usage of the C Foreign Function Interface (FFI).

- Finally, the largest program is the compiler itself. Most of the code is contained in a series of libraries which are used by [`cyclone.scm`](cyclone.scm) and [`icyc.scm`](icyc.scm) to create executables for Cyclone's compiler and interpreter.

License
-------
Copyright (C) 2014 [Justin Ethier](http://github.com/justinethier).

Cyclone is available under the [MIT license](http://www.opensource.org/licenses/mit-license.php).
