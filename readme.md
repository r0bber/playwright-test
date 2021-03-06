# playwright-test [![NPM Version](https://img.shields.io/npm/v/playwright-test.svg)](https://www.npmjs.com/package/playwright-test) [![NPM Downloads](https://img.shields.io/npm/dt/playwright-test.svg)](https://www.npmjs.com/package/playwright-test) [![NPM License](https://img.shields.io/npm/l/playwright-test.svg)](https://www.npmjs.com/package/playwright-test) ![tests](https://github.com/hugomrdias/playwright-test/workflows/tests/badge.svg)

> Run mocha, zora, uvu, tape and benchmark.js scripts inside real browsers with `playwright`.


## Install

```shell
$ npm install playwright-test
```

## Usage
```shell
$ playwright-test [files] [options]
# or 
$ pw-test [files] [options]

```
## Options

```shell
Description
    Run mocha, zora, uvu, tape and benchmark.js scripts inside real browsers with `playwright`.

  Usage
    $ playwright-test [files] [options]

  Options
    -r, --runner       Test runner. Options: mocha, tape, benchmark and zora.  (default mocha)
    -b, --browser      Browser to run tests. Options: chromium, firefox, webkit.  (default chromium)
    -m, --mode         Run mode. Options: main, worker.  (default main)
    -d, --debug        Debug mode, keeps browser window open.
    -w, --watch        Watch files for changes and re-run tests.
    -i, --incognito    Use incognito window to run tests.
    -e, --extension    Use extension background_page to run tests.
    --cov              Enable code coverage in istanbul format. Outputs '.nyc_output/out.json'.
    --before           Full path to a script to be loaded on a separate tab before the main script.
    --assets           Assets to be served by the http server.  (default process.cwd())
    --cwd              Current directory.  (default process.cwd())
    --extensions       File extensions allowed in the bundle.  (default js,cjs,mjs)
    -v, --version      Displays current version
    -h, --help         Displays this message


  Examples
    $ playwright-test test.js --runner tape
    $ playwright-test test --debug
    $ playwright-test "test/**/*.spec.js" --browser webkit --mode worker --incognito --debug

    $ playwright-test bench.js --runner benchmark
    # Uses benchmark.js to run your benchmark see playwright-test/mocks/benchmark.js for an example.

    $ playwright-test test --cov && npx nyc report --reporter=html
    # Enable code coverage in istanbul format which can be used by nyc.

    $ playwright-test "test/**/*.spec.js" --debug --before ./mocks/before.js
    # Run a script in a separate tab check ./mocks/before.js for an example.
    # Important: You need to call `self.PW_TEST.beforeEnd()` to start the main script.

  Runner Options
    All arguments passed to the cli not listed above will be fowarded to the runner.
    $ playwright-test test.js --runner mocha --bail --grep 'should fail'

    To send a `false` flag use --no-bail.
    Check https://mochajs.org/api/mocha for `mocha` options or `npx mocha --help`.

  Notes
    DEBUG env var filtering for 'debug' package logging will work as expected.
    $ DEBUG:app playwright-test test.js

    Do not let your shell expand globs, always wrap them.
    $ playwright-test "test/**" GOOD
    $ playwright-test test/** BAD
```

## Run in CI 
Check our CI config `.github/workflows/main.yml` and the playwright Github Action https://playwright.dev/#version=v1.5.2&path=docs%2Fci.md&q=github-actions


## License

MIT © [Hugo Dias](http://hugodias.me)
