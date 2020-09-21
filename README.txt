/*/// A Python module implemented in Rust.*/
//#[pymodule]
//fn string_sum(_py: Python, m: &PyModule) -> PyResult<()> {
//m.add_function(wrap_pyfunction!(sum_as_string, m)?)?;

//Ok(())
/*}*/

The code above does not work.
The code is available in src/lib.rs
The .cargo/config overrides the global cargo config. In this case the flags are needed
to compile the bindings correctly using only cargo build
To build, do:
$ cargo build --release
$ maturin develop (remember to have virtual env  with python 3.8 installed and running)

The name of the lib and the name of the module, must be the same (in this case, string_sum)  in order to the import to work.
For that check Cargo.toml

For more info: https://depth-first.com/articles/2020/08/10/python-extensions-in-pure-rust-with-pyo3/

