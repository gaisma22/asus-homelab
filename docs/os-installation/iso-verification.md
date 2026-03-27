# ISO Verification

## ISO Downloaded
- File: debian-12.12.0-i386-netinst.iso
- Source: https://cdimage.debian.org/cdimage/archive/12.12.0/i386/iso-cd/
- Architecture: i386 (32-bit) — required for Intel Atom N270

## Verification Method
- Downloaded SHA512SUMS from same server directory
- Ran: sha512sum -c SHA512SUMS --ignore-missing
- Result: OK

## Why This Matters
A checksum mismatch means either corrupted download or tampered file.
Never flash an unverified ISO to hardware.
