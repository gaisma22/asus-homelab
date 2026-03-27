# ISO Verification

## ISO Downloaded
- File: `debian-12.12.0-i386-netinst.iso`
- Source: `https://cdimage.debian.org/cdimage/archive/12.12.0/i386/iso-cd/`
- Architecture: `i386` (32-bit) — required for `Intel Atom N270`

## Why i386 and not amd64
The `Atom N270` is a 32-bit processor. A 64-bit OS sends instructions
the CPU has no circuitry to decode. The system would halt before the
OS even starts loading. Architecture has to match the hardware.

## Verification Method
- Downloaded `SHA512SUMS` from the same server directory using `wget`
- Command: `sha512sum -c SHA512SUMS --ignore-missing`
- Result: `OK`

## Why Verify
`wget` only confirms the transfer completed. It does not check whether
the file content is correct. A single corrupted byte changes the hash
completely. Flashing an unverified ISO to hardware is bad practice.
