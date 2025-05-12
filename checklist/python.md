# Fuzzing Harness Checklist for Python

## 1. Function Understanding

* [ ] What does the function do?
* [ ] Is it exposed to external or untrusted input?
* [ ] Can it crash, raise unhandled exceptions, or hang?

## 2. Input Type Mapping

* [ ] What input does the function expect (`str`, `bytes`, `dict`, etc.)?
* [ ] Can fuzz data be passed directly or does it require decoding?
* [ ] Does the function rely on I/O or environment setup?

## 3. Input Guards

* [ ] Add checks for minimum input length if required.
* [ ] Ensure inputs are well-formed if the function requires it (e.g., valid JSON, UTF-8).
* [ ] Catch and ignore expected exceptions (e.g., `ValueError`, `TypeError`).

## 4. Harness Construction

* [ ] Use `atheris.Setup()` with a function of signature `def TestOneInput(data: bytes)`.
* [ ] Convert or parse `data` to the expected input format.
* [ ] Wrap the target function call inside `try` blocks if needed.
* [ ] Avoid printing or logging unless debugging.

## 5. Crash and Exception Safety

* [ ] Ensure the function does not crash the interpreter.
* [ ] Catch unexpected exceptions and report if needed.
* [ ] Avoid side-effects like file I/O or network requests.

## 6. Property Checks (Optional)

* [ ] Does parsing then serializing yield the same result?
* [ ] Is output deterministic?
* [ ] Are key invariants or constraints respected?

## 7. Seed Corpus (Optional)

* [ ] Use `atheris.FuzzedDataProvider` with meaningful seeds.
* [ ] Add well-formed and malformed inputs to improve coverage.
* [ ] Consider edge cases and known problematic formats.

## 8. Performance and Logging

* [ ] Disable expensive operations unless needed.
* [ ] Remove `print()` or debug logs to avoid slowdowns.
* [ ] Use coverage tools to assess fuzz effectiveness.

