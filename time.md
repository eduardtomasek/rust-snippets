# Add seconds
```rust
use time::PrimitiveDateTime as DateTime;
use time::Duration;

// Returns a DateTime one billion seconds after start.
pub fn after(start: DateTime) -> DateTime {
    start + Duration::seconds(1_000_000_000)
}
```

# Clock
```rust
use std::fmt;
use time::PrimitiveDateTime as DateTime;
use time::Duration;
use time::Time;
use time::Date;

pub struct Clock {
    time: DateTime
}

impl Clock {
    pub fn new(hours: i32, minutes: i32) -> Self {
        let pt = DateTime::new(Date::from_ordinal_date(2019,1).unwrap(), Time::from_hms(0,0,0).unwrap());
        Clock{time: pt + Duration::seconds((hours as i64 * 60 * 60) + (minutes as i64 * 60))}
    }

    pub fn add_minutes(&self, minutes: i32) -> Self {
        Clock{ time: self.time + Duration::seconds(minutes as i64 * 60)}
    }
}

impl fmt::Display for Clock {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        write!(f, "{:02}:{:02}", self.time.hour(), self.time.minute())
    }
}

impl fmt::Debug for Clock {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        write!(f, "{:02}:{:02}", self.time.hour(), self.time.minute())
    }
}

impl PartialEq for Clock {
    fn eq(&self, other: &Self) -> bool {
        // Define your custom equality logic here
        self.time.hour() == other.time.hour() && self.time.minute() == other.time.minute()
    }
}
```
