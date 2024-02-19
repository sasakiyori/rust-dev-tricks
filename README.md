# rust-dev-tricks

Tricks for rust coding.

## Insert value into hashmap if not exists

```rust
fn insert_value_info_hashmap_if_not_exists() {
    let mut m = HashMap::new();
    m.insert(1, 1);

    // Not so graceful
    if !m.contains_key(&2) {
        m.insert(2, 2);
    }

    // Graceful and even can get the ref of value
    // Useful when value is a complicated struct
    let x: &mut i32 = m.entry(3).or_insert(3);
    let y: &mut i32 = m.entry(4).or_insert_with(|| 4);
    let z: &mut i32 = m.entry(5).or_insert_with_key(|key| {
        println!("{key}");
        5
    });
}
```
