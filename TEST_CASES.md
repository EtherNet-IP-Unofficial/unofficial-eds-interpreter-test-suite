# EDS Test Cases

This document describes the EDS (Electronic Data Sheet) test files used to verify how a tool parses and displays EDS content. Each test case has its own EDS file, located in the [`eds/`](eds/) folder, and focuses on a specific set of EDS keywords or data types.

## File naming convention

Each EDS file name is built from the device identity in hexadecimal, in the form `VVVVTTTTCCCCMMmm.eds`:

| Part | Meaning | Example (`0018002B00140100.eds`) |
|---|---|---|
| `VVVV` | Vendor ID | `0018` = 24 (ODVA Inc) |
| `TTTT` | Product Type | `002B` = 43 (Generic Device) |
| `CCCC` | Product Code | `0014` = 20 |
| `MM` | Major revision | `01` = 1 |
| `mm` | Minor revision | `00` = the minor revision doesn't affect anything related to the use of the EDS file |

## Test cases

- [Minimal Requirements](#minimal-requirements)
- [Param BOOL](#param-bool)
- [Param USINT](#param-usint)
- [Param UINT](#param-uint)
- [Param UDINT](#param-udint)
- [Param SINT](#param-sint)
- [Param INT](#param-int)
- [Param DINT](#param-dint)
- [Param All Data Types](#param-all-data-types)
- [Param Enumeration](#param-enumeration)
- [Assem SINT](#assem-sint)
- [Assem USINT](#assem-usint)
- [Assem INT](#assem-int)
- [Assem UINT](#assem-uint)
- [Assem DINT](#assem-dint)
- [Assem UDINT](#assem-udint)
- [Assem Mix Aligned](#assem-mix-aligned)
- [Assem Mix Unaligned](#assem-mix-unaligned)

---

## Minimal Requirements

| Field | Value |
|---|---|
| EDS file | [`0018002B00010100.eds`](eds/0018002B00010100.eds) |
| Vendor ID | 24 |
| Product Type | 43 |
| Product Code | 1 |

### Description

Tests an EDS file that contains only the bare minimum of required keywords for a device EDS file, with no optional sections or keywords.

Verifies that:

- The tool parses the file without errors or warnings.
- The required `[File]` section keywords (DescText, CreateDate, CreateTime, ModDate, ModTime, and Revision) are read and displayed correctly.
- The required `[Device]` section keywords (VendCode, VendName, ProdType, ProdTypeStr, ProdCode, MajRev, MinRev, and ProdName) are read and displayed correctly.
- The tool doesn't depend on any optional sections or keywords, and doesn't report their absence as an error.

---

## Param BOOL

| Field | Value |
|---|---|
| EDS file | [`0018002B00020100.eds`](eds/0018002B00020100.eds) |
| Vendor ID | 24 |
| Product Type | 43 |
| Product Code | 2 |

### Description

Tests the use of ParamN entry keywords with data type BOOL (0xC1).

Verifies that:

- The tool correctly parses the parameter definition.
- The full value range (0–1) is displayed correctly, including default values.
- The data type is shown as BOOL with a data size of 1 byte.
- The parameter name, units, and help string are displayed as defined in the EDS.

---

## Param USINT

| Field | Value |
|---|---|
| EDS file | [`0018002B00030100.eds`](eds/0018002B00030100.eds) |
| Vendor ID | 24 |
| Product Type | 43 |
| Product Code | 3 |

### Description

Tests the use of ParamN entry keywords with data type USINT (0xC6).

Verifies that:

- The tool correctly parses the parameter definition.
- The full value range (0–255) is displayed correctly, including the minimum, maximum, and default values.
- Values specified in hexadecimal notation (0x00–0xFF) are parsed correctly and displayed as their equivalent values.
- The data type is shown as USINT with a data size of 1 byte.
- The parameter name, units, and help string are displayed as defined in the EDS.

---

## Param UINT

| Field | Value |
|---|---|
| EDS file | [`0018002B00040100.eds`](eds/0018002B00040100.eds) |
| Vendor ID | 24 |
| Product Type | 43 |
| Product Code | 4 |

### Description

Tests the use of ParamN entry keywords with data type UINT (0xC7).

Verifies that:

- The tool correctly parses the parameter definition.
- The full value range (0–65535) is displayed correctly, including the minimum, maximum, and default values.
- Values specified in hexadecimal notation (0x0000–0xFFFF) are parsed correctly and displayed as their equivalent values.
- The data type is shown as UINT with a data size of 2 bytes.
- The parameter name, units, and help string are displayed as defined in the EDS.

---

## Param UDINT

| Field | Value |
|---|---|
| EDS file | [`0018002B00050100.eds`](eds/0018002B00050100.eds) |
| Vendor ID | 24 |
| Product Type | 43 |
| Product Code | 5 |

### Description

Tests the use of ParamN entry keywords with data type UDINT (0xC8).

Verifies that:

- The tool correctly parses the parameter definition.
- The full value range (0–4294967295) is displayed correctly, including the minimum, maximum, and default values.
- Values specified in hexadecimal notation (0x00000000–0xFFFFFFFF) are parsed correctly and displayed as their equivalent values.
- The data type is shown as UDINT with a data size of 4 bytes.
- The parameter name, units, and help string are displayed as defined in the EDS.

---

## Param SINT

| Field | Value |
|---|---|
| EDS file | [`0018002B00060100.eds`](eds/0018002B00060100.eds) |
| Vendor ID | 24 |
| Product Type | 43 |
| Product Code | 6 |

### Description

Tests the use of ParamN entry keywords with data type SINT (0xC2).

Verifies that:

- The tool correctly parses the parameter definition.
- The full signed value range (−128 to 127) is displayed correctly, including the minimum, maximum, and default values.
- Negative values are displayed with the correct sign.
- The data type is shown as SINT with a data size of 1 byte.
- The parameter name, units, and help string are displayed as defined in the EDS.

---

## Param INT

| Field | Value |
|---|---|
| EDS file | [`0018002B00070100.eds`](eds/0018002B00070100.eds) |
| Vendor ID | 24 |
| Product Type | 43 |
| Product Code | 7 |

### Description

Tests the use of ParamN entry keywords with data type INT (0xC3).

Verifies that:

- The tool correctly parses the parameter definition.
- The full signed value range (−32768 to 32767) is displayed correctly, including the minimum, maximum, and default values.
- Negative values are displayed with the correct sign.
- The data type is shown as INT with a data size of 2 bytes.
- The parameter name, units, and help string are displayed as defined in the EDS.

---

## Param DINT

| Field | Value |
|---|---|
| EDS file | [`0018002B00080100.eds`](eds/0018002B00080100.eds) |
| Vendor ID | 24 |
| Product Type | 43 |
| Product Code | 8 |

### Description

Tests the use of ParamN entry keywords with data type DINT (0xC4).

Verifies that:

- The tool correctly parses the parameter definition.
- The full signed value range (−2147483648 to 2147483647) is displayed correctly, including the minimum, maximum, and default values.
- Negative values are displayed with the correct sign.
- The data type is shown as DINT with a data size of 4 bytes.
- The parameter name, units, and help string are displayed as defined in the EDS.

---

## Param All Data Types

| Field | Value |
|---|---|
| EDS file | [`0018002B00090100.eds`](eds/0018002B00090100.eds) |
| Vendor ID | 24 |
| Product Type | 43 |
| Product Code | 9 |

### Description

Tests the use of ParamN entry keywords across all CIP elementary data types from BOOL (0xC1) to TIME (0xDB) in a single EDS file. The following data types are covered:

- **Boolean:** BOOL
- **Signed integers:** SINT, INT, DINT, LINT
- **Unsigned integers:** USINT, UINT, UDINT, ULINT
- **Floating point:** REAL, LREAL
- **Date and time:** STIME, DATE, TIME_OF_DAY, DATE_AND_TIME
- **Durations:** FTIME, LTIME, ITIME, TIME
- **Strings:** STRING, STRING2, SHORT_STRING
- **Bit strings:** BYTE, WORD, DWORD, LWORD

Verifies that:

- The tool correctly parses each parameter definition and displays the default value in the correct format for each data type.
- Negative values are displayed with the correct sign for signed integer, floating-point, and duration types.
- The maximum values of the unsigned integer types (including 64-bit ULINT) are displayed correctly.
- String defaults, including Unicode characters and escape sequences, are displayed correctly.
- Bit string defaults specified in binary notation are parsed correctly.
- The data type and data size are shown correctly for each parameter.
- The parameter name, units, and help string are displayed as defined in the EDS.

> **Note:** Minimum and maximum values are not tested in this file. Value ranges for BOOL, SINT, INT, DINT, USINT, UINT, and UDINT are covered by the individual data type tests.

---

## Param Enumeration

| Field | Value |
|---|---|
| EDS file | [`0018002B00140100.eds`](eds/0018002B00140100.eds) |
| Vendor ID | 24 |
| Product Type | 43 |
| Product Code | 20 |

### Description

Tests the use of EnumN entry keywords together with ParamN entries for integer and bit string data types.

Verifies that:

- The tool correctly associates each EnumN entry with its corresponding ParamN entry and displays the enumerated names in place of the numeric values.
- For the integer types (BOOL, SINT, INT, USINT, and UINT), each enumerated value is matched to the correct name, including negative values for the signed types (SINT and INT).
- For the bit string types (BYTE, WORD, DWORD, and LWORD), the enumerated values are interpreted as bit positions, and the lowest, second lowest, second highest, and highest bits are named correctly for each data size, up to bit 63 for LWORD.
- The default value of each parameter is displayed using its enumerated name where one is defined.
- Bit string defaults specified in binary notation are parsed correctly.
- The data type, data size, parameter name, units, and help string are displayed as defined in the EDS.

---

## Assem SINT

| Field | Value |
|---|---|
| EDS file | [`0018002B000A0100.eds`](eds/0018002B000A0100.eds) |
| Vendor ID | 24 |
| Product Type | 43 |
| Product Code | 10 |

### Description

Tests the use of ParamN entry keywords with data type SINT (0xC2) as members of AssemN entry keywords. Each AssemN entry references two ParamN entries, each with a unique name (for example, SINT 1, SINT 2).

Verifies that:

- The tool correctly resolves each ParamN reference in the AssemN entry and displays the corresponding parameter name for each assembly member.
- The member size is shown as 8 bits per SINT member.
- The members are displayed in the order defined in the EDS.
- The total assembly size is calculated correctly.

---

## Assem USINT

| Field | Value |
|---|---|
| EDS file | [`0018002B000B0100.eds`](eds/0018002B000B0100.eds) |
| Vendor ID | 24 |
| Product Type | 43 |
| Product Code | 11 |

### Description

Tests the use of ParamN entry keywords with data type USINT (0xC6) as members of AssemN entry keywords. Each AssemN entry references two ParamN entries, each with a unique name (for example, USINT 1, USINT 2).

Verifies that:

- The tool correctly resolves each ParamN reference in the AssemN entry and displays the corresponding parameter name for each assembly member.
- The member size is shown as 8 bits per USINT member.
- The members are displayed in the order defined in the EDS.
- The total assembly size is calculated correctly.

---

## Assem INT

| Field | Value |
|---|---|
| EDS file | [`0018002B000C0100.eds`](eds/0018002B000C0100.eds) |
| Vendor ID | 24 |
| Product Type | 43 |
| Product Code | 12 |

### Description

Tests the use of ParamN entry keywords with data type INT (0xC3) as members of AssemN entry keywords. Each AssemN entry references two ParamN entries, each with a unique name (for example, INT 1, INT 2).

Verifies that:

- The tool correctly resolves each ParamN reference in the AssemN entry and displays the corresponding parameter name for each assembly member.
- The member size is shown as 16 bits per INT member.
- The members are displayed in the order defined in the EDS.
- The total assembly size is calculated correctly.

---

## Assem UINT

| Field | Value |
|---|---|
| EDS file | [`0018002B000D0100.eds`](eds/0018002B000D0100.eds) |
| Vendor ID | 24 |
| Product Type | 43 |
| Product Code | 13 |

### Description

Tests the use of ParamN entry keywords with data type UINT (0xC7) as members of AssemN entry keywords. Each AssemN entry references two ParamN entries, each with a unique name (for example, UINT 1, UINT 2).

Verifies that:

- The tool correctly resolves each ParamN reference in the AssemN entry and displays the corresponding parameter name for each assembly member.
- The member size is shown as 16 bits per UINT member.
- The members are displayed in the order defined in the EDS.
- The total assembly size is calculated correctly.

---

## Assem DINT

| Field | Value |
|---|---|
| EDS file | [`0018002B000E0100.eds`](eds/0018002B000E0100.eds) |
| Vendor ID | 24 |
| Product Type | 43 |
| Product Code | 14 |

### Description

Tests the use of ParamN entry keywords with data type DINT (0xC4) as members of AssemN entry keywords. Each AssemN entry references two ParamN entries, each with a unique name (for example, DINT 1, DINT 2).

Verifies that:

- The tool correctly resolves each ParamN reference in the AssemN entry and displays the corresponding parameter name for each assembly member.
- The member size is shown as 32 bits per DINT member.
- The members are displayed in the order defined in the EDS.
- The total assembly size is calculated correctly.

---

## Assem UDINT

| Field | Value |
|---|---|
| EDS file | [`0018002B000F0100.eds`](eds/0018002B000F0100.eds) |
| Vendor ID | 24 |
| Product Type | 43 |
| Product Code | 15 |

### Description

Tests the use of ParamN entry keywords with data type UDINT (0xC8) as members of AssemN entry keywords. Each AssemN entry references two ParamN entries, each with a unique name (for example, UDINT 1, UDINT 2).

Verifies that:

- The tool correctly resolves each ParamN reference in the AssemN entry and displays the corresponding parameter name for each assembly member.
- The member size is shown as 32 bits per UDINT member.
- The members are displayed in the order defined in the EDS.
- The total assembly size is calculated correctly.

---

## Assem Mix Aligned

| Field | Value |
|---|---|
| EDS file | [`0018002B00100100.eds`](eds/0018002B00100100.eds) |
| Vendor ID | 24 |
| Product Type | 43 |
| Product Code | 16 |

### Description

Tests the use of ParamN entry keywords with the elementary integer data types (SINT, USINT, INT, UINT, DINT, and UDINT) as members of AssemN entry keywords. Each AssemN entry contains two members of each data type, arranged so that every 16-bit and 32-bit member starts on a 16-bit boundary without padding. Each ParamN entry has a unique name, as shown in the Member column.

The AssemN entries have the following structure:

| Member | Data type | Offset (bits) | Size (bits) |
|---|---|---:|---:|
| SINT 1 | SINT | 0 | 8 |
| SINT 2 | SINT | 8 | 8 |
| USINT 1 | USINT | 16 | 8 |
| USINT 2 | USINT | 24 | 8 |
| INT 1 | INT | 32 | 16 |
| INT 2 | INT | 48 | 16 |
| UINT 1 | UINT | 64 | 16 |
| UINT 2 | UINT | 80 | 16 |
| DINT 1 | DINT | 96 | 32 |
| DINT 2 | DINT | 128 | 32 |
| UDINT 1 | UDINT | 160 | 32 |
| UDINT 2 | UDINT | 192 | 32 |
| **Total** | | | **224 (28 bytes)** |

Verifies that:

- The tool correctly resolves each ParamN reference in the AssemN entry and displays the corresponding parameter name for each member.
- The size and bit offset of each member are shown correctly.
- The members are displayed in the order defined in the EDS.
- No padding is inserted.
- The total assembly size is calculated as 224 bits (28 bytes).

---

## Assem Mix Unaligned

| Field | Value |
|---|---|
| EDS file | [`0018002B00110100.eds`](eds/0018002B00110100.eds) |
| Vendor ID | 24 |
| Product Type | 43 |
| Product Code | 17 |

### Description

Tests the use of ParamN entry keywords with the unsigned elementary integer data types (USINT, UINT, and UDINT) as members of AssemN entry keywords. Each AssemN entry contains two members of each data type, packed without alignment or padding, so that some 16-bit and 32-bit members do not start on their natural alignment boundary. Each ParamN entry has a unique name, as shown in the Member column.

The AssemN entries have the following structure:

| Member | Data type | Offset (bits) | Size (bits) | Value (T→O) |
|---|---|---:|---:|---:|
| USINT 1 | USINT | 0 | 8 | 8 |
| UINT 1 | UINT | 8 | 16 | 16 |
| UDINT 1 | UDINT | 24 | 32 | 32 |
| USINT 2 | USINT | 56 | 8 | 8 |
| UINT 2 | UINT | 64 | 16 | 16 |
| UDINT 2 | UDINT | 80 | 32 | 32 |
| **Total** | | | **112 (14 bytes)** | |

Verifies that:

- The tool correctly resolves each ParamN reference in the AssemN entry and displays the corresponding parameter name for each member.
- The size and bit offset of each member are shown correctly.
- The members are displayed in the order defined in the EDS.
- No padding is inserted.
- The total assembly size is calculated as 112 bits (14 bytes).
- The data sent by the reference implementation in the T→O direction is decoded correctly, with each member showing the value listed in the table.
