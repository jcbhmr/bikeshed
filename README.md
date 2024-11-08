# Bikeshed prebuilt

🚲 Bundles [Bikeshed](https://speced.github.io/bikeshed/) for use without Python or pip \
🔀 Forked from [speced/bikeshed](https://github.com/speced/bikeshed)

<p align=center>
  <a href="https://github.com/jcbhmr/bikeshed/releases/latest"><img src="https://github.com/user-attachments/assets/5ac85fe1-d904-4f24-9c4a-7788557305e4"></a>
</p>

<p align=center>
  <a href="https://github.com/jcbhmr/bikeshed/releases">GitHub releases (this project)</a>
  | <a href="https://speced.github.io/bikeshed/">Official Bikeshed website</a>
</p>

🐍 Uses [PyInstaller](https://pyinstaller.org/en/stable/) \
🏭 Compiles [the `bikeshed` PyPI package](https://pypi.org/project/bikeshed/) to a standalone program \
[🚚 Distributed via GitHub releases](https://github.com/jcbhmr/bikeshed/releases) \
💻 Builds for Windows, macOS, and Linux \
🌌 Bundled as a single [actually portable executable](https://justine.lol/ape.html)

## Installation

![Windows](https://img.shields.io/static/v1?style=for-the-badge&message=Windows&color=0078D4&logo=Windows&logoColor=FFFFFF&label=)
![Linux](https://img.shields.io/static/v1?style=for-the-badge&message=Linux&color=222222&logo=Linux&logoColor=FCC624&label=)
![macOS](https://img.shields.io/static/v1?style=for-the-badge&message=macOS&color=000000&logo=macOS&logoColor=FFFFFF&label=)

🛑 If possible you should **install Bikeshed directly from [the `bikeshed` PyPI package](https://pypi.org/project/bikeshed/)** as is [officially recommended](https://speced.github.io/bikeshed/#install-final).

```sh
pipx install bikeshed
```

You can get Bikeshed builds built by this bikeshed-builder project from [the GitHub releases tab](https://github.com/jcbhmr/bikeshed/releases). These are unofficial.

This project is intended to be used & integrated with software that works better without the Python & pip requirements that the official Bikeshed distribution method uses. You can also use it as a standalone way to install Bikeshed without a Python environment. For example an npm redistribution of the Bikeshed project to be `npm install <bikeshed_package_name>` would not want to require a particular Python environment. Instead, they would opt for a premade all-in-one binary/package such as the PyInstaller bikeshed released by this project! 😊

Here are the relevant URLs that you would use in your code to fetch releases from this project:

```
https://github.com/jcbhmr/bikeshed/releases/download/v4.2.3/bikeshed-linux_x86_64-4.1.12.tar.gz
https://github.com/jcbhmr/bikeshed/releases/download/v4.2.3/bikeshed-macosx_10_9_x86_64-4.1.12.tar.gz
https://github.com/jcbhmr/bikeshed/releases/download/v4.2.3/bikeshed-macosx_11_0_arm64-4.1.12.tar.gz
https://github.com/jcbhmr/bikeshed/releases/download/v4.2.3/bikeshed-win_amd64-4.1.12.zip
https://github.com/jcbhmr/bikeshed/releases/download/v4.2.3/bikeshed-ape-4.1.12.zip
```

In addition to the PyInstaller tarballs there's also an [actually portable executable](https://justine.lol/ape.html) (APE) that bundles the Windows, macOS (x86-64 & AArch64), and Linux binaries into a single multiplatform executable.

Programs are encouraged to pin an exact version of Bikeshed and then update Bikeshed as a dependency as opposed to always fetching the latest Bikeshed release binaries.

[📚 Read the Bikeshed documentation for how to use the `bikeshed` CLI](https://speced.github.io/bikeshed/)

## Development

![Python](https://img.shields.io/static/v1?style=for-the-badge&message=Python&color=3776AB&logo=Python&logoColor=FFFFFF&label=)
![GitHub Actions](https://img.shields.io/static/v1?style=for-the-badge&message=GitHub+Actions&color=2088FF&logo=GitHub+Actions&logoColor=FFFFFF&label=)

This is a friendly fork🔀 of [speced/bikeshed](https://github.com/speced/bikeshed). I don't know if upstream wants to host prebuilt binaries. 🤷‍♀️ This project is a small patch (hopefully) that should build each Bikeshed CLI version and publish some sweet precompiled binaries.

Bikeshed doesn't do release tags. Make sure to manually watch [the release notes issue](https://github.com/speced/bikeshed/issues/1773) and then merge any changes into this fork.

To create a release of this project:

1. Run the "Create release" workflow manually. Choose `draft: true`.
4. Check the draft release using the GitHub web UI. If it looks good, publish it!
6. Update the copyable URLs in the Usage section.

TODO: [I need some assistance in handling non-zero exit codes and process signals properly in Windows.](https://github.com/jcbhmr/bikeshed/blob/56d3c38789064c84101633302547a265e36a2a79/bikeshed-ape.cpp#L109) If anyone reading this knows how to `waitpid()` correctly please enlighten me! ☺️

---

Bikeshed, a spec preprocessor
=============================

<img src="https://raw.githubusercontent.com/speced/bikeshed/main/bikeshed.svg" width=100 height=100 align=left>

Bikeshed is a pre-processor for spec documents,
turning a source document
(containing only the actual spec content, plus several shorthands for linking to terms and other things)
into a final spec document,
with appropriate boilerplate, bibliography, indexes, etc all filled in.
It's used on specs for CSS and many other W3C working groups,
WHATWG,
the C++ standards committee,
and elsewhere!

![CI](https://github.com/speced/bikeshed/workflows/CI/badge.svg)
[![Gitter](https://img.shields.io/badge/Gitter-Join%20Chat%20↣-blue.svg)](https://gitter.im/tabatkins/bikeshed?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)
[![Docs](https://img.shields.io/badge/docs-available-orange.svg)](https://speced.github.io/bikeshed)
[![Release Notes](https://img.shields.io/badge/release-notes-purple.svg)](https://github.com/speced/bikeshed/issues/1773)

The processor can be easily [installed](https://speced.github.io/bikeshed/#installing) and run locally (requiring no
network access unless you're updating), or accessed as a CGI without any installation at all: <https://api.csswg.org/bikeshed/>

A short overview of some of Bikeshed's features:

* [automatic linking](https://speced.github.io/bikeshed/#autolinking) of terms to their definitions based on text, so you can simple write `Use <a>some term</a> to...` and have it automatically link to the `<dfn>some term</dfn>` elsewhere in the document, or in another spec entirely!
* [automatic id generation](https://speced.github.io/bikeshed/#id-gen) for headings and definitions, based on their text.
* [textual shortcuts for autolinks](https://speced.github.io/bikeshed/#autolink-shortcuts): [[FOO]] for bibliography entries, &lt;&lt;foo>> for grammar productions, 'foo' for CSS property names, {{foo}} for IDL terms, and more.
* [boilerplate generation](https://speced.github.io/bikeshed/#boilerplate), both wholesale and piecemeal.
* [Bikeshed-flavored Markdown](https://speced.github.io/bikeshed/#markdown), a slight variant that is extra-friendly to intermixing with normal HTML. (Besides the few intentional divergences, compliance with [CommonMark](https://commonmark.org) is expected.)
* a [compact syntax](https://speced.github.io/bikeshed/#table-expansion) for writing property-definition tables.
* [automatic whitespace-prefix stripping](https://speced.github.io/bikeshed/#pre-whitespace-stripping) from `<pre>` contents, so the contents can be indented properly in your HTML.
* [automatic IDL processing and syntax-checking](https://speced.github.io/bikeshed/#idl) for `<pre class=idl>` contents, so you don't have to mark up every single significant term yourself.
* [automatic generation of railroad diagrams](https://speced.github.io/bikeshed/#railroad) from `<pre class='railroad'>` contents.

Documentation Sections
----------------------

The full Bikeshed documentation is generated by Bikeshed and [accessible here](https://speced.github.io/bikeshed/).

Note About Fatal Errors
-----------------------

Bikeshed generates "fatal errors" for lots of things that it wants you to fix,
but generally recovers gracefully from them anyway.
If you're getting a fatal error,
but don't have time to fix it and just need a spec **right now**,
you can force Bikeshed to generate anyway with the `-f` flag, like: `bikeshed -f spec`.

This is also sometimes useful when converting a spec to Bikeshed for the first time,
so you can see all the errors at once and fix them in whatever order is easiest,
rather than having to deal with them one-by-one with no idea when they'll end.
(You may also want to silence the warnings in this case,
to reduce visual noise until you've gotten it at least building successfully.
Use `bikeshed -qf spec`.)

Bikeshed File Extension
-----------------------

The preferred file extensions for Bikeshed source files is `bs`, like `index.bs`.
Bikeshed will automatically recognize `*.bs` files in the folder it's run in,
and assume that you want an output file of the same name with a `.html` extension.
The repository also contains a syntax highlighting script for Bikeshed source files.

(Bikeshed also recognizes files with `*.src.html` for backwards compatibility with older CSS specs,
though most such specs have switched their source file extensions to `.bs` now.
Using `.src.html` in most text editors will display the file with HTML source formatting,
which isn't generally what you want.)

License
-------

This document and all associated files in the github project are licensed under [CC0](https://creativecommons.org/publicdomain/zero/1.0/) ![](https://licensebuttons.net/p/zero/1.0/80x15.png).
This means you can reuse, remix, or otherwise appropriate this project for your own use **without restriction**.
(The actual legal meaning can be found at the above link.)
Don't ask me for permission to use any part of this project, **just use it**.
I would appreciate attribution, but that is not required by the license.
