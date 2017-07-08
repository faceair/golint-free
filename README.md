From [`golint`](https://github.com/golang/lint/#purpose):
> We will not be adding pragmas or other knobs to suppress specific warnings, so do not expect or require code to be completely "lint-free".

`golint-free` is exactly like `golint` (it fork from golint) with the ability to suppress specific warning messages.

#### Install

`go get -u github.com/faceair/golint-free`

create `$GOPATH/.golint-free` to be a JSON with 1 fields:

- ignore
  > An array of strings used for matching golint warnings that you want ignored

Example warning:

    testfile:25:6: don't use underscores in Go names; func Test_input should be TestInput
    testfile:40:6: exported type MockWriter should have comment or be unexported

If I wanted both to be suppressed I would edit `.golint-free` to look like this:

    {
      "ignore": [
        "don't use underscores in Go names",
        "should have comment or be unexported"
      ]
    }

And it'll suppress warnings that match any lines you have.
