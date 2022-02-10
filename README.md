# puppeteer

[Replay](https://replay.io) enabled fork of the [Puppeteer](https://pptr.dev/) library.

## Overview

This is an alternative to Puppeteer that uses a replay enabled chromium where possible, simplifying installation and versioning when compared with configuring the standard Puppeteer library to use replay browsers directly.

## Installation

`npm i @recordreplay/puppeteer`

## Usage

Replace `puppeteer` with `@recordreplay/puppeteer` in require/import statements, and this library will be used instead.  On supported platforms (see below), replay enabled browsers will be used to make recordings and save them to disk.  After running any puppeteer scripts, use the [replay-recordings](https://www.npmjs.com/package/@recordreplay/recordings-cli) CLI tool to manage and upload the recordings.

## Supported Platforms

The replay enabled chromium is currently only supported on linux.
