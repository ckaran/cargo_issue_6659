# cargo_issue_6659
This repository is for [cargo issue 6659](https://github.com/rust-lang/cargo/issues/6659).
Do not use this in production.

To turn on or off the error, edit the line marked in the `[lib]` section of the
`Cargo.toml` as it says.  As the file is currently, running `cargo -vvv test`
will result in something similar to the following:

```
   Compiling cargo_issue_6659 v0.1.0 (/home/cfkaran2/Desktop/cargo_issue_6659)
     Running `rustc --edition=2018 --crate-name tester tests/tester.rs --color always --emit=dep-info,link -C debuginfo=2 --test -C metadata=0525a91fc572753f -C extra-filename=-0525a91fc572753f --out-dir /home/cfkaran2/Desktop/cargo_issue_6659/target/debug/deps -C incremental=/home/cfkaran2/Desktop/cargo_issue_6659/target/debug/incremental -L dependency=/home/cfkaran2/Desktop/cargo_issue_6659/target/debug/deps`
     Running `rustc --edition=2018 --crate-name cargo_issue_6659 src/lib.rs --color always --emit=dep-info,link -C debuginfo=2 --test -C metadata=b9fa70b838dfddae -C extra-filename=-b9fa70b838dfddae --out-dir /home/cfkaran2/Desktop/cargo_issue_6659/target/debug/deps -C incremental=/home/cfkaran2/Desktop/cargo_issue_6659/target/debug/incremental -L dependency=/home/cfkaran2/Desktop/cargo_issue_6659/target/debug/deps`
error[E0463]: can't find crate for `rustc_issue_report_cdylib`
 --> tests/tester.rs:1:1
  |
1 | extern crate rustc_issue_report_cdylib;
  | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^ can't find crate

error: aborting due to previous error

For more information about this error, try `rustc --explain E0463`.
error: Could not compile `cargo_issue_6659`.

Caused by:
  process didn't exit successfully: `rustc --edition=2018 --crate-name tester tests/tester.rs --color always --emit=dep-info,link -C debuginfo=2 --test -C metadata=0525a91fc572753f -C extra-filename=-0525a91fc572753f --out-dir /home/cfkaran2/Desktop/cargo_issue_6659/target/debug/deps -C incremental=/home/cfkaran2/Desktop/cargo_issue_6659/target/debug/incremental -L dependency=/home/cfkaran2/Desktop/cargo_issue_6659/target/debug/deps` (exit code: 1)
warning: build failed, waiting for other jobs to finish...
error: build failed
```

# Meta information

```
$ cargo -V -vvv
cargo 1.32.0 (8610973aa 2019-01-02)
release: 1.32.0
commit-hash: 8610973aaf48615ba7dc9a38a9a2795ba6f36a31
commit-date: 2019-01-02
$ rustc -Vv
rustc 1.32.0 (9fda7c223 2019-01-16)
binary: rustc
commit-hash: 9fda7c2237db910e41d6a712e9a2139b352e558b
commit-date: 2019-01-16
host: x86_64-unknown-linux-gnu
release: 1.32.0
LLVM version: 8.0
$ uname -a
Linux EMANE 4.15.0-45-generic #48-Ubuntu SMP Tue Jan 29 16:28:13 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
$ lsb_release --all
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:    18.04
Codename:   bionic
```
