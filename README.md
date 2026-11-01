# Go Token Bucket Rate Limiter

A small, concurrency-safe in-memory token bucket. It permits a configured burst and replenishes tokens at a steady rate.

## Run tests

```bash
go test -race ./...
```

## Example

```go
bucket := limiter.New(10, 2) // burst of 10, refill at 2 tokens/second
if !bucket.Allow() {
    // Return HTTP 429 or defer the operation.
}
```

Import the package with `github.com/Servitor108/go-rate-limiter/limiter`.

## Engineering concepts

- Token bucket burst capacity and refill rate.
- Mutex-protected state safe for concurrent goroutines.
- Elapsed-time refill using Go's time package.
- Concurrency-focused tests.

This implementation is process-local. A distributed limit across multiple service instances requires shared coordination, such as Redis or an API gateway.
