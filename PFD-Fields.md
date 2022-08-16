#VSF TR-06-3 Payload Format Descriptor Coding

##Introduction

The RIST Advanced Profile Payload Format Descriptor (PFD) is a 32-bit value that indicates the content of the tunnel packet. PFD values are registered using this repository. This document describes bit assignments for this field.

##Payload Format Descriptor Field

The general format of the Payload Format Descriptor is shown below:

	 0                   1                   2                   3 
	 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
	+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
	|ID TYPE|            ID VALUE (dependent on ID TYPE)            |
	+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+

The fields above are defined as follows:

1. ID TYPE: 4 bits
Senders shall set this field to identify a standards body category, and to define the format of the ID VALUE field.  The following ID Types are defined:
    - 0:  VSF Category.
    - 1:  RFC Category.
    - 2:  SMPTE Category.
    - 3:  IEEE Category.
    - 4:  ISO/IEC Category.
    - 5: AES Category.
    - 6: ATSC Category.
    - 7: ITU Category.
    - 8: ETSI/DVB Category.
    - 9: EBU Category.
    - 10-14: Reserved for future use.
    - 15:  Vendor defined type: reserved for private allocation to vendors.  Note that interoperability is not guaranteed in this case.
1. ID VALUE: 28 bits
Senders shall use this value to identify the exact Standard, RFC or Recommendation. The formatting of this field is dependent on the ID TYPE field and described in the following sections of this document.

NOTE: Not all ID Types are covered in this document. The document will be updated as needed to further define the remaining ID Types.

###Payload Format Description for VSF Specifications

The Payload Format Descriptor for VSF Specifications is shown in below.  The ID VALUE field is divided into three components: the Main Document Number, the Part and the ID Flavor.

	 0                   1                   2                   3 
	 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
	+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
	|   0   |      Main Document Number     |  Part |   ID Flavor   |
	+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
	

Senders shall set these fields as follows:

1. Main Document Number: 16 bits
Senders shall set this field to indicate the VSF TR number. Example: for VSF TR-06-3, this field will have the value “6”.
1. Part: 4 bits
Senders shall set this field to indicate the VSF TR subpart.
Example: for VSF TR-06-3, this field will have the value “3”.
1. ID Flavor: 8 bits
A VSF TR may define multiple packet formats.  Senders shall set this field to indicate the specific format. Values shall be used sequentially – e.g., the first packet format will have ID Flavor=0, the next ID Flavor=1, and so on.

###Payload Format Descriptor for RFCs

The Payload Format Descriptor for RFCs is shown below. The ID VALUE field is divided into two components: the RFC number and the ID Flavor.

	 0                   1                   2                   3 
	 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
	+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
	|   1   |             RFC NUMBER                |   ID Flavor   |
	+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
	
Senders shall set these fields as follows:

1. RFC NUMBER: 20 bits
Senders shall set this field to the RFC number.
1. ID Flavor: 8 bits
An RFC may define multiple packet formats.  Senders shall set this field to indicate the specific format. Values shall be used sequentially – e.g., the first packet format will have ID Flavor=0, the next ID Flavor=1, and so on.

###Payload Format Descriptor for SMPTE Standards

The Payload Format Descriptor for SMPTE Standards is shown below.  The ID VALUE field is divided into three components: the Main Document Number, the Subpart Number and the ID Flavor.

	 0                   1                   2                   3 
	 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
	+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
	|   2   |   Main Document Number  | Sub Part No |   ID Flavor   |
	+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
	
Senders shall set these fields as follows:

1. Main Document Number: 13 bits
Senders shall use this field to indicate the SMPTE Standard Number.
Example: for SMPTE 2110-20, this field will have the value “2110”.
1. Sub Part Number: 7 bits
Senders shall use this field to indicate the SMPTE Standard Subpart Number.
Example: for SMPTE 2110-20, this field will have the value “20”.
1. ID Flavor: 8 bits
A SMPTE Standard may define multiple packet formats.  Senders shall set this field to indicate the specific format. Values shall be used sequentially – e.g., the first packet format will have ID Flavor=0, the next ID Flavor=1, and so on.

###Payload Format Descriptor for ISO/IEC Standards

The Payload Format Descriptor for ISO/IEC Standards is shown below.  The ID VALUE field is divided into three components: the Main Document Number, the Subpart Number and the ID Flavor.

	 0                   1                   2                   3 
	 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
	+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
	|   4   |       Main Document Number      | Sub Part  |ID Flavor|
	+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
	
Senders shall set these fields as follows:

1. Main Document Number: 17 bits
Senders shall use this field to indicate the ISO/IEC Standard Number.
Example: for ISO/IEC 14496-14, this field will have the value “14496”.
1. Sub Part: 5 bits
Senders shall use this field to indicate the ISO/IEC Standard Subpart Number.
Example: for ISO/IEC 14496-14, this field will have the value “14”.
1. ID Flavor: 6 bits
An ISO/IEC Standard may define multiple packet formats.  Senders shall set this field to indicate the specific format. Values shall be used sequentially – e.g., the first packet format will have ID Flavor=0, the next ID Flavor=1, and so on.

###Payload Format Descriptor for ATSC Standards

The Payload Format Descriptor for ATSC Standards is shown below.  The ID VALUE field is divided into three components:  the Main Document Number, the Part Number and the ID Flavor.

	 0                   1                   2                   3 
	 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
	+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
	|   6   |  Main Document Number |    Part No    |   ID Flavor   |
	+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+

Senders shall set these fields as follows:

1. Main Document Number: 12 bits
Senders shall use this field to indicate the main ATSC standard number.
Example: for ATSC A/72, this field will contain the value “72”.
1. Part Number: 8 bits
Some ATSC standards have multiple parts.  For standards where this is the case, senders shall use the Part Number field to indicate the part.  For ATSC standards with no parts, this field shall be coded as zero.
1. ID Flavor: 8 bits
An ATSC Standard may define multiple packet formats.  Senders shall set this field to indicate the specific format. Values shall be used sequentially – e.g., the first packet format will have ID Flavor=0, the next ID Flavor=1, and so on.

###Payload Format Descriptor for the Vendor-Defined Category

The Payload Format Descriptor for the vendor-defined category is shown below.  Vendors who desire to utilize this format shall register with the VSF and obtain a Vendor ID.

	 0                   1                   2                   3 
	 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
	+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
	|  15   |        Vendor ID      |   For Vendor Use/Allocation   |
	+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+

Senders shall set these fields as follows:

1. Vendor ID: 12 bits
Senders shall set this field to a 12-bit Vendor ID.  A vendor who wishes to use this feature shall register with the VSF and obtain a unique Vendor ID.
1. For Vendor Use/Allocation: 16 bits
Senders shall set this field to a value that is managed by the vendor.
