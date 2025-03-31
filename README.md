# stringEnum
 Go string enums generator. 

## Why
I often use sum types in TypeScript, and I want to bring the functionalities to Go:
 - Type-safe.
 - A same name can be used in multiple enums.
 - Support short strings (array) and long strings (key/value)
 - Easy-to-use

## Install
```shell
go install github.com/stanNthe5/stringenum@latest
```

## Generate Enums

In your Go project folder, create a file named `enums.yaml`.
Example:
```yaml
package: yourPackageName
output: enums.go
enums:
  font-size:
    - small
    - normal
  div-size:
    - small
    - normal
    - big
  colors:
    red: "#ff0000"
    green: "#00ff00"
```
And run
```shell
stringenum
```

A file named `enums.go` will be generated:
```go
type ColorsEnum interface {
	colors()
	String() string
}

type DivSizeEnum interface {
	divsize()
	String() string
}

type FontSizeEnum interface {
	fontsize()
	String() string
}
...
...
```

## Use the Enums

You can now use the Enums in your Go file:
```go
func fontSize(s FontSizeEnum) {
	fmt.Println(s.String())
}
func divSize(s DivSizeEnum) {
	fmt.Println(s.String())
}
func color(c ColorsEnum){
	fmt.Println(c.String())
}

func main() {
	fontSize(Small)
	divSize(Normal)
	color(Green)
}
```

