Carbon
======

A simple extension for [Time](https://golang.org/pkg/time/#Time) based on PHP's [Carbon](http://carbon.nesbot.com) library.

__Features:__

* [Time](https://golang.org/pkg/time/#Time) is embedded into Carbon (provides access to all of [Time](https://golang.org/pkg/time/#Time)'s functionality)
* Supports addition and subtraction of dates
* Provides methods to compare dates
* Supports date formatting in common formats
* Easily calculate difference between dates

__To do:__

* Implement all localization features as in Carbon
* As this port is from PHP, there're parts that aren't that idiomatic, and therefore should be improved.

## Getting started
Install Carbon:
```
go get github.com/uniplaces/carbon
```

Add to your imports to start using Carbon
```go
import "github.com/uniplaces/carbon"
```

## Examples
A simple example to get you started:
```go
package main

import (
	"fmt"
	"time"

	"github.com/uniplaces/carbon"
)

func main() {
	fmt.Printf("Right now is %s\n", carbon.Now().DateTimeString())

	today, _ := carbon.NowInLocation("America/Vancouver")
	fmt.Printf("Right now in Vancouver is %s\n", today)

	fmt.Printf("Tomorrow is %s\n", carbon.Now().AddDay())
	fmt.Printf("Last week is %s\n", carbon.Now().SubWeek())

	nextOlmypics, _ := carbon.CreateFromDate(2016, time.August, 5, "Europe/London")
	nextOlmypics = nextOlmypics.AddYears(4)
	fmt.Printf("Next olympics are in %d\n", nextOlmypics.Year())

	if carbon.Now().IsWeekend() {
		fmt.Printf("Party time!")
	}
}
```

You can also check the `examples/` folder for more examples.

## Contributing
Please feel free to make suggestions, create issues, fork the repository and send pull requests!

## Licence
Copyright 2016 UNIPLACES

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

  http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
