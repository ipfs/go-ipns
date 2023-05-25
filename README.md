# go-ipns

> ipns record definitions

[![](https://img.shields.io/badge/made%20by-Protocol%20Labs-blue.svg?style=flat-square)](https://protocol.ai)
[![](https://img.shields.io/badge/project-IPFS-blue.svg?style=flat-square)](https://ipfs.tech/)
[![standard-readme compliant](https://img.shields.io/badge/standard--readme-OK-green.svg?style=flat-square)](https://github.com/RichardLitt/standard-readme)
[![GoDoc](https://godoc.org/github.com/ipfs/go-datastore?status.svg)](https://godoc.org/github.com/ipfs/go-ipns)


## ❗ This repo is no longer maintained.
👉 We highly recommend switching to the maintained version at https://github.com/ipfs/boxo/tree/main/ipns.
🏎️ Good news!  There is [tooling and documentation](https://github.com/ipfs/boxo#migrating-to-boxo) to expedite a switch in your repo. 

⚠️ If you continue using this repo, please note that security fixes will not be provided (unless someone steps in to maintain it).

📚 Learn more, including how to take the maintainership mantle or ask questions, [here](https://github.com/ipfs/boxo/wiki/Copied-or-Migrated-Repos-FAQ).


This package contains all of the components necessary to create, understand, and validate IPNS records. It does *not* publish or resolve those records. [Kubo](https://github.com/ipfs/kubo) uses this package internally to manipulate records.

## Usage

To create a new IPNS record:

```go
import (
	"time"

	ipns "github.com/ipfs/go-ipns"
	crypto "github.com/libp2p/go-libp2p-crypto"
)

// Generate a private key to sign the IPNS record with. Most of the time, 
// however, you'll want to retrieve an already-existing key from IPFS using the
// go-ipfs/core/coreapi CoreAPI.KeyAPI() interface.
privateKey, publicKey, err := crypto.GenerateKeyPair(crypto.RSA, 2048)
if err != nil {
  panic(err)
}

// Create an IPNS record that expires in one hour and points to the IPFS address
// /ipfs/Qme1knMqwt1hKZbc1BmQFmnm9f36nyQGwXxPGVpVJ9rMK5
ipnsRecord, err := ipns.Create(privateKey, []byte("/ipfs/Qme1knMqwt1hKZbc1BmQFmnm9f36nyQGwXxPGVpVJ9rMK5"), 0, time.Now().Add(1*time.Hour))
if err != nil {
	panic(err)
}
```

Once you have the record, you’ll need to use IPFS to *publish* it.

There are several other major operations you can do with `go-ipns`. Check out the [API docs](https://godoc.org/github.com/ipfs/go-ipns) or look at the tests in this repo for examples.

## Documentation

https://godoc.org/github.com/ipfs/go-ipns

### Want to hack on IPFS?

[![](https://cdn.rawgit.com/jbenet/contribute-ipfs-gif/master/img/contribute.gif)](https://github.com/ipfs/community/blob/master/CONTRIBUTING.md)

## License

Copyright (c) Protocol Labs, Inc. under the **MIT license**. See [LICENSE file](./LICENSE) for details.
