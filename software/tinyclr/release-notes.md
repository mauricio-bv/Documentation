# Release Notes
---
![TinyCLR Logo](images/tinyclr-logo-noborder.jpg)

## 2.0.0-preview2 update

### Released 2020-01-31
A refresh release of the firmware only with improved performance.

#### Changes
- Considerably faster execution speed.

#### Known Issues
- See the 2.0.0-preview2 release notes.
- This 2.0.0.21000 release activates all accelerators which might cause some bugs. If you have any strange behavior, please load the previous 2.0.0.20000 release and see if that fixes your issue. Both firmware versions are identical otherwise, and both run with same 2.0.0-preview2 NuGet packages.

## 2.0.0-preview2

### Released 2020-01-22
Initial insider release for SITCore hardware.

### Visual Studio Project System

#### Changes
- First release to private insiders with major changes.

#### Known Issues
- Cannot change boards or connect an additional board to your PC while Visual Studio is open, or Visual Studio will get confused and deployment will stop working. Do not switch devices while Visual Studio is open.
- Not digitally signed.

### Libraries

#### Changes
- First release to private insiders with major changes.

#### Known Issues
- None, still going through final testing.
- Cryptography and hashing are currently only supported through TLS. We are still planning how to securely expose this functionality.
- Not digitally signed.

### TinyCLR Config

#### Changes
- First release to private insiders with major changes.

#### Known Issues
- TinyCLR may not work when connecting over UART. Use Tera Term to update firmware when in UART mode.
- Not digitally signed.

### TinyCLR Font Converter

#### Changes
- None.

#### Known Issues
- None.
- Not digitally signed.

### Firmware

#### Changes
- First release to private insiders with major changes.

#### Known Issues
- TinyCLR OS is not yet optimized for full performance as this release is focused on stability.
- Conversion from enum to string (enumObject.ToString()) may fail.
- PulseFeedback DrainDuration does not work when going from low to high.
- Not digitally signed.

## 2.0.0-preview1

### Released 2019-12-09
A preview of the new API and available features.

### Libraries

#### Changes
- Major changes.

#### Known Issues
- Still going through complete testing.

### Firmware

#### Changes
- Major changes.

#### Known Issues
- Internal use only.

### TinyCLR Config

#### Changes
- None.

#### Known Issues
- Random crash.
