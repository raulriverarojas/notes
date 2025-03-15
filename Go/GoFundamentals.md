# Go Language Notes

## Table of Contents
- [Go Routines](#go-routines)
- [Go Channels](#go-channels)
- [Go Interfaces](#go-interfaces)
- [Go Structs](#go-structs)
- [Methods in Go](#methods-in-go)
- [Generics in Go](#generics-in-go)
- [Error Handling](#error-handling)
- [Dependency Management](#dependency-management)
- [Glossary](#glossary)

## Go Routines

- Go concurrency units
- Very light, not processes or threads
- Syntax:

```go
go func() {
   // code
}()
```

- If `func()` is defined somewhere else, you can just put the `go` keyword in front of function call
- To wait until go routines are done, use wait groups

```go
// Manually add routines to waitgroup
wg.Add(n)
// Wait for completion
wg.Wait()
```

## Go Channels

- Channels are used for go routines to communicate with each other
- Sending & receiving on channels are blocking operations (unless buffered channel & has buffer space available)
- Syntax & creation:

```go
ch := make(ch type, buffer)   // buffered
ch := make(ch channeltype)    // unbuffered
```

- Send syntax:
```go
channelName <- value
```

- Receive syntax:
```go
receivedVal <- channelName
```

- Channels have lengths & capacity
- Buffered channels can temp hold # of values defined by buffer size
- Sending into this buffer space is non-blocking

## Go Interfaces

- Defines a set of methods that a type should implement
- Interfaces are useful abstractions

## Go Structs

- Custom type defs in Go
- Structs combine fields into a data type
- When structs initialized, fields set to zero values for field type unless specified in initialization
- Dot notation used to access struct fields both through struct & pointers to structs
- When init struct, you can pass values to fields by position in struct def or by name:

```go
struct { "field 1", "field 2" }
```

```go
struct {
   field1name: "field 1",
   field2name: "field 2"
}
```

## Methods in Go

- Methods can be def to structs
- To be part of a struct, a method needs to have a receiver in definition

```go
func (receiver structType) funcName(params) returnType {
   // code
}
```

- The receiver can also be a pointer to modify struct state

```go
func (*pointerRec structType) funcName(params) returnType {
   // code
}
```

## Generics in Go

- In Generics, an interface can also be a set of types
- Syntax:

```go
type Generic[T interface{}] interface {
   int|float64|string|...
}
```

## Error Handling

- Errors are treated as values & return them
- Stack trace and default behavior
- Drop-in packages provided for stack trace func
- Go has panic function for when you can't handle errors; not recommended
- We can guard against panic:
 - Inside a defer func()
 - We call the recover() func
 - It recover returns something, there was panic, otherwise no panic

## Dependency Management

- Go mod file declares dependencies, min version of go & module name
- Go mod tidy is a command to fix up go mod file

## Glossary

- **Go Routines**: Lightweight concurrency units in Go, similar to threads but managed by the Go runtime
- **Channels**: Communication mechanisms for Go routines to exchange data safely
- **Interfaces**: A type that defines a set of methods another type must implement
- **Structs**: Custom data types that group together variables under a single name
- **Methods**: Functions attached to a particular type (often structs)
- **Generics**: Feature allowing code to be written for multiple types while maintaining type safety
- **Receivers**: The parameter that appears between `func` keyword and the function name, binding the function to a type
- **Buffered channel**: A channel with storage capacity allowing non-blocking operations up to buffer limit
- **Wait groups**: A synchronization mechanism to wait for multiple goroutines to finish
- **Panic**: A runtime error that stops the normal flow of a goroutine
- **Recover**: A built-in function that regains control of a panicking goroutine
