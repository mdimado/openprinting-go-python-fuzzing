## Integrating OSS-Fuzz for Go-Based and Python-Based OpenPrinting Projects

This project aims to integrate OSS-Fuzz into key OpenPrinting projects written in Go and Python to improve their security and robustness through fuzz testing. Fuzzing helps identify bugs, crashes, and memory issues by continuously feeding programs with unexpected or malformed inputs.

OpenPrinting maintains several critical components used in modern, driverless printing systems. However, some of these projects lack extensive test or fuzz coverage. This GSoC effort introduces modern fuzzing techniques using Go fuzzing and Python’s Atheris to systematically test these projects.

#### Goals:
Improve security and reliability of OpenPrinting projects by:
- [ ] Writing fuzzers for key components in:
  - [goipp](https://github.com/OpenPrinting/goipp) – IPP protocol in Go
  - [ipp-usb](https://github.com/OpenPrinting/ipp-usb) – USB-over-IPP service for printers
  - [pycups](https://github.com/OpenPrinting/pycups) – Python bindings wrapping the CUPS API
  - [pyppd](https://github.com/OpenPrinting/pyppd) – PPD archive generator and decompressor
- [ ] Creating seed corpora to guide fuzzing.
- [ ] Integrating each project into OSS-Fuzz with build scripts and Docker configurations.

#### Next steps:
- [Understanding the goipp project](https://github.com/mdimado/openprinting-go-python-fuzzing/blob/main/goipp.md)
- [Understanding the ipp-usb project](https://github.com/mdimado/openprinting-go-python-fuzzing/blob/main/goipp.md)
- [Understanding the pycups project](https://github.com/mdimado/openprinting-go-python-fuzzing/blob/main/goipp.md)
- [Understanding the pyppd project](https://github.com/mdimado/openprinting-go-python-fuzzing/blob/main/goipp.md)

