# go-gpt-3-encoder

Go BPE tokenizer (Encoder+Decoder) for GPT2 and GPT3.

## About

GPT2 and GPT3 use byte pair encoding to turn text into a series of integers to feed into the model. This is a Go implementation of OpenAI's original Python encoder/decoder which can be found [here](https://github.com/openai/gpt-2/blob/master/src/encoder.py).

This code was inspired by [Javascript implementation](https://github.com/latitudegames/GPT-3-Encoder) and partially generated by OpenAI himself!

## About this fork
This is only a version that fixes the import problem and supports multibyte characters, so you can use this repository's version temporarily until the original repository is fixed or supported.

## Install

```bash
go get github.com/GanymedeNil/go-gpt-3-encoder
```

## Usage

```go
import tokenizer "github.com/GanymedeNil/go-gpt-3-encoder"

encoder, err := tokenizer.NewEncoder()
if err != nil {
    log.Fatal(err)
}

str := "This is an example sentence to try encoding out on!"

encoded, err := encoder.Encode(str)
if err != nil {
    log.Fatal(err)
}

fmt.Println("We can look at each token and what it represents:")
for _, token := range encoded {
  fmt.Printf("%s -- %s\n", token, encoder.Decode([]int{token}))
}

decoded := encoder.Decode(encoded)
fmt.Printf("We can decode it back into: %s\n", decoded)
```

## Contribute

Some corner cases are not covered by this library. See `@TODO` in tests.
