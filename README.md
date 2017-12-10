# semaphoreci-gcc-arm-test

[![Build Status](https://semaphoreci.com/api/v1/karlding/semaphoreci-gcc-arm-test/branches/master/shields_badge.svg)](https://semaphoreci.com/karlding/semaphoreci-gcc-arm-test)

Test Semaphore CI integration with GCC ARM projects using Throw The Switch's [Unity](http://www.throwtheswitch.org/unity/) unit-testing framework for C unit tests.

This is a test repository that demonstrates a proof-of-concept for the [University of Waterloo](https://uwaterloo.ca/)'s [Midnight Sun Solar Rayce Car team's](http://www.uwmidsun.com/) software team (our GitHub organization can be found at [uw-midsun](https://github.com/uw-midsun)).

## Usage
To use, just enable the Semaphore CI integration for your project, and then modify the setup scripts under **Build Settings** as appropriate. Currently, the configuration has Semaphore:

1. Install dependencies from the ppas
2. Build GNU Make from source

After cloning the project repository, it updates all the submodules using

```bash
git submodule update --init --recursive
```

And then builds a project:

```bash
make build_all PLATFORM=$PLATFORM
```

Our ``Makefile`` is set up such that it returns the exit code in ``$?``. So Semaphore CI will detect that ``make`` failed, and will report the appropriate error code.
