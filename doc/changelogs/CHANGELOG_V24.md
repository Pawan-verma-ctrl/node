# Node.js 24 ChangeLog

<!--lint disable maximum-line-length no-literal-urls prohibited-strings-->

<table>
<tr>
<th>Current</th>
</tr>
<tr>
<td>
<a href="#24.0.0">24.0.0</a><br/>
</td>
</tr>
</table>

* Other Versions
  * [23.x](CHANGELOG_V23.md)
  * [22.x](CHANGELOG_V22.md)
  * [21.x](CHANGELOG_V21.md)
  * [20.x](CHANGELOG_V20.md)
  * [19.x](CHANGELOG_V19.md)
  * [18.x](CHANGELOG_V18.md)
  * [17.x](CHANGELOG_V17.md)
  * [16.x](CHANGELOG_V16.md)
  * [15.x](CHANGELOG_V15.md)
  * [14.x](CHANGELOG_V14.md)
  * [13.x](CHANGELOG_V13.md)
  * [12.x](CHANGELOG_V12.md)
  * [11.x](CHANGELOG_V11.md)
  * [10.x](CHANGELOG_V10.md)
  * [9.x](CHANGELOG_V9.md)
  * [8.x](CHANGELOG_V8.md)
  * [7.x](CHANGELOG_V7.md)
  * [6.x](CHANGELOG_V6.md)
  * [5.x](CHANGELOG_V5.md)
  * [4.x](CHANGELOG_V4.md)
  * [0.12.x](CHANGELOG_V012.md)
  * [0.10.x](CHANGELOG_V010.md)
  * [io.js](CHANGELOG_IOJS.md)
  * [Archive](CHANGELOG_ARCHIVE.md)

<a id="24.0.0"></a>

## 2025-04-23, Version 24.0.0 (Current), @RafaelGSS and @juanarbol

We're excited to announce the release of Node.js 24! Highlights include
updating the V8 JavaScript engine to 13.4, upgrading npm to version 11.0.0,
making `AsyncLocalStorage` use `AsyncContextFrame` by default, exposing
`URLPattern` as a global, and many more improvements!

As a reminder, Node.js 24 will enter long-term support (LTS) in October,
but until then, it will be the "Current" release for the next six months.
We encourage you to explore the new features and benefits offered by this
latest release and evaluate their potential impact on your applications.

## Notable Changes

### V8 13.4

The V8 engine is updated to version 13.4, which includes several new
JavaScript features:

* [`Atomics.pause`](https://chromestatus.com/feature/5106098833719296) - A new API to pause execution for a specified duration
* [WebAssembly Memory64](https://chromestatus.com/feature/5070065734516736) - Support for 64-bit memory in WebAssembly
* [Explicit resource management](https://tc39.es/proposal-explicit-resource-management/) - The new 'using' and 'await using' declarations for deterministic resource cleanup
* [`Error.isError`](https://github.com/tc39/proposal-is-error) - A new static method to check if a value is an Error object

The V8 update was a contribution by Michaël Zasso in [#55014](https://github.com/nodejs/node/pull/55014).

### npm 11.0.0

Node.js 24 comes with npm 11.0.0, which includes several improvements and new
features. This update brings enhanced performance, improved security features,
and better compatibility with modern JavaScript packages.

The npm update was a contribution by the npm team in [#56274](https://github.com/nodejs/node/pull/56274).

### `AsyncLocalStorage` defaults to `AsyncContextFrame`

`AsyncLocalStorage` now uses `AsyncContextFrame` by default, which provides a
more efficient implementation of asynchronous context tracking.
This change improves performance and makes the API more robust for advanced
use cases.

This change was a contribution by Stephen Belanger in [#55552](https://github.com/nodejs/node/pull/55552).

### `URLPattern` as a Global

The [`URLPattern`](https://developer.mozilla.org/en-US/docs/Web/API/URLPattern)
API is now exposed on the global object, making it easier to use without
explicit imports. This API provides a powerful pattern matching system for URLs,
similar to how regular expressions work for strings.

This feature was a contribution by Jonas Badalič in [#56950](https://github.com/nodejs/node/pull/56950).

### Permission Model Improvements

The experimental Permission Model introduced in Node.js 20 has been improved,
and the flag has been changed from `--experimental-permission` to simply
`--permission`, indicating its increasing stability and readiness for broader
adoption.

This change was a contribution by Rafael Gonzaga in [#56240](https://github.com/nodejs/node/pull/56240).

### Test Runner Enhancements

The test runner module now automatically waits for subtests to finish,
eliminating the need to manually await test promises. This makes writing tests
more intuitive and reduces common errors related to unhandled promises.

The test runner improvements were contributions by Colin Ihrig in [#56664](https://github.com/nodejs/node/pull/56664).

### Undici 7.0.0

Node.js 24 includes Undici 7.0.0, which brings numerous improvements to the
HTTP client capabilities, including better performance and support for newer
HTTP features.

### Deprecations and Removals

Several APIs have been deprecated or removed in this release:

* Runtime deprecation of `url.parse()` - use the WHATWG URL API instead ([#55017](https://github.com/nodejs/node/pull/55017))
* Removal of deprecated `tls.createSecurePair` ([#57361](https://github.com/nodejs/node/pull/57361))
* Runtime deprecation of `SlowBuffer` ([#55175](https://github.com/nodejs/node/pull/55175))
* Runtime deprecation of instantiating REPL without new ([#54869](https://github.com/nodejs/node/pull/54869))
* Deprecation of using Zlib classes without `new` ([#55718](https://github.com/nodejs/node/pull/55718))
* Deprecation of passing `args` to `spawn` and `execFile` in child\_process ([#57199](https://github.com/nodejs/node/pull/57199))

### Semver-Major Commits

* \[[`0bff10a04c`](https://github.com/nodejs/node/commit/0bff10a04c)] - **(SEMVER-MAJOR)** _**Revert**_ "**assert,util**: revert recursive breaking change" (Ruben Bridgewater) [#57622](https://github.com/nodejs/node/pull/57622)
* \[[`1c1c504d82`](https://github.com/nodejs/node/commit/1c1c504d82)] - **(SEMVER-MAJOR)** **buffer**: move SlowBuffer to EOL (James M Snell) [#58008](https://github.com/nodejs/node/pull/58008)
* \[[`f92f7e6c82`](https://github.com/nodejs/node/commit/f92f7e6c82)] - **(SEMVER-MAJOR)** **buffer**: make `buflen` in integer range (zhenweijin) [#51821](https://github.com/nodejs/node/pull/51821)
* \[[`dc24270009`](https://github.com/nodejs/node/commit/dc24270009)] - **(SEMVER-MAJOR)** **build**: downgrade armv7 support to experimental (Michaël Zasso) [#58071](https://github.com/nodejs/node/pull/58071)
* \[[`8b40221777`](https://github.com/nodejs/node/commit/8b40221777)] - **(SEMVER-MAJOR)** **build**: bump supported macOS version to 13.5 (Michaël Zasso) [#57115](https://github.com/nodejs/node/pull/57115)
* \[[`ed52ab913b`](https://github.com/nodejs/node/commit/ed52ab913b)] - **(SEMVER-MAJOR)** **build**: increase minimum Xcode version to 16.1 (Michaël Zasso) [#56824](https://github.com/nodejs/node/pull/56824)
* \[[`89f661dd66`](https://github.com/nodejs/node/commit/89f661dd66)] - **(SEMVER-MAJOR)** **build**: link V8 with atomic library (Michaël Zasso) [#55014](https://github.com/nodejs/node/pull/55014)
* \[[`44b0e423dc`](https://github.com/nodejs/node/commit/44b0e423dc)] - **(SEMVER-MAJOR)** **build**: remove support for ppc 32-bit (Michaël Zasso) [#55014](https://github.com/nodejs/node/pull/55014)
* \[[`1f654e655c`](https://github.com/nodejs/node/commit/1f654e655c)] - **(SEMVER-MAJOR)** **build**: reset embedder string to "-node.0" (Michaël Zasso) [#55014](https://github.com/nodejs/node/pull/55014)
* \[[`85330e26b8`](https://github.com/nodejs/node/commit/85330e26b8)] - **(SEMVER-MAJOR)** **child\_process**: deprecate passing `args` to `spawn` and `execFile` (Daniel Venable) [#57199](https://github.com/nodejs/node/pull/57199)
* \[[`52d39441d0`](https://github.com/nodejs/node/commit/52d39441d0)] - **(SEMVER-MAJOR)** **deps**: V8: cherry-pick f915fa4c9f41 (Olivier Flückiger) [#55014](https://github.com/nodejs/node/pull/55014)
* \[[`99ffe3555a`](https://github.com/nodejs/node/commit/99ffe3555a)] - **(SEMVER-MAJOR)** **deps**: V8: cherry-pick 0d5d6e71bbb0 (Yagiz Nizipli) [#55014](https://github.com/nodejs/node/pull/55014)
* \[[`5d8011d91c`](https://github.com/nodejs/node/commit/5d8011d91c)] - **(SEMVER-MAJOR)** **deps**: V8: cherry-pick 0c11feeeca4a (Michaël Zasso) [#55014](https://github.com/nodejs/node/pull/55014)
* \[[`d85d2f8350`](https://github.com/nodejs/node/commit/d85d2f8350)] - **(SEMVER-MAJOR)** **deps**: define V8\_PRESERVE\_MOST as no-op on Windows (Stefan Stojanovic) [#55014](https://github.com/nodejs/node/pull/55014)
* \[[`e8f55f7b7a`](https://github.com/nodejs/node/commit/e8f55f7b7a)] - **(SEMVER-MAJOR)** **deps**: always define V8\_NODISCARD as no-op (Michaël Zasso) [#55014](https://github.com/nodejs/node/pull/55014)
* \[[`b3c1b63a5d`](https://github.com/nodejs/node/commit/b3c1b63a5d)] - **(SEMVER-MAJOR)** **deps**: fix FP16 bitcasts.h (Stefan Stojanovic) [#55014](https://github.com/nodejs/node/pull/55014)
* \[[`d0361f0bba`](https://github.com/nodejs/node/commit/d0361f0bba)] - **(SEMVER-MAJOR)** **deps**: patch V8 to support compilation with MSVC (StefanStojanovic) [#55014](https://github.com/nodejs/node/pull/55014)
* \[[`a4e0fce896`](https://github.com/nodejs/node/commit/a4e0fce896)] - **(SEMVER-MAJOR)** **deps**: patch V8 to avoid duplicated zlib symbol (Michaël Zasso) [#55014](https://github.com/nodejs/node/pull/55014)
* \[[`4f8fd566cc`](https://github.com/nodejs/node/commit/4f8fd566cc)] - **(SEMVER-MAJOR)** **deps**: disable V8 concurrent sparkplug compilation (Michaël Zasso) [#55014](https://github.com/nodejs/node/pull/55014)
* \[[`1142f78f1d`](https://github.com/nodejs/node/commit/1142f78f1d)] - **(SEMVER-MAJOR)** **deps**: always define V8\_EXPORT\_PRIVATE as no-op (Michaël Zasso) [#55014](https://github.com/nodejs/node/pull/55014)
* \[[`5edec0e39a`](https://github.com/nodejs/node/commit/5edec0e39a)] - **(SEMVER-MAJOR)** **deps**: update V8 to 13.0.245.25 (Michaël Zasso) [#55014](https://github.com/nodejs/node/pull/55014)
* \[[`25b22e4754`](https://github.com/nodejs/node/commit/25b22e4754)] - **(SEMVER-MAJOR)** **deps**: upgrade npm to 11.0.0 (npm team) [#56274](https://github.com/nodejs/node/pull/56274)
* \[[`47b80c293d`](https://github.com/nodejs/node/commit/47b80c293d)] - **(SEMVER-MAJOR)** **deps**: update undici to 7.0.0 (Node.js GitHub Bot) [#56070](https://github.com/nodejs/node/pull/56070)
* \[[`bac47c3750`](https://github.com/nodejs/node/commit/bac47c3750)] - **(SEMVER-MAJOR)** **fs**: remove ability to call truncate with fd (Yagiz Nizipli) [#57567](https://github.com/nodejs/node/pull/57567)
* \[[`529b56ef9d`](https://github.com/nodejs/node/commit/529b56ef9d)] - **(SEMVER-MAJOR)** **fs**: deprecate passing invalid types in `fs.existsSync` (Carlos Espa) [#55753](https://github.com/nodejs/node/pull/55753)
* \[[`b02cd411c2`](https://github.com/nodejs/node/commit/b02cd411c2)] - **(SEMVER-MAJOR)** **fs**: runtime deprecate `fs.F_OK`, `fs.R_OK`, `fs.W_OK`, `fs.X_OK` (Livia Medeiros) [#49686](https://github.com/nodejs/node/pull/49686)
* \[[`d9540b51eb`](https://github.com/nodejs/node/commit/d9540b51eb)] - **(SEMVER-MAJOR)** **fs**: remove `dirent.path` (Antoine du Hamel) [#55548](https://github.com/nodejs/node/pull/55548)
* \[[`44ad1664ca`](https://github.com/nodejs/node/commit/44ad1664ca)] - **(SEMVER-MAJOR)** **http**: remove outgoingmessage \_headers and \_headersList (Yagiz Nizipli) [#57551](https://github.com/nodejs/node/pull/57551)
* \[[`4ecc8f5498`](https://github.com/nodejs/node/commit/4ecc8f5498)] - **(SEMVER-MAJOR)** **http2**: session tracking and graceful server close (Kushagra Pandey) [#57586](https://github.com/nodejs/node/pull/57586)
* \[[`be5571b477`](https://github.com/nodejs/node/commit/be5571b477)] - **(SEMVER-MAJOR)** **lib**: remove obsolete Cipher export (James M Snell) [#57266](https://github.com/nodejs/node/pull/57266)
* \[[`1731a78a68`](https://github.com/nodejs/node/commit/1731a78a68)] - **(SEMVER-MAJOR)** **lib**: unexpose six process bindings (Michaël Zasso) [#57149](https://github.com/nodejs/node/pull/57149)
* \[[`51ae57673d`](https://github.com/nodejs/node/commit/51ae57673d)] - **(SEMVER-MAJOR)** **lib**: make ALS default to AsyncContextFrame (Stephen Belanger) [#55552](https://github.com/nodejs/node/pull/55552)
* \[[`019efe1453`](https://github.com/nodejs/node/commit/019efe1453)] - **(SEMVER-MAJOR)** **lib**: runtime deprecate SlowBuffer (Rafael Gonzaga) [#55175](https://github.com/nodejs/node/pull/55175)
* \[[`d5bfca0407`](https://github.com/nodejs/node/commit/d5bfca0407)] - **(SEMVER-MAJOR)** **net**: make \_setSimultaneousAccepts() end-of-life deprecated (Yagiz Nizipli) [#57550](https://github.com/nodejs/node/pull/57550)
* \[[`5ec933bc46`](https://github.com/nodejs/node/commit/5ec933bc46)] - **(SEMVER-MAJOR)** **readline**: add stricter validation for functions called after closed (Dario Piotrowicz) [#57680](https://github.com/nodejs/node/pull/57680)
* \[[`3f00345af6`](https://github.com/nodejs/node/commit/3f00345af6)] - **(SEMVER-MAJOR)** **readline**: fix unicode line separators being ignored (Dario Piotrowicz) [#57591](https://github.com/nodejs/node/pull/57591)
* \[[`0368f2f662`](https://github.com/nodejs/node/commit/0368f2f662)] - **(SEMVER-MAJOR)** **repl**: runtime deprecate instantiating without new (Aviv Keller) [#54869](https://github.com/nodejs/node/pull/54869)
* \[[`7e8752006a`](https://github.com/nodejs/node/commit/7e8752006a)] - **(SEMVER-MAJOR)** **src**: update GetForegroundTaskRunner override (Etienne Pierre-doray) [#55014](https://github.com/nodejs/node/pull/55014)
* \[[`7917b67313`](https://github.com/nodejs/node/commit/7917b67313)] - **(SEMVER-MAJOR)** **src**: update NODE\_MODULE\_VERSION to 134 (Michaël Zasso) [#55014](https://github.com/nodejs/node/pull/55014)
* \[[`bf3bc4ec2f`](https://github.com/nodejs/node/commit/bf3bc4ec2f)] - **(SEMVER-MAJOR)** **src**: drop --experimental-permission in favour of --permission (Rafael Gonzaga) [#56240](https://github.com/nodejs/node/pull/56240)
* \[[`58982d712b`](https://github.com/nodejs/node/commit/58982d712b)] - **(SEMVER-MAJOR)** **src**: add async context frame to AsyncResource (Gerhard Stöbich) [#56082](https://github.com/nodejs/node/pull/56082)
* \[[`03dcd7077a`](https://github.com/nodejs/node/commit/03dcd7077a)] - **(SEMVER-MAJOR)** **src**: nuke deprecated and un-used enum members in `OptionEnvvarSettings` (Juan José) [#53079](https://github.com/nodejs/node/pull/53079)
* \[[`fd8de670da`](https://github.com/nodejs/node/commit/fd8de670da)] - **(SEMVER-MAJOR)** **stream**: catch and forward error from dest.write (jakecastelli) [#55270](https://github.com/nodejs/node/pull/55270)
* \[[`6857dbc018`](https://github.com/nodejs/node/commit/6857dbc018)] - **(SEMVER-MAJOR)** **test**: disable fast API call count checks (Michaël Zasso) [#55014](https://github.com/nodejs/node/pull/55014)
* \[[`1a2eb15bc6`](https://github.com/nodejs/node/commit/1a2eb15bc6)] - **(SEMVER-MAJOR)** **test\_runner**: remove promises returned by t.test() (Colin Ihrig) [#56664](https://github.com/nodejs/node/pull/56664)
* \[[`96718268fe`](https://github.com/nodejs/node/commit/96718268fe)] - **(SEMVER-MAJOR)** **test\_runner**: remove promises returned by test() (Colin Ihrig) [#56664](https://github.com/nodejs/node/pull/56664)
* \[[`aa3523ec22`](https://github.com/nodejs/node/commit/aa3523ec22)] - **(SEMVER-MAJOR)** **test\_runner**: automatically wait for subtests to finish (Colin Ihrig) [#56664](https://github.com/nodejs/node/pull/56664)
* \[[`736537f892`](https://github.com/nodejs/node/commit/736537f892)] - **(SEMVER-MAJOR)** **timers**: check for immediate instance in clearImmediate (Gürgün Dayıoğlu) [#57069](https://github.com/nodejs/node/pull/57069)
* \[[`5d7091f1bc`](https://github.com/nodejs/node/commit/5d7091f1bc)] - **(SEMVER-MAJOR)** **timers**: set several methods EOL (Yagiz Nizipli) [#56966](https://github.com/nodejs/node/pull/56966)
* \[[`9beb616c1c`](https://github.com/nodejs/node/commit/9beb616c1c)] - **(SEMVER-MAJOR)** **tls**: remove deprecated tls.createSecurePair (Jonas) [#57361](https://github.com/nodejs/node/pull/57361)
* \[[`4769f284c3`](https://github.com/nodejs/node/commit/4769f284c3)] - **(SEMVER-MAJOR)** **tls**: make server.prototype.setOptions end-of-life (Yagiz Nizipli) [#57339](https://github.com/nodejs/node/pull/57339)
* \[[`6f965260dd`](https://github.com/nodejs/node/commit/6f965260dd)] - **(SEMVER-MAJOR)** **tools**: update V8 gypfiles for 13.0 (Michaël Zasso) [#55014](https://github.com/nodejs/node/pull/55014)
* \[[`d1f8ccb10d`](https://github.com/nodejs/node/commit/d1f8ccb10d)] - **(SEMVER-MAJOR)** **url**: expose urlpattern as global (Jonas) [#56950](https://github.com/nodejs/node/pull/56950)
* \[[`11fbdd8c9d`](https://github.com/nodejs/node/commit/11fbdd8c9d)] - **(SEMVER-MAJOR)** **url**: runtime deprecate url.parse (Yagiz Nizipli) [#55017](https://github.com/nodejs/node/pull/55017)
* \[[`4ee87b8bc3`](https://github.com/nodejs/node/commit/4ee87b8bc3)] - **(SEMVER-MAJOR)** **zlib**: deprecate classes usage without `new` (Yagiz Nizipli) [#55718](https://github.com/nodejs/node/pull/55718)

### Semver-Minor Commits

* \[[`4ce2467061`](https://github.com/nodejs/node/commit/4ce2467061)] - **(SEMVER-MINOR)** **assert**: mark partialDeepStrictEqual() as stable (Ruben Bridgewater) [#57370](https://github.com/nodejs/node/pull/57370)
* \[[`e2beb6db60`](https://github.com/nodejs/node/commit/e2beb6db60)] - **(SEMVER-MINOR)** **doc**: graduate multiple experimental apis (James M Snell) [#57765](https://github.com/nodejs/node/pull/57765)
* \[[`82fdeb528f`](https://github.com/nodejs/node/commit/82fdeb528f)] - **(SEMVER-MINOR)** **esm**: graduate import.meta properties (James M Snell) [#58011](https://github.com/nodejs/node/pull/58011)
* \[[`cbf9a64687`](https://github.com/nodejs/node/commit/cbf9a64687)] - **(SEMVER-MINOR)** **esm**: support top-level Wasm without package type (Guy Bedford) [#57610](https://github.com/nodejs/node/pull/57610)
* \[[`5795c55aaa`](https://github.com/nodejs/node/commit/5795c55aaa)] - **(SEMVER-MINOR)** **esm**: support source phase imports for WebAssembly (Guy Bedford) [#56919](https://github.com/nodejs/node/pull/56919)
* \[[`703995a4a8`](https://github.com/nodejs/node/commit/703995a4a8)] - **(SEMVER-MINOR)** **http**: support http proxy for fetch under NODE\_USE\_ENV\_PROXY (Joyee Cheung) [#57165](https://github.com/nodejs/node/pull/57165)
* \[[`e74ef8ffad`](https://github.com/nodejs/node/commit/e74ef8ffad)] - **(SEMVER-MINOR)** **lib**: add defaultValue and name options to AsyncLocalStorage (James M Snell) [#57766](https://github.com/nodejs/node/pull/57766)
* \[[`b726903e30`](https://github.com/nodejs/node/commit/b726903e30)] - **(SEMVER-MINOR)** **repl**: add support for multiline history (Giovanni Bucci) [#57400](https://github.com/nodejs/node/pull/57400)
* \[[`0077ca11f5`](https://github.com/nodejs/node/commit/0077ca11f5)] - **(SEMVER-MINOR)** **src**: add ExecutionAsyncId getter for any Context (Attila Szegedi) [#57820](https://github.com/nodejs/node/pull/57820)
* \[[`56336eeb85`](https://github.com/nodejs/node/commit/56336eeb85)] - **(SEMVER-MINOR)** **stream**: preserve AsyncLocalStorage context in finished() (Gürgün Dayıoğlu) [#57865](https://github.com/nodejs/node/pull/57865)
* \[[`55413004c8`](https://github.com/nodejs/node/commit/55413004c8)] - **(SEMVER-MINOR)** **stream**: handle generator destruction from Duplex.from() (Matthieu Sieben) [#55096](https://github.com/nodejs/node/pull/55096)
* \[[`350b82c5a4`](https://github.com/nodejs/node/commit/350b82c5a4)] - **(SEMVER-MINOR)** **test\_runner**: add global setup and teardown functionality (Pietro Marchini) [#57438](https://github.com/nodejs/node/pull/57438)
* \[[`6cd04d7708`](https://github.com/nodejs/node/commit/6cd04d7708)] - **(SEMVER-MINOR)** **util**: add `types.isFloat16Array()` (Livia Medeiros) [#57879](https://github.com/nodejs/node/pull/57879)
* \[[`f342ad2a3f`](https://github.com/nodejs/node/commit/f342ad2a3f)] - **(SEMVER-MINOR)** **worker**: add worker.getHeapStatistics() (Matteo Collina) [#57888](https://github.com/nodejs/node/pull/57888)

### Semver-Patch Commits

* \[[`953aa2103d`](https://github.com/nodejs/node/commit/953aa2103d)] - **assert**: support `Float16Array` in loose deep equality checks (Livia Medeiros) [#57881](https://github.com/nodejs/node/pull/57881)
* \[[`7cf6fbea99`](https://github.com/nodejs/node/commit/7cf6fbea99)] - **assert,util**: fix constructor lookup in deep equal comparison (Ruben Bridgewater) [#57876](https://github.com/nodejs/node/pull/57876)
* \[[`ee95d40d7a`](https://github.com/nodejs/node/commit/ee95d40d7a)] - **assert,util**: improve deep object comparison performance (Ruben Bridgewater) [#57648](https://github.com/nodejs/node/pull/57648)
* \[[`12a6fee66c`](https://github.com/nodejs/node/commit/12a6fee66c)] - **assert,util**: improve unequal number comparison performance (Ruben Bridgewater) [#57619](https://github.com/nodejs/node/pull/57619)
* \[[`7b603a3c1c`](https://github.com/nodejs/node/commit/7b603a3c1c)] - **assert,util**: improve array comparison (Ruben Bridgewater) [#57619](https://github.com/nodejs/node/pull/57619)
* \[[`311e86b3a2`](https://github.com/nodejs/node/commit/311e86b3a2)] - **async\_hooks**: enable AsyncLocalStorage once constructed (Chengzhong Wu) [#58029](https://github.com/nodejs/node/pull/58029)
* \[[`429b4eea72`](https://github.com/nodejs/node/commit/429b4eea72)] - **benchmark**: disambiguate `filename` and `dirname` read perf (Antoine du Hamel) [#58056](https://github.com/nodejs/node/pull/58056)
* \[[`c2150e0724`](https://github.com/nodejs/node/commit/c2150e0724)] - **buffer**: avoid creating unnecessary environment (Yagiz Nizipli) [#58053](https://github.com/nodejs/node/pull/58053)
* \[[`5335158b6a`](https://github.com/nodejs/node/commit/5335158b6a)] - **buffer**: improve byteLength performance (Yagiz Nizipli) [#58048](https://github.com/nodejs/node/pull/58048)
* \[[`38368fbf1c`](https://github.com/nodejs/node/commit/38368fbf1c)] - **buffer**: define global v8::CFunction objects as const (Mert Can Altin) [#57676](https://github.com/nodejs/node/pull/57676)
* \[[`9e0abe52b0`](https://github.com/nodejs/node/commit/9e0abe52b0)] - **build**: use `$(BUILDTYPE)` when cleaning coverage files (Aviv Keller) [#57995](https://github.com/nodejs/node/pull/57995)
* \[[`df48d168fa`](https://github.com/nodejs/node/commit/df48d168fa)] - **build**: define python when generating `out/Makefile` (Aviv Keller) [#57970](https://github.com/nodejs/node/pull/57970)
* \[[`f9f0314487`](https://github.com/nodejs/node/commit/f9f0314487)] - **build**: fix zstd libname (Antoine du Hamel) [#57999](https://github.com/nodejs/node/pull/57999)
* \[[`ecbef9b1ba`](https://github.com/nodejs/node/commit/ecbef9b1ba)] - **build**: use clang-cl in coverage-windows workflow (Michaël Zasso) [#57919](https://github.com/nodejs/node/pull/57919)
* \[[`b0a797f4c6`](https://github.com/nodejs/node/commit/b0a797f4c6)] - **build**: fix missing files warning (Luigi Pinca) [#57870](https://github.com/nodejs/node/pull/57870)
* \[[`7755d192f1`](https://github.com/nodejs/node/commit/7755d192f1)] - **build**: remove redundant `-mXX` flags for V8 (Michaël Zasso) [#57907](https://github.com/nodejs/node/pull/57907)
* \[[`e55b02b368`](https://github.com/nodejs/node/commit/e55b02b368)] - **build**: drop support for python 3.8 (Aviv Keller) [#55239](https://github.com/nodejs/node/pull/55239)
* \[[`b34212b4e9`](https://github.com/nodejs/node/commit/b34212b4e9)] - **crypto**: fix cross-realm `SharedArrayBuffer` validation (Antoine du Hamel) [#57974](https://github.com/nodejs/node/pull/57974)
* \[[`3e876cd846`](https://github.com/nodejs/node/commit/3e876cd846)] - **crypto**: fix cross-realm check of `ArrayBuffer` (Felipe Forbeck) [#57828](https://github.com/nodejs/node/pull/57828)
* \[[`a1ad082292`](https://github.com/nodejs/node/commit/a1ad082292)] - **crypto**: forbid passing `Float16Array` to `getRandomValues()` (Livia Medeiros) [#57880](https://github.com/nodejs/node/pull/57880)
* \[[`d13d273153`](https://github.com/nodejs/node/commit/d13d273153)] - **crypto**: revert dangerous uses of std::string\_view (Tobias Nießen) [#57816](https://github.com/nodejs/node/pull/57816)
* \[[`e60146515b`](https://github.com/nodejs/node/commit/e60146515b)] - **crypto**: fix misleading positional argument (Tobias Nießen) [#57843](https://github.com/nodejs/node/pull/57843)
* \[[`4178f97884`](https://github.com/nodejs/node/commit/4178f97884)] - **crypto**: make auth tag size assumption explicit (Tobias Nießen) [#57803](https://github.com/nodejs/node/pull/57803)
* \[[`fcffbee0a2`](https://github.com/nodejs/node/commit/fcffbee0a2)] - **crypto**: remove CipherBase::Init (Tobias Nießen) [#57787](https://github.com/nodejs/node/pull/57787)
* \[[`34d2b8ed73`](https://github.com/nodejs/node/commit/34d2b8ed73)] - **crypto**: remove BoringSSL dh-primes addition (Shelley Vohr) [#57023](https://github.com/nodejs/node/pull/57023)
* \[[`ba2892f14e`](https://github.com/nodejs/node/commit/ba2892f14e)] - **deps**: update ada to 3.2.3 (Node.js GitHub Bot) [#58045](https://github.com/nodejs/node/pull/58045)
* \[[`eeddf8d39b`](https://github.com/nodejs/node/commit/eeddf8d39b)] - **deps**: update zstd to 1.5.7 (Node.js GitHub Bot) [#57940](https://github.com/nodejs/node/pull/57940)
* \[[`56d958be1d`](https://github.com/nodejs/node/commit/56d958be1d)] - **deps**: update simdutf to 6.5.0 (Node.js GitHub Bot) [#57939](https://github.com/nodejs/node/pull/57939)
* \[[`e142710337`](https://github.com/nodejs/node/commit/e142710337)] - **deps**: update undici to 7.8.0 (Node.js GitHub Bot) [#57770](https://github.com/nodejs/node/pull/57770)
* \[[`62d4e51acb`](https://github.com/nodejs/node/commit/62d4e51acb)] - **deps**: update zlib to 1.3.0.1-motley-780819f (Node.js GitHub Bot) [#57768](https://github.com/nodejs/node/pull/57768)
* \[[`f4671e7188`](https://github.com/nodejs/node/commit/f4671e7188)] - **deps**: update timezone to 2025b (Node.js GitHub Bot) [#57857](https://github.com/nodejs/node/pull/57857)
* \[[`7519f894cd`](https://github.com/nodejs/node/commit/7519f894cd)] - **deps**: update amaro to 0.5.2 (Node.js GitHub Bot) [#57871](https://github.com/nodejs/node/pull/57871)
* \[[`00247677de`](https://github.com/nodejs/node/commit/00247677de)] - **deps**: update simdutf to 6.4.2 (Node.js GitHub Bot) [#57855](https://github.com/nodejs/node/pull/57855)
* \[[`bdc81ef8bf`](https://github.com/nodejs/node/commit/bdc81ef8bf)] - **deps**: delete OpenSSL demos, doc and test folders (Michaël Zasso) [#57835](https://github.com/nodejs/node/pull/57835)
* \[[`4e2d09ed23`](https://github.com/nodejs/node/commit/4e2d09ed23)] - **deps**: upgrade npm to 11.3.0 (npm team) [#57801](https://github.com/nodejs/node/pull/57801)
* \[[`c50a332f92`](https://github.com/nodejs/node/commit/c50a332f92)] - **deps**: update c-ares to v1.34.5 (Node.js GitHub Bot) [#57792](https://github.com/nodejs/node/pull/57792)
* \[[`ea65fcf784`](https://github.com/nodejs/node/commit/ea65fcf784)] - **deps**: update simdutf to 6.4.0 (Node.js GitHub Bot) [#56764](https://github.com/nodejs/node/pull/56764)
* \[[`dbfaca3153`](https://github.com/nodejs/node/commit/dbfaca3153)] - **deps**: update ada to 3.2.2 (Yagiz Nizipli) [#57693](https://github.com/nodejs/node/pull/57693)
* \[[`018c133085`](https://github.com/nodejs/node/commit/018c133085)] - **deps**: update amaro to 0.5.1 (Marco Ippolito) [#57704](https://github.com/nodejs/node/pull/57704)
* \[[`f0aac6ed32`](https://github.com/nodejs/node/commit/f0aac6ed32)] - **deps**: update undici to 7.6.0 (nodejs-github-bot) [#57685](https://github.com/nodejs/node/pull/57685)
* \[[`0729bbc31d`](https://github.com/nodejs/node/commit/0729bbc31d)] - **deps**: update amaro to 0.5.0 (nodejs-github-bot) [#57687](https://github.com/nodejs/node/pull/57687)
* \[[`a4e0383ff0`](https://github.com/nodejs/node/commit/a4e0383ff0)] - **deps**: update icu to 77.1 (Node.js GitHub Bot) [#57455](https://github.com/nodejs/node/pull/57455)
* \[[`8ef7016f37`](https://github.com/nodejs/node/commit/8ef7016f37)] - **deps**: update undici to 7.5.0 (Node.js GitHub Bot) [#57427](https://github.com/nodejs/node/pull/57427)
* \[[`49f3b275a5`](https://github.com/nodejs/node/commit/49f3b275a5)] - **deps**: upgrade npm to 11.2.0 (npm team) [#57334](https://github.com/nodejs/node/pull/57334)
* \[[`b95b76592e`](https://github.com/nodejs/node/commit/b95b76592e)] - **deps**: update undici to 7.4.0 (Node.js GitHub Bot) [#57236](https://github.com/nodejs/node/pull/57236)
* \[[`9dee7b94bf`](https://github.com/nodejs/node/commit/9dee7b94bf)] - **deps**: update undici to 7.3.0 (Node.js GitHub Bot) [#56624](https://github.com/nodejs/node/pull/56624)
* \[[`cadc4ed067`](https://github.com/nodejs/node/commit/cadc4ed067)] - **deps**: upgrade npm to 11.1.0 (npm team) [#56818](https://github.com/nodejs/node/pull/56818)
* \[[`5770972dc6`](https://github.com/nodejs/node/commit/5770972dc6)] - **deps**: update undici to 7.2.1 (Node.js GitHub Bot) [#56569](https://github.com/nodejs/node/pull/56569)
* \[[`67b647edc7`](https://github.com/nodejs/node/commit/67b647edc7)] - **deps**: update undici to 7.2.0 (Node.js GitHub Bot) [#56335](https://github.com/nodejs/node/pull/56335)
* \[[`6c03beba46`](https://github.com/nodejs/node/commit/6c03beba46)] - **deps**: update undici to 7.1.0 (Node.js GitHub Bot) [#56179](https://github.com/nodejs/node/pull/56179)
* \[[`782b189fd3`](https://github.com/nodejs/node/commit/782b189fd3)] - **dns**: restore dns query cache ttl (Ethan Arrowood) [#57640](https://github.com/nodejs/node/pull/57640)
* \[[`e512009651`](https://github.com/nodejs/node/commit/e512009651)] - **doc**: fix env variable name in `util.styleText` (Antoine du Hamel) [#58072](https://github.com/nodejs/node/pull/58072)
* \[[`fcb0a5658b`](https://github.com/nodejs/node/commit/fcb0a5658b)] - **doc**: add returns for https.get (Eng Zer Jun) [#58025](https://github.com/nodejs/node/pull/58025)
* \[[`db5a5404f7`](https://github.com/nodejs/node/commit/db5a5404f7)] - **doc**: fix typo in `buffer.md` (chocolateboy) [#58052](https://github.com/nodejs/node/pull/58052)
* \[[`edf1621113`](https://github.com/nodejs/node/commit/edf1621113)] - **doc**: reserve module version 136 for Electron 37 (Calvin) [#57979](https://github.com/nodejs/node/pull/57979)
* \[[`6c68429d93`](https://github.com/nodejs/node/commit/6c68429d93)] - **doc**: correct deprecation type of `assert.CallTracker` (René) [#57997](https://github.com/nodejs/node/pull/57997)
* \[[`2966d0a8fe`](https://github.com/nodejs/node/commit/2966d0a8fe)] - **doc**: fix `AsyncLocalStorage` example response changes after node v18 (Naor Tedgi (Abu Emma)) [#57969](https://github.com/nodejs/node/pull/57969)
* \[[`8094ea67c8`](https://github.com/nodejs/node/commit/8094ea67c8)] - **doc**: fix linter errors (Antoine du Hamel) [#57987](https://github.com/nodejs/node/pull/57987)
* \[[`140cfd66d8`](https://github.com/nodejs/node/commit/140cfd66d8)] - **doc**: mark devtools integration section as active development (Chengzhong Wu) [#57886](https://github.com/nodejs/node/pull/57886)
* \[[`d1ebb568a0`](https://github.com/nodejs/node/commit/d1ebb568a0)] - **doc**: fix typo in `module.md` (Alex Schwartz) [#57889](https://github.com/nodejs/node/pull/57889)
* \[[`0d8a5e1ca2`](https://github.com/nodejs/node/commit/0d8a5e1ca2)] - **doc**: increase z-index of header element (Dario Piotrowicz) [#57851](https://github.com/nodejs/node/pull/57851)
* \[[`bfad36b616`](https://github.com/nodejs/node/commit/bfad36b616)] - **doc**: clarify future Corepack removal in v25+ (Trivikram Kamat) [#57825](https://github.com/nodejs/node/pull/57825)
* \[[`11d1a96598`](https://github.com/nodejs/node/commit/11d1a96598)] - **doc**: add missing TS formats for `load` hooks (Antoine du Hamel) [#57837](https://github.com/nodejs/node/pull/57837)
* \[[`3162116649`](https://github.com/nodejs/node/commit/3162116649)] - **doc**: clarify the multi REPL example (Dario Piotrowicz) [#57759](https://github.com/nodejs/node/pull/57759)
* \[[`6dfc40482d`](https://github.com/nodejs/node/commit/6dfc40482d)] - **doc**: fix deprecation type for `DEP0148` (Livia Medeiros) [#57785](https://github.com/nodejs/node/pull/57785)
* \[[`a4e305a21c`](https://github.com/nodejs/node/commit/a4e305a21c)] - **doc**: list DOMException as a potential error raised by Node.js (Chengzhong Wu) [#57783](https://github.com/nodejs/node/pull/57783)
* \[[`cc79470347`](https://github.com/nodejs/node/commit/cc79470347)] - **doc**: add missing v0.x changelog entries (Antoine du Hamel) [#57779](https://github.com/nodejs/node/pull/57779)
* \[[`3449356c2d`](https://github.com/nodejs/node/commit/3449356c2d)] - **doc**: fix typo in writing-docs (Sebastian Beltran) [#57776](https://github.com/nodejs/node/pull/57776)
* \[[`551d26a923`](https://github.com/nodejs/node/commit/551d26a923)] - **doc**: clarify examples section in REPL doc (Dario Piotrowicz) [#57762](https://github.com/nodejs/node/pull/57762)
* \[[`e5223d9467`](https://github.com/nodejs/node/commit/e5223d9467)] - **doc**: explicitly state that corepack will be removed in v25+ (Trivikram Kamat) [#57747](https://github.com/nodejs/node/pull/57747)
* \[[`0f0c506ed5`](https://github.com/nodejs/node/commit/0f0c506ed5)] - **doc**: update position type to integer | null in fs (Yukihiro Hasegawa) [#57745](https://github.com/nodejs/node/pull/57745)
* \[[`9a90056a45`](https://github.com/nodejs/node/commit/9a90056a45)] - **doc**: allow the $schema property in node.config.json (Remco Haszing) [#57560](https://github.com/nodejs/node/pull/57560)
* \[[`ff72e4c578`](https://github.com/nodejs/node/commit/ff72e4c578)] - **doc**: update CI instructions (Antoine du Hamel) [#57743](https://github.com/nodejs/node/pull/57743)
* \[[`6bcacb0349`](https://github.com/nodejs/node/commit/6bcacb0349)] - **doc**: update example of using `await` in REPL (Dario Piotrowicz) [#57653](https://github.com/nodejs/node/pull/57653)
* \[[`7d9e112f9e`](https://github.com/nodejs/node/commit/7d9e112f9e)] - **doc**: add back mention of visa fees to onboarding doc (Darshan Sen) [#57730](https://github.com/nodejs/node/pull/57730)
* \[[`9ee30598fc`](https://github.com/nodejs/node/commit/9ee30598fc)] - **doc**: remove link to `QUIC.md` (Antoine du Hamel) [#57729](https://github.com/nodejs/node/pull/57729)
* \[[`5d3106d7b8`](https://github.com/nodejs/node/commit/5d3106d7b8)] - **doc**: process.execve is only unavailable for Windows (Yaksh Bariya) [#57726](https://github.com/nodejs/node/pull/57726)
* \[[`1bed9b4cb8`](https://github.com/nodejs/node/commit/1bed9b4cb8)] - **doc**: mark type stripping as release candidate (Marco Ippolito) [#57705](https://github.com/nodejs/node/pull/57705)
* \[[`6f5b4fd8b1`](https://github.com/nodejs/node/commit/6f5b4fd8b1)] - **doc**: clarify `unhandledRejection` events behaviors in process doc (Dario Piotrowicz) [#57654](https://github.com/nodejs/node/pull/57654)
* \[[`dc8427aa0d`](https://github.com/nodejs/node/commit/dc8427aa0d)] - **doc**: improved fetch docs (Alessandro Miliucci) [#57296](https://github.com/nodejs/node/pull/57296)
* \[[`75825aa27e`](https://github.com/nodejs/node/commit/75825aa27e)] - **doc**: document REPL custom eval arguments (Dario Piotrowicz) [#57690](https://github.com/nodejs/node/pull/57690)
* \[[`9d05072b6e`](https://github.com/nodejs/node/commit/9d05072b6e)] - **doc**: classify Chrome DevTools Protocol as tier 2 (Chengzhong Wu) [#57634](https://github.com/nodejs/node/pull/57634)
* \[[`d44a827519`](https://github.com/nodejs/node/commit/d44a827519)] - **doc**: mark multiple vm module APIS stable (James M Snell) [#57513](https://github.com/nodejs/node/pull/57513)
* \[[`5965a4cd5f`](https://github.com/nodejs/node/commit/5965a4cd5f)] - **doc**: correct status of require(esm) warning in v20 changelog (Joyee Cheung) [#57529](https://github.com/nodejs/node/pull/57529)
* \[[`7a86454608`](https://github.com/nodejs/node/commit/7a86454608)] - **doc**: reserve NMV 135 for Electron 36 (David Sanders) [#57151](https://github.com/nodejs/node/pull/57151)
* \[[`5119049ca6`](https://github.com/nodejs/node/commit/5119049ca6)] - **doc**: fix faulty YAML metadata (Antoine du Hamel) [#56508](https://github.com/nodejs/node/pull/56508)
* \[[`7bedcfd4a2`](https://github.com/nodejs/node/commit/7bedcfd4a2)] - **doc**: fix typo (Alex Yang) [#56125](https://github.com/nodejs/node/pull/56125)
* \[[`069ec1b983`](https://github.com/nodejs/node/commit/069ec1b983)] - **doc**: consolidate history table of CustomEvent (Edigleysson Silva (Edy)) [#55758](https://github.com/nodejs/node/pull/55758)
* \[[`b49c9c8701`](https://github.com/nodejs/node/commit/b49c9c8701)] - **doc,build,win**: update docs with clang (Stefan Stojanovic) [#57991](https://github.com/nodejs/node/pull/57991)
* \[[`77c49c5793`](https://github.com/nodejs/node/commit/77c49c5793)] - **esm**: avoid `import.meta` setup costs for unused properties (Antoine du Hamel) [#57286](https://github.com/nodejs/node/pull/57286)
* \[[`f3c4ece9fe`](https://github.com/nodejs/node/commit/f3c4ece9fe)] - **fs**: added test for missing call to uv\_fs\_req\_cleanup (Justin Nietzel) [#57811](https://github.com/nodejs/node/pull/57811)
* \[[`ea95ec6bf5`](https://github.com/nodejs/node/commit/ea95ec6bf5)] - **fs**: add missing call to uv\_fs\_req\_cleanup (Justin Nietzel) [#57811](https://github.com/nodejs/node/pull/57811)
* \[[`39af0aa444`](https://github.com/nodejs/node/commit/39af0aa444)] - **fs**: improve globSync performance (Rich Trott) [#57725](https://github.com/nodejs/node/pull/57725)
* \[[`d931914d0e`](https://github.com/nodejs/node/commit/d931914d0e)] - **fs**: only show deprecation warning when error code matches (Antoine du Hamel) [#56549](https://github.com/nodejs/node/pull/56549)
* \[[`c91ce2120c`](https://github.com/nodejs/node/commit/c91ce2120c)] - **fs**: fix `getDirent().parentPath` when type is `UV_DIRENT_UNKNOWN` (Livia Medeiros) [#55553](https://github.com/nodejs/node/pull/55553)
* \[[`1cdb0e15b6`](https://github.com/nodejs/node/commit/1cdb0e15b6)] - **http2**: add raw header array support to h2Session.request() (Tim Perry) [#57917](https://github.com/nodejs/node/pull/57917)
* \[[`8c156d5117`](https://github.com/nodejs/node/commit/8c156d5117)] - **http2**: use args.This() instead of args.Holder() (Joyee Cheung) [#58004](https://github.com/nodejs/node/pull/58004)
* \[[`639267fb44`](https://github.com/nodejs/node/commit/639267fb44)] - **http2**: fix graceful session close (Kushagra Pandey) [#57808](https://github.com/nodejs/node/pull/57808)
* \[[`733b6b1fce`](https://github.com/nodejs/node/commit/733b6b1fce)] - **http2**: fix check for `frame->hd.type` (hanguanqiang) [#57644](https://github.com/nodejs/node/pull/57644)
* \[[`9725a83cce`](https://github.com/nodejs/node/commit/9725a83cce)] - **http2**: skip writeHead if stream is closed (Shima Ryuhei) [#57686](https://github.com/nodejs/node/pull/57686)
* \[[`09e8c88ed4`](https://github.com/nodejs/node/commit/09e8c88ed4)] - **lib**: avoid StackOverflow on `serializeError` (Chengzhong Wu) [#58075](https://github.com/nodejs/node/pull/58075)
* \[[`f2d004b733`](https://github.com/nodejs/node/commit/f2d004b733)] - **lib**: resolve the issue of not adhering to the specified buffer size (0hm☘️🏳️‍⚧️) [#55896](https://github.com/nodejs/node/pull/55896)
* \[[`92bba294cf`](https://github.com/nodejs/node/commit/92bba294cf)] - **lib**: fix AbortSignal.any() with timeout signals (Gürgün Dayıoğlu) [#57867](https://github.com/nodejs/node/pull/57867)
* \[[`ab56bf9f74`](https://github.com/nodejs/node/commit/ab56bf9f74)] - **lib**: use Map primordial for ActiveAsyncContextFrame (Gürgün Dayıoğlu) [#57670](https://github.com/nodejs/node/pull/57670)
* \[[`2d98c63572`](https://github.com/nodejs/node/commit/2d98c63572)] - **meta**: allow penetration testing on live system with prior authorization (Matteo Collina) [#57966](https://github.com/nodejs/node/pull/57966)
* \[[`0d6d9851fb`](https://github.com/nodejs/node/commit/0d6d9851fb)] - **meta**: fix subsystem in commit title (Luigi Pinca) [#57945](https://github.com/nodejs/node/pull/57945)
* \[[`e4b845f814`](https://github.com/nodejs/node/commit/e4b845f814)] - **meta**: bump Mozilla-Actions/sccache-action from 0.0.8 to 0.0.9 (dependabot\[bot]) [#57720](https://github.com/nodejs/node/pull/57720)
* \[[`882e4801a7`](https://github.com/nodejs/node/commit/882e4801a7)] - **meta**: bump actions/download-artifact from 4.1.9 to 4.2.1 (dependabot\[bot]) [#57719](https://github.com/nodejs/node/pull/57719)
* \[[`3a1ca449e3`](https://github.com/nodejs/node/commit/3a1ca449e3)] - **meta**: bump actions/setup-python from 5.4.0 to 5.5.0 (dependabot\[bot]) [#57718](https://github.com/nodejs/node/pull/57718)
* \[[`5cca504045`](https://github.com/nodejs/node/commit/5cca504045)] - **meta**: bump peter-evans/create-pull-request from 7.0.7 to 7.0.8 (dependabot\[bot]) [#57717](https://github.com/nodejs/node/pull/57717)
* \[[`fdc8192999`](https://github.com/nodejs/node/commit/fdc8192999)] - **meta**: bump github/codeql-action from 3.28.10 to 3.28.13 (dependabot\[bot]) [#57716](https://github.com/nodejs/node/pull/57716)
* \[[`cb85db32c8`](https://github.com/nodejs/node/commit/cb85db32c8)] - **meta**: bump actions/cache from 4.2.2 to 4.2.3 (dependabot\[bot]) [#57715](https://github.com/nodejs/node/pull/57715)
* \[[`2eb9ca0a4f`](https://github.com/nodejs/node/commit/2eb9ca0a4f)] - **meta**: bump actions/setup-node from 4.2.0 to 4.3.0 (dependabot\[bot]) [#57714](https://github.com/nodejs/node/pull/57714)
* \[[`d5ef101bb6`](https://github.com/nodejs/node/commit/d5ef101bb6)] - **meta**: bump actions/upload-artifact from 4.6.1 to 4.6.2 (dependabot\[bot]) [#57713](https://github.com/nodejs/node/pull/57713)
* \[[`81ad5b2af6`](https://github.com/nodejs/node/commit/81ad5b2af6)] - **module**: fix incorrect formatting in require(esm) cycle error message (haykam821) [#57453](https://github.com/nodejs/node/pull/57453)
* \[[`beb21a0543`](https://github.com/nodejs/node/commit/beb21a0543)] - **module**: improve `getPackageType` performance (Dario Piotrowicz) [#57599](https://github.com/nodejs/node/pull/57599)
* \[[`7b6b07f1a7`](https://github.com/nodejs/node/commit/7b6b07f1a7)] - **module**: remove unnecessary `readPackage` function (Dario Piotrowicz) [#57596](https://github.com/nodejs/node/pull/57596)
* \[[`6cacc36f16`](https://github.com/nodejs/node/commit/6cacc36f16)] - **module**: improve typescript error message format (Marco Ippolito) [#57687](https://github.com/nodejs/node/pull/57687)
* \[[`d383110af5`](https://github.com/nodejs/node/commit/d383110af5)] - **node-api**: add nested object wrap and napi\_ref test (Chengzhong Wu) [#57981](https://github.com/nodejs/node/pull/57981)
* \[[`a963e83f43`](https://github.com/nodejs/node/commit/a963e83f43)] - **node-api**: convert NewEnv to node\_napi\_env\_\_::New (Vladimir Morozov) [#57834](https://github.com/nodejs/node/pull/57834)
* \[[`06c0e21fa5`](https://github.com/nodejs/node/commit/06c0e21fa5)] - **os**: fix netmask format check condition in getCIDR function (Wiyeong Seo) [#57324](https://github.com/nodejs/node/pull/57324)
* \[[`93f5b4668b`](https://github.com/nodejs/node/commit/93f5b4668b)] - **process**: disable building execve on IBM i (Abdirahim Musse) [#57883](https://github.com/nodejs/node/pull/57883)
* \[[`9230f22029`](https://github.com/nodejs/node/commit/9230f22029)] - **process**: remove support for undocumented symbol (Antoine du Hamel) [#56552](https://github.com/nodejs/node/pull/56552)
* \[[`4280a8b5f2`](https://github.com/nodejs/node/commit/4280a8b5f2)] - **quic**: fix debug log (jakecastelli) [#57689](https://github.com/nodejs/node/pull/57689)
* \[[`b1df3e94d7`](https://github.com/nodejs/node/commit/b1df3e94d7)] - **repl**: fix multiline history editing string order (Giovanni Bucci) [#57874](https://github.com/nodejs/node/pull/57874)
* \[[`8cb6f30ab3`](https://github.com/nodejs/node/commit/8cb6f30ab3)] - **repl**: deprecate `repl.builtinModules` (Dario Piotrowicz) [#57508](https://github.com/nodejs/node/pull/57508)
* \[[`b45da5bbef`](https://github.com/nodejs/node/commit/b45da5bbef)] - **sqlite**: add location method (Edy Silva) [#57860](https://github.com/nodejs/node/pull/57860)
* \[[`885c61f051`](https://github.com/nodejs/node/commit/885c61f051)] - **sqlite**: add getter to detect transactions (Colin Ihrig) [#57925](https://github.com/nodejs/node/pull/57925)
* \[[`0835b68f65`](https://github.com/nodejs/node/commit/0835b68f65)] - **sqlite**: add timeout options to DatabaseSync (Edy Silva) [#57752](https://github.com/nodejs/node/pull/57752)
* \[[`23b2bc93d9`](https://github.com/nodejs/node/commit/23b2bc93d9)] - **sqlite**: add setReturnArrays method to StatementSync (Gürgün Dayıoğlu) [#57542](https://github.com/nodejs/node/pull/57542)
* \[[`c5eb6471d6`](https://github.com/nodejs/node/commit/c5eb6471d6)] - **sqlite**: enable common flags (Edy Silva) [#57621](https://github.com/nodejs/node/pull/57621)
* \[[`51557d1c84`](https://github.com/nodejs/node/commit/51557d1c84)] - **sqlite**: refactor prepared statement iterator (Colin Ihrig) [#57569](https://github.com/nodejs/node/pull/57569)
* \[[`b471dde3ff`](https://github.com/nodejs/node/commit/b471dde3ff)] - **sqlite,doc,test**: add aggregate function (Edy Silva) [#56600](https://github.com/nodejs/node/pull/56600)
* \[[`c123d5e9c1`](https://github.com/nodejs/node/commit/c123d5e9c1)] - **sqlite,src**: refactor sqlite value conversion (Edy Silva) [#57571](https://github.com/nodejs/node/pull/57571)
* \[[`badb4f56b8`](https://github.com/nodejs/node/commit/badb4f56b8)] - **src**: improve parsing of boolean options (Edy Silva) [#58039](https://github.com/nodejs/node/pull/58039)
* \[[`a842a150ee`](https://github.com/nodejs/node/commit/a842a150ee)] - **src**: remove unused detachArrayBuffer method (Yagiz Nizipli) [#58055](https://github.com/nodejs/node/pull/58055)
* \[[`b6a02bf9b6`](https://github.com/nodejs/node/commit/b6a02bf9b6)] - **src**: fix internalModuleStat v8 fast path (Yagiz Nizipli) [#58054](https://github.com/nodejs/node/pull/58054)
* \[[`f1e6107d39`](https://github.com/nodejs/node/commit/f1e6107d39)] - **src**: fix EnvironmentOptions.async\_context\_frame default value (Chengzhong Wu) [#58030](https://github.com/nodejs/node/pull/58030)
* \[[`ac2e08bc2e`](https://github.com/nodejs/node/commit/ac2e08bc2e)] - **src**: annotate BaseObjects in the heap snapshots correctly (Joyee Cheung) [#57417](https://github.com/nodejs/node/pull/57417)
* \[[`3e78222457`](https://github.com/nodejs/node/commit/3e78222457)] - **src**: use macros to reduce code duplication is cares\_wrap (James M Snell) [#57937](https://github.com/nodejs/node/pull/57937)
* \[[`f0905d3913`](https://github.com/nodejs/node/commit/f0905d3913)] - **src**: improve error handling in cares\_wrap (James M Snell) [#57937](https://github.com/nodejs/node/pull/57937)
* \[[`95e8249d4f`](https://github.com/nodejs/node/commit/95e8249d4f)] - **src**: use ranges library (C++20) to simplify code (Daniel Lemire) [#57975](https://github.com/nodejs/node/pull/57975)
* \[[`44c2ef660d`](https://github.com/nodejs/node/commit/44c2ef660d)] - **src**: fix -Wunreachable-code-return in node\_sea (Shelley Vohr) [#57664](https://github.com/nodejs/node/pull/57664)
* \[[`5eaa04cdb8`](https://github.com/nodejs/node/commit/5eaa04cdb8)] - **src**: add dcheck\_eq for Object::New constructor calls (Jonas) [#57943](https://github.com/nodejs/node/pull/57943)
* \[[`ca25de94f2`](https://github.com/nodejs/node/commit/ca25de94f2)] - **src**: move windows specific fns to `_WIN32` (Yagiz Nizipli) [#57951](https://github.com/nodejs/node/pull/57951)
* \[[`100d7e00d8`](https://github.com/nodejs/node/commit/100d7e00d8)] - **src**: avoid calling SetPrototypeV2() (Yagiz Nizipli) [#57949](https://github.com/nodejs/node/pull/57949)
* \[[`221637194d`](https://github.com/nodejs/node/commit/221637194d)] - **src**: change DCHECK to CHECK (Wuli Zuo) [#57948](https://github.com/nodejs/node/pull/57948)
* \[[`0a7dd54fe7`](https://github.com/nodejs/node/commit/0a7dd54fe7)] - **src**: improve thread safety of TaskQueue (Shelley Vohr) [#57910](https://github.com/nodejs/node/pull/57910)
* \[[`62230000ca`](https://github.com/nodejs/node/commit/62230000ca)] - **src**: fixup errorhandling more in various places (James M Snell) [#57852](https://github.com/nodejs/node/pull/57852)
* \[[`7da7142b68`](https://github.com/nodejs/node/commit/7da7142b68)] - **src**: fix typo in comments (Edy Silva) [#57868](https://github.com/nodejs/node/pull/57868)
* \[[`d4a212fc35`](https://github.com/nodejs/node/commit/d4a212fc35)] - **src**: update std::vector\<v8::Local\<T>> to use v8::LocalVector\<T> (Aditi) [#57646](https://github.com/nodejs/node/pull/57646)
* \[[`18735df3e4`](https://github.com/nodejs/node/commit/18735df3e4)] - **src**: update std::vector\<v8::Local\<T>> to use v8::LocalVector\<T> (Aditi) [#57642](https://github.com/nodejs/node/pull/57642)
* \[[`bbb9d64a30`](https://github.com/nodejs/node/commit/bbb9d64a30)] - **src**: update std::vector\<v8::Local\<T>> to use v8::LocalVector\<T> (Aditi) [#57578](https://github.com/nodejs/node/pull/57578)
* \[[`959827af55`](https://github.com/nodejs/node/commit/959827af55)] - **src**: migrate from deprecated SnapshotCreator constructor (Joyee Cheung) [#55337](https://github.com/nodejs/node/pull/55337)
* \[[`c8bb3feaa6`](https://github.com/nodejs/node/commit/c8bb3feaa6)] - **src**: improve error message for invalid child stdio type in spawn\_sync (Dario Piotrowicz) [#57589](https://github.com/nodejs/node/pull/57589)
* \[[`60e96c0ecd`](https://github.com/nodejs/node/commit/60e96c0ecd)] - **src**: implement util.types fast API calls (Ruben Bridgewater) [#57819](https://github.com/nodejs/node/pull/57819)
* \[[`b65f4925c9`](https://github.com/nodejs/node/commit/b65f4925c9)] - **src**: enter and lock isolate properly in json parser (Joyee Cheung) [#57823](https://github.com/nodejs/node/pull/57823)
* \[[`9f691e850e`](https://github.com/nodejs/node/commit/9f691e850e)] - **src**: add BaseObjectPtr nullptr operations (Chengzhong Wu) [#56585](https://github.com/nodejs/node/pull/56585)
* \[[`c1edf5aca4`](https://github.com/nodejs/node/commit/c1edf5aca4)] - **src**: remove `void*` -> `char*` -> `void*` casts (Tobias Nießen) [#57791](https://github.com/nodejs/node/pull/57791)
* \[[`d48d24fba2`](https://github.com/nodejs/node/commit/d48d24fba2)] - **src**: improve error handling in `node_env_var.cc` (Antoine du Hamel) [#57767](https://github.com/nodejs/node/pull/57767)
* \[[`8763d7f3c4`](https://github.com/nodejs/node/commit/8763d7f3c4)] - **src**: improve error handling in node\_http2 (James M Snell) [#57764](https://github.com/nodejs/node/pull/57764)
* \[[`02647e2e30`](https://github.com/nodejs/node/commit/02647e2e30)] - **src**: improve error handing in node\_messaging (James M Snell) [#57760](https://github.com/nodejs/node/pull/57760)
* \[[`8a77876c7b`](https://github.com/nodejs/node/commit/8a77876c7b)] - **src**: improve error handling in crypto\_x509 (James M Snell) [#57757](https://github.com/nodejs/node/pull/57757)
* \[[`0de2c64c1f`](https://github.com/nodejs/node/commit/0de2c64c1f)] - **src**: improve error handling in callback.cc (James M Snell) [#57758](https://github.com/nodejs/node/pull/57758)
* \[[`78d81b9bc1`](https://github.com/nodejs/node/commit/78d81b9bc1)] - **src**: improve StringBytes error handling (James M Snell) [#57706](https://github.com/nodejs/node/pull/57706)
* \[[`496a3cba23`](https://github.com/nodejs/node/commit/496a3cba23)] - **src**: initialize privateSymbols for per\_context (Jason Zhang) [#57479](https://github.com/nodejs/node/pull/57479)
* \[[`d3672255e2`](https://github.com/nodejs/node/commit/d3672255e2)] - **src**: improve error handling in process.env handling (James M Snell) [#57707](https://github.com/nodejs/node/pull/57707)
* \[[`23cc162a02`](https://github.com/nodejs/node/commit/23cc162a02)] - **src**: remove unused variable in crypto\_x509.cc (Michaël Zasso) [#57754](https://github.com/nodejs/node/pull/57754)
* \[[`d211a59f3d`](https://github.com/nodejs/node/commit/d211a59f3d)] - **src**: update std::vector\<v8::Local\<T>> to use v8::LocalVector\<T> (Aditi) [#57733](https://github.com/nodejs/node/pull/57733)
* \[[`dcbe427b84`](https://github.com/nodejs/node/commit/dcbe427b84)] - **src**: fix kill signal 0 on Windows (Stefan Stojanovic) [#57695](https://github.com/nodejs/node/pull/57695)
* \[[`2472fd9f2f`](https://github.com/nodejs/node/commit/2472fd9f2f)] - **src**: fixup fs SyncCall to propagate errors correctly (James M Snell) [#57711](https://github.com/nodejs/node/pull/57711)
* \[[`b2ac57af59`](https://github.com/nodejs/node/commit/b2ac57af59)] - **src**: fix inefficient usage of v8\_inspector::StringView (Simon Zünd) [#52372](https://github.com/nodejs/node/pull/52372)
* \[[`887f4d6bdb`](https://github.com/nodejs/node/commit/887f4d6bdb)] - **src**: disable abseil deadlock detection (Chengzhong Wu) [#57582](https://github.com/nodejs/node/pull/57582)
* \[[`edb5c87f4b`](https://github.com/nodejs/node/commit/edb5c87f4b)] - **src**: remove deleted tls file (Shelley Vohr) [#57481](https://github.com/nodejs/node/pull/57481)
* \[[`98186c09d4`](https://github.com/nodejs/node/commit/98186c09d4)] - _**Revert**_ "**src**: do not expose simdjson.h in node\_config\_file.h" (James M Snell) [#57197](https://github.com/nodejs/node/pull/57197)
* \[[`fc90f8871b`](https://github.com/nodejs/node/commit/fc90f8871b)] - **src**: do not expose simdjson.h in node\_config\_file.h (Cheng) [#57173](https://github.com/nodejs/node/pull/57173)
* \[[`ad845588d0`](https://github.com/nodejs/node/commit/ad845588d0)] - _**Revert**_ "**src**: modernize cleanup queue to use c++20" (Richard Lau) [#56846](https://github.com/nodejs/node/pull/56846)
* \[[`581b44421a`](https://github.com/nodejs/node/commit/581b44421a)] - **src**: modernize cleanup queue to use c++20 (Yagiz Nizipli) [#56063](https://github.com/nodejs/node/pull/56063)
* \[[`8fb2130201`](https://github.com/nodejs/node/commit/8fb2130201)] - **src,permission**: make ERR\_ACCESS\_DENIED more descriptive (Rafael Gonzaga) [#57585](https://github.com/nodejs/node/pull/57585)
* \[[`6156f8a6d5`](https://github.com/nodejs/node/commit/6156f8a6d5)] - _**Revert**_ "**stream**: handle generator destruction from Duplex.from()" (jakecastelli) [#56278](https://github.com/nodejs/node/pull/56278)
* \[[`745f48cf7e`](https://github.com/nodejs/node/commit/745f48cf7e)] - **test**: update WPT for WebCryptoAPI to b48efd681e (Node.js GitHub Bot) [#58044](https://github.com/nodejs/node/pull/58044)
* \[[`e8572c919c`](https://github.com/nodejs/node/commit/e8572c919c)] - **test**: add missing newlines to repl .exit writes (Dario Piotrowicz) [#58041](https://github.com/nodejs/node/pull/58041)
* \[[`b083d0fd05`](https://github.com/nodejs/node/commit/b083d0fd05)] - **test**: use validateByRetainingPath in heapdump tests (Joyee Cheung) [#57417](https://github.com/nodejs/node/pull/57417)
* \[[`0c027cded7`](https://github.com/nodejs/node/commit/0c027cded7)] - **test**: add fast api tests for getLibuvNow() (Yagiz Nizipli) [#58022](https://github.com/nodejs/node/pull/58022)
* \[[`416f503135`](https://github.com/nodejs/node/commit/416f503135)] - **test**: add ALS test using http agent keep alive (Gerhard Stöbich) [#58017](https://github.com/nodejs/node/pull/58017)
* \[[`a779de6b48`](https://github.com/nodejs/node/commit/a779de6b48)] - **test**: deflake test-http2-options-max-headers-block-length (Luigi Pinca) [#57959](https://github.com/nodejs/node/pull/57959)
* \[[`e2446ac78e`](https://github.com/nodejs/node/commit/e2446ac78e)] - **test**: rename to getCallSites (Wuli Zuo) [#57948](https://github.com/nodejs/node/pull/57948)
* \[[`9ffdfeff7e`](https://github.com/nodejs/node/commit/9ffdfeff7e)] - **test**: force GC in test-file-write-stream4 (Luigi Pinca) [#57930](https://github.com/nodejs/node/pull/57930)
* \[[`065b4a354c`](https://github.com/nodejs/node/commit/065b4a354c)] - **test**: enable skipped colorize test (Shima Ryuhei) [#57887](https://github.com/nodejs/node/pull/57887)
* \[[`2aef0329bb`](https://github.com/nodejs/node/commit/2aef0329bb)] - **test**: update WPT for WebCryptoAPI to 164426ace2 (Node.js GitHub Bot) [#57854](https://github.com/nodejs/node/pull/57854)
* \[[`bbb50e18c2`](https://github.com/nodejs/node/commit/bbb50e18c2)] - **test**: deflake test-buffer-large-size (jakecastelli) [#57789](https://github.com/nodejs/node/pull/57789)
* \[[`9fc71268e2`](https://github.com/nodejs/node/commit/9fc71268e2)] - **test**: add test for frame count being 0.5 (Jake Yuesong Li) [#57732](https://github.com/nodejs/node/pull/57732)
* \[[`f94e5fc84d`](https://github.com/nodejs/node/commit/f94e5fc84d)] - **test**: fix the decimal fractions explaination (Jake Yuesong Li) [#57732](https://github.com/nodejs/node/pull/57732)
* \[[`ea5e60dba3`](https://github.com/nodejs/node/commit/ea5e60dba3)] - _**Revert**_ "**test**: add tests for REPL custom evals" (Tobias Nießen) [#57793](https://github.com/nodejs/node/pull/57793)
* \[[`33b615babf`](https://github.com/nodejs/node/commit/33b615babf)] - **test**: add tests for REPL custom evals (Dario Piotrowicz) [#57691](https://github.com/nodejs/node/pull/57691)
* \[[`39e38cddda`](https://github.com/nodejs/node/commit/39e38cddda)] - **test**: update expected error message for macOS (Antoine du Hamel) [#57742](https://github.com/nodejs/node/pull/57742)
* \[[`94b4388439`](https://github.com/nodejs/node/commit/94b4388439)] - **test**: fix dangling promise in test\_runner no isolation test setup (Jacob Smith) [#57595](https://github.com/nodejs/node/pull/57595)
* \[[`51ded6eaeb`](https://github.com/nodejs/node/commit/51ded6eaeb)] - **test**: improve test description (jakecastelli) [#56943](https://github.com/nodejs/node/pull/56943)
* \[[`75b9c1cdd8`](https://github.com/nodejs/node/commit/75b9c1cdd8)] - **test**: remove test-macos-app-sandbox flaky designation (Luigi Pinca) [#56471](https://github.com/nodejs/node/pull/56471)
* \[[`72537f5631`](https://github.com/nodejs/node/commit/72537f5631)] - **test**: remove flaky test-pipe-file-to-http designation (Luigi Pinca) [#56472](https://github.com/nodejs/node/pull/56472)
* \[[`984a472137`](https://github.com/nodejs/node/commit/984a472137)] - **test**: remove test-runner-watch-mode-complex flaky designation (Luigi Pinca) [#56470](https://github.com/nodejs/node/pull/56470)
* \[[`23275cc7bc`](https://github.com/nodejs/node/commit/23275cc7bc)] - **test**: add test case for `util.inspect` (Jordan Harband) [#55778](https://github.com/nodejs/node/pull/55778)
* \[[`14ef36e834`](https://github.com/nodejs/node/commit/14ef36e834)] - **test\_runner**: support mocking json modules (Jacob Smith) [#58007](https://github.com/nodejs/node/pull/58007)
* \[[`e47b4630ef`](https://github.com/nodejs/node/commit/e47b4630ef)] - **test\_runner**: recalculate run duration on watch restart (Pietro Marchini) [#57786](https://github.com/nodejs/node/pull/57786)
* \[[`b4908e334a`](https://github.com/nodejs/node/commit/b4908e334a)] - **test\_runner**: match minimum file column to 'all files' (Shima Ryuhei) [#57848](https://github.com/nodejs/node/pull/57848)
* \[[`c4a1601817`](https://github.com/nodejs/node/commit/c4a1601817)] - **test\_runner**: improve --test-timeout to be per test (jakecastelli) [#57672](https://github.com/nodejs/node/pull/57672)
* \[[`74e6553ec6`](https://github.com/nodejs/node/commit/74e6553ec6)] - **tools**: enable CodeQL config file (Rich Trott) [#58036](https://github.com/nodejs/node/pull/58036)
* \[[`d6a9a8be3d`](https://github.com/nodejs/node/commit/d6a9a8be3d)] - **tools**: ignore test directory in CodeQL scans (Rich Trott) [#57978](https://github.com/nodejs/node/pull/57978)
* \[[`cd4cd35b16`](https://github.com/nodejs/node/commit/cd4cd35b16)] - **tools**: add semver-major release support to release-lint (Antoine du Hamel) [#57892](https://github.com/nodejs/node/pull/57892)
* \[[`3793c8f281`](https://github.com/nodejs/node/commit/3793c8f281)] - **tools**: add codeql nightly (Rafael Gonzaga) [#57788](https://github.com/nodejs/node/pull/57788)
* \[[`498da23ddf`](https://github.com/nodejs/node/commit/498da23ddf)] - **tools**: edit create-release-proposal workflow to handle pr body length (Elves Vieira) [#57841](https://github.com/nodejs/node/pull/57841)
* \[[`1d6f39c0d4`](https://github.com/nodejs/node/commit/1d6f39c0d4)] - **tools**: add zstd updater to workflow (KASEYA\yahor.siarheyenka) [#57831](https://github.com/nodejs/node/pull/57831)
* \[[`1425bdd25d`](https://github.com/nodejs/node/commit/1425bdd25d)] - **tools**: remove unused `osx-pkg-postinstall.sh` (Antoine du Hamel) [#57667](https://github.com/nodejs/node/pull/57667)
* \[[`43d326c39b`](https://github.com/nodejs/node/commit/43d326c39b)] - **tools**: do not use temp files when merging PRs (Antoine du Hamel) [#57790](https://github.com/nodejs/node/pull/57790)
* \[[`3d7825bf37`](https://github.com/nodejs/node/commit/3d7825bf37)] - **tools**: update gyp-next to 0.20.0 (Node.js GitHub Bot) [#57683](https://github.com/nodejs/node/pull/57683)
* \[[`a69c2cef2c`](https://github.com/nodejs/node/commit/a69c2cef2c)] - **tools**: update doc to new version (Node.js GitHub Bot) [#57769](https://github.com/nodejs/node/pull/57769)
* \[[`1d4bb4da6f`](https://github.com/nodejs/node/commit/1d4bb4da6f)] - **tools**: bump the eslint group in /tools/eslint with 4 updates (dependabot\[bot]) [#57721](https://github.com/nodejs/node/pull/57721)
* \[[`8f709f6d21`](https://github.com/nodejs/node/commit/8f709f6d21)] - **tools**: enable linter in `test/fixtures/source-map/output` (Antoine du Hamel) [#57700](https://github.com/nodejs/node/pull/57700)
* \[[`1c0b900c10`](https://github.com/nodejs/node/commit/1c0b900c10)] - **tools**: enable linter in `test/fixtures/errors` (Antoine du Hamel) [#57701](https://github.com/nodejs/node/pull/57701)
* \[[`392fe2ffa2`](https://github.com/nodejs/node/commit/392fe2ffa2)] - **tools**: enable linter in `test/fixtures/test-runner/output` (Antoine du Hamel) [#57698](https://github.com/nodejs/node/pull/57698)
* \[[`6addbdbf3c`](https://github.com/nodejs/node/commit/6addbdbf3c)] - **tools**: enable linter in `test/fixtures/eval` (Antoine du Hamel) [#57699](https://github.com/nodejs/node/pull/57699)
* \[[`eeb3e23938`](https://github.com/nodejs/node/commit/eeb3e23938)] - **tools**: enable linter on some fixtures file (Antoine du Hamel) [#57674](https://github.com/nodejs/node/pull/57674)
* \[[`f11293e354`](https://github.com/nodejs/node/commit/f11293e354)] - **tools**: update ESLint to 9.23 (Antoine du Hamel) [#57673](https://github.com/nodejs/node/pull/57673)
* \[[`9192964cba`](https://github.com/nodejs/node/commit/9192964cba)] - **tools**: update doc to new version (Node.js GitHub Bot) [#57085](https://github.com/nodejs/node/pull/57085)
* \[[`b1ee186a62`](https://github.com/nodejs/node/commit/b1ee186a62)] - **tools**: update doc to new version (Node.js GitHub Bot) [#51192](https://github.com/nodejs/node/pull/51192)
* \[[`be34b5e7fc`](https://github.com/nodejs/node/commit/be34b5e7fc)] - **tools**: disable doc building when ICU is not available (Antoine du Hamel) [#51192](https://github.com/nodejs/node/pull/51192)
* \[[`2f36e80973`](https://github.com/nodejs/node/commit/2f36e80973)] - **url**: improve canParse() performance for non-onebyte strings (Yagiz Nizipli) [#58023](https://github.com/nodejs/node/pull/58023)
* \[[`ab5ae9e53a`](https://github.com/nodejs/node/commit/ab5ae9e53a)] - **util**: fix parseEnv handling of invalid lines (Augustin Mauroy) [#57798](https://github.com/nodejs/node/pull/57798)
* \[[`8b2c17c9d2`](https://github.com/nodejs/node/commit/8b2c17c9d2)] - **util**: fix formatting of objects with built-in Symbol.toPrimitive (Shima Ryuhei) [#57832](https://github.com/nodejs/node/pull/57832)
* \[[`5783d3a6b9`](https://github.com/nodejs/node/commit/5783d3a6b9)] - **util**: preserve `length` of deprecated functions (Livia Medeiros) [#57806](https://github.com/nodejs/node/pull/57806)
* \[[`64b32997db`](https://github.com/nodejs/node/commit/64b32997db)] - **util**: fix parseEnv incorrectly splitting multiple ‘=‘ in value (HEESEUNG) [#57421](https://github.com/nodejs/node/pull/57421)
* \[[`e577618227`](https://github.com/nodejs/node/commit/e577618227)] - **util**: inspect: enumerable Symbols no longer have square brackets (Jordan Harband) [#55778](https://github.com/nodejs/node/pull/55778)
* \[[`24cf97695c`](https://github.com/nodejs/node/commit/24cf97695c)] - **watch**: clarify completion/failure watch mode messages (Dario Piotrowicz) [#57926](https://github.com/nodejs/node/pull/57926)
* \[[`2aa957a1e2`](https://github.com/nodejs/node/commit/2aa957a1e2)] - **watch**: check parent and child path properly (Jason Zhang) [#57425](https://github.com/nodejs/node/pull/57425)
* \[[`cddf7aada0`](https://github.com/nodejs/node/commit/cddf7aada0)] - **win**: fix SIGQUIT on ClangCL (Stefan Stojanovic) [#57659](https://github.com/nodejs/node/pull/57659)
* \[[`628ad93f7f`](https://github.com/nodejs/node/commit/628ad93f7f)] - **worker**: add ESM version examples to worker docs (fisker Cheung) [#57645](https://github.com/nodejs/node/pull/57645)
* \[[`226237d4ed`](https://github.com/nodejs/node/commit/226237d4ed)] - **zlib**: fix pointer alignment (jhofstee) [#57727](https://github.com/nodejs/node/pull/57727)
