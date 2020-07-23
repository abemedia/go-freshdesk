# Freshdesk Client for Go

[![GoDoc](https://godoc.org/github.com/abemedia/go-freshdesk?status.png)](https://godoc.org/github.com/abemedia/go-freshdesk)

```go
package main

import (
	"log"

	"github.com/abemedia/go-freshdesk"
)

func main() {
	client, err := freshdesk.NewClient("your-domain", "your-api-key")
	if err != nil {
		log.Fatalf("Could not create client: %s", err)
	}

	ticket := &freshdesk.Ticket{
		Email:       "email@example.com",
		Name:        "your name",
		Subject:     "this is a test",
		Type:        "Question",
		Description: "the content of the ticket would go here",
		Status:      freshdesk.Open,
		Priority:    freshdesk.Medium,
		Source:      freshdesk.Portal,
	}

	if _, err := client.Tickets().Create(ticket); err != nil {
		log.Fatalf("failed to create ticket: %s", err)
	}
}
```