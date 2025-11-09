all-inkl for [`libdns`](https://github.com/libdns/libdns)
=======================

[![Go Reference](https://pkg.go.dev/badge/test.svg)](https://pkg.go.dev/github.com/libdns/TODO:PROVIDER_NAME)

This package implements the [libdns interfaces](https://github.com/libdns/libdns) for all-inkl, allowing you to manage DNS records.

# Authentication
To authenticate you need to supply your KAS-Username and KAS-Password to the Provider.

# Example
```go
package main

import (
    "context"
    "fmt"
    "log"

    "github.com/libdns/libdns"
    "github.com/ljelschen/libdns-all-inkl"
)


func main() {
	provider := allinkl.Provider{
        Username: "your-kas-username",
        Password: "your-kas-password",
	}

	records, err  := provider.GetRecords(context.TODO(), "example.com.")
	if err != nil {
		fmt.Println(err.Error())    
	}

	for _, record := range records {
		fmt.Printf("%s %v %s %s\n", record.Name, record.TTL.Seconds(), record.Type, record.Value)
	}
}
```

# License
MIT License

Copyright (c) 2025 Lars Jelschen

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.