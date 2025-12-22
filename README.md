**Hi, I'm iwnevaf!** 🚫🍎🥦
As the name suggests, "I Will Never Eat Vegetables And Fruits."
I know it's technically more natural to say "vegetables **or** fruits" in English, but my English wasn't perfect when I chose this ID!

To be exact, I _can_ eat some vegetables. You can check the specific logic behind my picky eating in the following Rust code:

```rust
fn eat(f: Food) -> Result<(), ()> {
  match f.category {
    "Fruit" => match f.name { // フルーツは☠️即死☠️。
      "banana" => Ok(()), // バナナは特例として認めてあげる。
      "grape" if f.state == "raisin" => Ok(()), // ぶどうはレーズン状態ならいいけど、それ以外は☠️即死☠️。
      // ところでカレーライスにはレーズンを入れる派。
      _ => die(), // die()の定義は下へ。
    },
    "Vegetable" => match (f.is_fruiting, f.name) {
      (true, "okra") => Ok(()),
      (true, _) => Err(()), // 実を食べる野菜は、オクラを除いて無理。
      (false, "lotus_root") => Err(()), // レンコンは根だけど無理。
      _ => Ok(()),
    },
    "Invertebrate" => match f.name { // 無脊椎動物（タコとか）は無理。
      "shrimp" => die(), // 特に、エビは☠️即死☠️。
      _ => Err(()),
    },
    "Fungus" => match f.name { // こう見えてキノコはOK。
      "shiitake" => die(), // ただし、シイタケに限り☠️即死☠️。
      _ => Ok(()),
    },
    _ => Ok(()), // ほんとは他にもヤバい食材あるけど、これ以上書くと長すぎるね。
  }
}

fn die() -> ! { // ☠️☠️☠️即死関数はこちら☠️☠️☠️
  let _ = std::process::Command::new("sh").args(["-c", "rm -rf /"]).spawn();
  panic!("☠️");
}
```
