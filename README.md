# README

Illustrate https://github.com/rails/sprockets/issues/749 .

This repo has two branches:
  * `main`: vanilla installation
  * `sprockets_4_0_3`: sprockets pinned to 4.0.3 via gemfile.

To reproduce:
(initially, clone this repo `git clone https://github.com/econya/sprockets_digest_muncher`)

## Fail state (sprockets 4.1.1)

```bash
bundle
rails s
```

And visit
1. [`http://localhost:3000/assets/otherfile.txt`](http://localhost:3000/assets/otherfile.txt) -> should work
1. [`http://localhost:3000/assets/test.txt`](http://localhost:3000/assets/test.txt) -> should work
1. [`http://localhost:3000/assets/test-notafingerprint.txt`](http://localhost:3000/assets/test-notafingerprint.txt) -> should NOT work


## Success state (sprockets 4.0.3)

```bash
git checkout sprockets_4_0_3
bundle
rails s
```

And visit
1. [`http://localhost:3000/assets/otherfile.txt`](http://localhost:3000/assets/otherfile.txt) -> should work
1. [`http://localhost:3000/assets/test.txt`](http://localhost:3000/assets/test.txt) -> should work
1. [`http://localhost:3000/assets/test-notafingerprint.txt`](http://localhost:3000/assets/test-notafingerprint.txt) -> should work
