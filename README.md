## [latex-rs](https://github.com/Michael-F-Bryan/latex-rs) and [tectonic](https://github.com/tectonic-typesetting/tectonic) together (on Windows with VSCode)

1. Install the needed tectonic [external dependencies](https://tectonic-typesetting.github.io/book/latest/howto/build-tectonic/cargo-vcpkg-dep-install.html)
2. Change the VCPKG_ROOT variable in `.vscode/settings.json` to point to your vcpkg installation
3. `cargo add tectonic --features "external-harfbuzz"`
4. `cargo add latex`
5. use `rust-analyzer.run` task to create a PDF file

Now there aren't even any intermediate `.tex` files created, and the output is a PDF file.

### Reasoning

When running `cargo build` or `cargo run` through the command line or a custom task cargo always rebuilts the entire project on the `cargo check` from the rust-analyzer (even if nothing has changed). I assume this has to do with the `RUSTFLAGS` environment variable even if it is set to the same value in both cases.

This is not the case when using the `rust-analyzer.run` task.

The above described setup seems to work for me - maybe it helps someone else too.
