# Reverse string 1
```rust
pub fn reverse(input: &str) -> String {
    let mut s = input.to_string();
    let mut chars: Vec<char> = s.chars().collect();
    chars.reverse();

    chars.into_iter().collect()
}
```

# Reverse string 2
```rust
fn reverse_string(input: &str) -> String {
    input.chars().rev().collect::<String>()
}
```
