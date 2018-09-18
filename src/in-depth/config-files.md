# Using config files

Dealing with configurations can be annoying
especially if you support multiple operating systems
which all have their own places
for short and long-term files.

There are multiple solutions to this,
some being more low-level than others.

The easiest to use crate is `confy`
which asks you for the name of your application
and requires you to specify the config layout
via a `struct` (that is `Serialize`, `Deserialize`)
and it will figure out the rest!

```rust
#[derive(Debug, Serialize, Deserialize)]
struct MyConfig {
    name: String,
    comfy: bool,
    foo: i64,
}

fn main() -> Result<(), io::Error> {
    let cfg: ConfyConfig = confy::load("my_app")?;
    println!("{:#?}", cfg);
    Ok(())
}
```

This is incredibly easy to use
for which you of course surrender configurability.
But if a simple config is all you want,
this crate might be for you!

## Configuration environments

**TODO**

1. Evaluate crates that exist
2. Cli-args + multiple configs + env variables
3. Can `configure` do all this? Is there a nice wrapper around it?