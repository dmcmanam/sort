## sort

A Multi-Pivot Quicksort implementation in Go. The algorithm is taken from the paper [Multi-Pivot Quicksort: Theory and Experiments](http://epubs.siam.org/doi/abs/10.1137/1.9781611973198.6)

### Usage

This package has the exact same API as the sort package in the standard library. Therefore, all you have to do is change your import from `"sort"` to `"github.com/dmcmanam/sort"` and everything else remains the same.

### Example

```go
// This is the same example as the standard library just mentioned here for convenience
package main

import (
    "fmt"
    "github.com/dmcmanam/sort"
)

type Person struct {
    Name string
    Age  int
}

func (p Person) String() string {
    return fmt.Sprintf("%s: %d", p.Name, p.Age)
}

// ByAge implements sort.Interface for []Person based on
// the Age field.
type ByAge []Person

func (a ByAge) Len() int           { return len(a) }
func (a ByAge) Swap(i, j int)      { a[i], a[j] = a[j], a[i] }
func (a ByAge) Less(i, j int) bool { return a[i].Age < a[j].Age }

func main() {
    people := []Person{
        {"Bob", 31},
        {"John", 42},
        {"Michael", 17},
        {"Jenny", 26},
    }

    fmt.Println(people)

    sort.Slice(people, func(i, j int) bool {
        return people[i].Age < people[j].Age
    })
    fmt.Println(people)

}
```

### Benchmarks

TBD




