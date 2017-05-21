# Go Binary Buildpack

Use Go Binary Buildpack if you need Heroku/Flynn (or any other similar PaaS) to build and deploy a Go binary.

1. Builds main.go located in `GO_INSTALL_PACKAGE_SPEC`, e.g. "github.com/path/to/project/root". `GO_INSTALL_PACKAGE_SPEC` must be set. (For more advanced use cases please open an issue/PR.)
2. Assumes that you have all your dependencies in `vendor`. Go Binary Buildpack does not run any package manager scripts.
3. Runs the `main` binary file.

Buildpack was based on https://github.com/heroku/heroku-buildpack-go and https://github.com/ryandotsmith/null-buildpack.

## Usage

Create a directory for your Heroku Golang app:

```bash
$ mkdir -p github.com/path/to/your/project
$ cd github.com/path/to/your/project
$ touch main.go

package main
import "fmt"
func main() {
    fmt.Println("hello world")
}
```

Push the app to Heroku and run our executable:

```bash
$ git init; git add .; git commit -am 'Initial commit'
$ heroku create --buildpack http://github.com/ernsheong/go-binary-buildpack.git
$ git push heroku master
hello world
```

For Flynn see https://flynn.io/docs/apps#buildpacks for Flynn instructions.
