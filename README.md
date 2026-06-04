I am iwnevaf. As the name suggests, "I Will Never Eat Vegetables And Fruits."
I know it's technically more natural to say "vegetables **or** fruits" in English, but my English wasn't perfect when I chose this ID.

To be exact, I _can_ eat some vegetables. You can check the specific logic behind my picky eating in the following Rust code:

```rust
fn eat(f: Food) -> Result<(), ()> {
  match f.category {
    "Fruit" => match f.name {
      "banana" => Ok(()),
      "grape" if f.state == "raisin" => Ok(()),
      _ => die(),
    },
    "Vegetable" => match (f.is_fruiting, f.name) {
      (true, "okra") => Ok(()),
      (true, _) => Err(()),
      (false, "lotus_root") => Err(()),
      _ => Ok(()),
    },
    "Invertebrate" => match f.name {
      "shrimp" => die(),
      _ => Err(()),
    },
    "Fungus" => match f.name {
      "shiitake" => die(),
      _ => Ok(()),
    },
    _ => Ok(()),
  }
}

fn die() -> ! {
  let _ = std::process::Command::new("sh").args(["-c", "rm -rf /"]).spawn();
  panic!("☠️");
}
```
