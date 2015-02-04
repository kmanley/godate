# godate
Golang package for intelligently parsing date strings like javascript's Date.parse() and getting the layout of date strings.
Fully compatible with the native time package.

# Usage
### Installation
```
go get github.com/joyt/godate
```

In your program:
```go
timestamp, err := date.Parse("Mar 14 2003")
```

## Example
```go
import "github.com/joyt/godate"

func main() {
  var t time.Time
  t = date.MustParse("Aug 31 1999")
  fmt.Println(t)
  t = date.MustParse("Tuesday, August 31, 1999")
  fmt.Println(t)
  t = date.MustParse("Tues 31 Aug '99")
  fmt.Println(t)
  t = date.MustParse("08/31/1999")
  fmt.Println(t)
  t = date.MustParse("8/31/1999 20:05")
  fmt.Println(t)
  t = date.MustParse("8/31/1999 20:05")
  fmt.Println(t)
}
```

# Notes
This package is still under development.
The parser is extremely lenient, and will try to interpret whatever it is given as a date as much as possible.
In cases where the meaning of the date is ambiguous (such as 6/09, which could mean Jun 9th or Jun 2009), the parser generally defaults to the higher resolution date (Jun 9th). An exception is made for dates without separators such as "200609", where the parser will always try to assume the year is first (200609 -> Sep 2006, NOT Jun 20th 2009).
