/*/// A Python module implemented in Rust.*/
//#[pymodule]
//fn string_sum(_py: Python, m: &PyModule) -> PyResult<()> {
//m.add_function(wrap_pyfunction!(sum_as_string, m)?)?;

//Ok(())
/*}*/

The code above does not work.

The code is available in src/lib.rs
-----------------------------------------------------------------------------------------
# BUILD

The .cargo/config overrides the global cargo config. In this case the flags are needed
to compile the bindings correctly using only cargo build

To build with cargo, do:
$ cargo build --release (to build the lib and binaries to the target/release folder)
or
$ cargo build (to build the lib and binaries to the target/debug folder)

With the first 2 alternatives, in order to test the lib, you will have to change the name of libstring_sum.dylib to sum_string.so

Another option is to run, which also installs the lib automatically in the virtual env

The name of the lib and the name of the module, must be the same (in this case, string_sum)  in order to the import to work.
For that check Cargo.toml

$ maturin develop (remember to have virtual env  with python 3.8 installed and running)
-----------------------------------------------------------------------------------------
# RELEASE

To release as a python package, maturin is the easiest option. Just run:
$ maturin build

And the wheel will be created in target/wheels folder

The name of the lib and the name of the module, must be the same (in this case, string_sum)  in order to the import to work.
For that check Cargo.toml

-----------------------------------------------------------------------------------------
For more info: https://depth-first.com/articles/2020/08/10/python-extensions-in-pure-rust-with-pyo3/

