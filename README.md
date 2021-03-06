# hacking suite (hack/cpp)

## Motivation

Fast and simple hacking shouldn't require a complex set of tools. However, even such simple programs, when done systematically, might benefit from a basic conventional framework. This suite's aim is to provide basic functionality to anyone wishing to develop simple programs, such as for programming contests, that work on standard i/o.

This template was made with c++ in mind, but I believe it can be easily adapted to any other programming language that supports standard i/o and a lightweight test framework.

## Features

**automated test** against custom inputs. The *lib/run.sh* script looks at all inputs in the *input/* folder and tests the program against it, putting the output in the *output/* folder. It also measures execution time(in %s.%ms format) and prints the difference between the actual output and the target one, which is located in the *target* folder. The many-files input style is ideal for programs that take one input at a time, and can be used to organize by theme the inputs for programs that can take multiple ones(some example themes are already provided). Corresponding files in all these folders should have the same name. Empty files are ignored.

**automated build** through a *makefile*. This simplifies the up-arrow compile and run workflow to a make command. A makefile is also useful to simplify compilation within command-line debuggers, such as gdb. Make targets include: clean(n), compile(c), test(t), run(r) and all(a).

**automated unit test** through the *tests\_main.cpp* file. Choose your fit: there's a raw template to write tests in pure c++ with your own prints, [unit.hpp from sweet.hpp](https://github.com/burner/sweet.hpp) and [tinytest](https://github.com/ccosmin/tinytest). This format is easily extended to any light test framework and I'd love to hear about alternatives to include here. **WARNING** This functionality is implemented by using a sed script that extracts the main function out of your *main.cpp* file and puts the result in the *src/functions.cpp* file. The *test\_main.cpp* must include this functions.cpp file to see any implemented method without conflict with your main program's main function. It is imperative that you have a well-formed *int main* that ends in a line containing only a closing bracket *}* and that no line before this is composed like so(just properly indent your code). I wish this was not the case, but it is the best I could do so far. I also think that maybe the *functions.cpp* file should be included elsewhere, but none of the other folders match and I feel dumb creating one just for it. :P

**source and test templates** with standard functionality. These should save up some time and energy when starting a new hack.

## Project Structure


>.

>├── target/

>├── input/

>├── lib/

>│      ├── extract\_functions.sh

>│      ├── run.sh

>│      ├── tinytest.h

>│      └── unit.hpp

>├── LICENSE

>├── makefile

>├── output/

>├── README.md

>└── src/

>        ├── main.cpp

>        ├── test\_main.cpp

>        ├── tiny\_test\_main.cpp

>        └── unit\_test\_main.cpp
