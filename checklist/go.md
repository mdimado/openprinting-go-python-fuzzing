# Fuzzing Harness Checklist

## 1. Function Understanding

* [ ] What does the function do?
* [ ] Is it exposed to untrusted or external input?
* [ ] Can malformed input cause panics, hangs, or undefined behavior?

## 2. Input Analysis

* [ ] What input types does the function accept (`[]byte`, `string`, `io.Reader`, struct, etc.)?
* [ ] Can fuzz input be used directly or needs conversion?
* [ ] Is the function a method on a struct (requires receiver setup)?

## 3. Preconditions and Guards

* [ ] Are there minimum input length requirements?
* [ ] Does the function handle nil or empty input safely?
* [ ] Are there format expectations (e.g., UTF-8, structured binary)?

## 4. Harness Construction

* [ ] Use `f.Fuzz(func(t *testing.T, data []byte) { ... })` for fuzzing.
* [ ] Wrap input as needed (e.g., `bytes.NewReader(data)`).
* [ ] Construct required struct instances.
* [ ] Call the target function with fuzzed input.
* [ ] Do not treat errors as test failures unless they indicate a crash or violation.

## 5. Crash Safety

* [ ] The function must not panic on any input.
* [ ] Avoid I/O, network, or non-deterministic side effects.

## 6. Behavior Verification (Optional)

* [ ] Does `Decode(Encode(x)) == x` or other invariant hold?
* [ ] Is the function deterministic?
* [ ] Are logical properties (e.g., idempotence) preserved?

## 7. Seed Inputs (Optional)

* [ ] Add known valid examples with `f.Add(...)`.
* [ ] Include malformed but interesting edge cases.
* [ ] Ensure corpus diversity to improve fuzzing coverage.

## 8. Output and Logging

* [ ] Suppress logging or printing during fuzzing.
* [ ] Ensure output does not depend on or leak internal state.

