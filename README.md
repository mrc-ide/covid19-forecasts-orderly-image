# covid19-forecasts-orderly-image

[![Build status](https://badge.buildkite.com/0f1277f28c627a4d2e182b0191084533defb0e4e47c83bf2c6.svg?branch=main)](https://buildkite.com/mrc-ide/covid19-forecasts-orderly)

This is the docker container for [covid19-forecasts-orderly](https://github.com/mrc-ide/covid19-forecasts-orderly).

This repo is a fork of [`montagu-orderly`](https://github.com/vimc/montagu-orderly) with minor modifications

**Interaction with the server**.  These commands interact with the orderly server on the *same host* as you run it.  If you run these on your desktop they will not affect any other machine.

Make sure you have the most recent version of the container with with

Update the `covid19-forecasts-orderly` repo on the orderly volume

```
./pull_sources
```

Run orderly commands with

```
./orderly run <name>
./orderly list names
./orderly --help
```

etc.

Get a shell on the container with

```
./shell
```

## Building the image

The image is built on [Buildkite](https://buildkite.com/mrc-ide/covid19-forecasts-orderly-image)
