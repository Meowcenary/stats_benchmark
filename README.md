## stats_benchmark
This project provides tests and benchmarks of the Go library "stats" using the
data set Anscombe's quartet. It includes benchmarks of the same operations in
Python and R for comparison.

#### Installation and Dependencies
This project can be cloned through git with the following command:
```
git clone https://github.com/Meowcenary/stats_benchmark.git
```

In order to run the Python and R benchmarks you will need to install Python
3.7.11 and R 4.3.1. Additional dependencies for Python can be installed from
within the `anscombe_quartet_benchmark_py/` with:
`pip install -r requirements.txt`.

#### Running the Tests
The tests for the stats package can be viewed in in `stats_test.go`. The tests
can be run From the root directory of the project with `go test`

#### Running Benchmarks
Go benchmarks, which are included alongside the tests in `stats_test.go`, can be
run from the root directory of the project with `go test -bench=.`

The Python benchmarks can be run by switching to the directory
`anscombe_quartet_benchmark_py/`, installing dependencies from requirements.txt
(if you have not already done so), and finally running the script with
`python3 anscombe_quartet_benchmark.py`

The R benchmarks can be run by switching to the directory
`anscombe_quartet_benchmark_r/` and running the script with
`Rscript anscombe_quartet_benchmark.R`

## Comparing Go, Python, and R
#### Statistical Calculation
The Go library "stats" calculates linear regression coeffcients, intercepts, and
gradients for the data set "Anscombe's quartet" that align with the output from
the provided Python and R scripts. The tests and data can be viewed within
`stats_test.go`.

#### Benchmarks
Each script was benchmarked ten times with the fastest, slowest, and average
time recorded below.

The Go "stats" library had an average run time of 0.0000025 ns with the slowest
time at 0.0000029 ns and the fastest time at 0.0000020 ns.

The Python script had an average run time of 5.838 ns with the slowest time at
6.01 ns and the fastest time at 5.69 ns.

Finally, the R script had an average run time of 19190070 ns with the slowest
time at 20943880 ns and the fastest time at 18280030 ns.

These comparisons are from relatively small data sets and at scale the gap
between Go's run time versus both Python and R will only widen.

#### Other Potential Concerns
One of the most common concerns with migrating from languages like Python or R
to Go is the learning curve of Go's syntax, best practices, and tools. While Go
can be intimidating to look at compared to the syntax of Python or R, the
relatively small language specification and philosophy of having a single
solution to a problem leads to simple solutions that can be easily understood
even with little experience in the language. There are also many books written
on learning Go and thorough documentation that reduce the learning curve through
examples. Regarding tooling, Go's installation includes standard tools for
packaging, testing, and linting. By providing a standard out of the box there is
no need to look for external tools to handle these common tasks which is
convenient, removes the need to argue for one tool versus another, and avoids
adding external dependencies.

Another common concern with migrating programming languages is finding
replacements for libraries. The library "stats" tested in this repository with
Go's standard packages provides everything needed to produce the output from the
Python and R scripts. Though R does not require additional libraries, Go only
require one while Python requires three. While R has the functionality built in,
the run time is significantly slower. With the expectation that large data sets
will need to be analyzed, efficiency is the main priority and the cost of a
single dependency is outweighed by Go's superior efficiency.

Based on the efficiency, small language specification, readily available
learning materials, and testing of the stats library it is my recommendation
to use the Go programming language for future development.
