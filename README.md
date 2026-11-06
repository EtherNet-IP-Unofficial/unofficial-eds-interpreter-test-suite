# Unofficial EDS Interpreter Test Suite

A collection of EDS (Electronic Data Sheet) test files for verifying how EDS interpreters parse and display EDS content.

> [!IMPORTANT]
> **This is not an official ODVA test suite.** These files are not an ODVA publication and are not endorsed or maintained by ODVA. They do not replace ODVA conformance testing, and passing these tests does not imply compliance with the CIP Networks Library specifications.

## Purpose

There are currently no official ODVA test files for EDS interpreters. This repository provides a set of EDS files, each focused on a specific set of EDS keywords or data types, so that developers of EDS interpreters can:

- Check that their tool parses EDS keywords correctly
- Check that values, data types, and structures are displayed as defined in the EDS
- Compare behavior across different tools using the same input files

## Repository contents

```
.
├── README.md        This file
├── TEST_CASES.md    Description of each test case and what it verifies
└── eds/             The EDS test files
```

## Test coverage

The test suite currently covers:

- **Minimal requirements:** an EDS file with only the required keywords
- **ParamN entries:** individual tests for BOOL, SINT, INT, DINT, USINT, UINT, and UDINT, plus a combined test of all CIP elementary data types from BOOL (0xC1) to TIME (0xDB)
- **EnumN entries:** enumerated values for integer and bit string data types
- **AssemN entries:** assemblies built from each integer data type, plus mixed aligned and unaligned assemblies
- **Configuration assemblies:** an aligned target configuration assembly, and Indirect Parameter References (Descriptor bit 10) where configuration parameters select the members of the T→O assembly, including a value of 0 (no reference) and referenced parameters of different sizes

See [TEST_CASES.md](TEST_CASES.md) for a full description of each test case.

## Using the test files

1. Load an EDS file from the [`eds/`](eds/) folder into the EDS interpreter under test.
2. Look up the test case in [TEST_CASES.md](TEST_CASES.md) by EDS file name.
3. Check that the tool's behavior matches each item listed under "Verifies that."

Some test cases also involve a reference implementation of the device, which exchanges I/O data with the tool. This makes it possible to check that the tool decodes T→O data correctly and delivers configuration data as expected.

## File naming convention

Each EDS file name is built from the device identity in hexadecimal, in the form `VVVVTTTTCCCCMMmm.eds` (Vendor ID, Product Type, Product Code, major revision, minor revision). For example, `0018002B00140100.eds` is Vendor ID 24, Product Type 43 (Generic Device), Product Code 20, revision 1. The minor revision is always `00`, because it doesn't affect anything related to the use of the EDS file.

All test files use Vendor ID 24 and Product Type 43 (Generic Device), and each test case has its own unique Product Code.

## Contributing

Issues and pull requests are welcome, whether you've found an error in a test file, have an idea for a new test case, or have seen an interpreter behave in an unexpected way. When adding a test case, include:

- The EDS file in the `eds/` folder, named according to the convention above, using the next free Product Code
- A matching section in [TEST_CASES.md](TEST_CASES.md)

## Trademarks

CIP™, EtherNet/IP™, and DeviceNet™ are trademarks of ODVA, Inc. Use of these names does not imply endorsement by ODVA.
