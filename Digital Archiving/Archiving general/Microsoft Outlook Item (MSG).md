
https://www.loc.gov/preservation/digital/formats/fdd/fdd000379.shtml


## Microsoft Outlook Item (MSG)

>> Back

**Table of Contents**

- [Identification and description](https://www.loc.gov/preservation/digital/formats/fdd/fdd000379.shtml#identification)
- [Local use](https://www.loc.gov/preservation/digital/formats/fdd/fdd000379.shtml#local)
- [Sustainability factors](https://www.loc.gov/preservation/digital/formats/fdd/fdd000379.shtml#sustainability)
- [Quality and functionality factors](https://www.loc.gov/preservation/digital/formats/fdd/fdd000379.shtml#factors)
- [File type signifiers](https://www.loc.gov/preservation/digital/formats/fdd/fdd000379.shtml#sign)
- [Notes](https://www.loc.gov/preservation/digital/formats/fdd/fdd000379.shtml#notes)
- [Format specifications](https://www.loc.gov/preservation/digital/formats/fdd/fdd000379.shtml#specs)
- [Useful references](https://www.loc.gov/preservation/digital/formats/fdd/fdd000379.shtml#useful)

**Format Description Properties [![Explanation of format description terms](https://www.loc.gov/preservation/digital/formats/fdd/info.gif "Explanation of format description terms")](https://www.loc.gov/preservation/digital/formats/fdd/fdd_explanation.shtml)** 

- ID: fdd000379
- Short name: MSG
- Content categories: text, email
- Format Category: file-format
- Other facets: unitary, binary, structured, symbolic
- Last significant FDD update: 2023-03-01
- Draft status: Full

  

### Identification and description [![Explanation of format description terms](https://www.loc.gov/preservation/digital/formats/fdd/info.gif "Explanation of format description terms")](https://www.loc.gov/preservation/digital/formats/fdd/fdd_explanation.shtml#identification)

|   |   |
|---|---|
|Full name|Microsoft Outlook Item (MSG)|
|Description|The Outlook Item MSG (.msg) file format is a syntax for storing a single Message object, such as an email, an appointment, a contact, a task, and so on, in a file. Any properties that are present on the Message object, including Attachment objects, are also present in the MSG file.<br><br>MSG is based on the [CFB_3](https://www.loc.gov/preservation/digital/formats/fdd/fdd000380.shtml) format which implements a simplified file system through a hierarchical collection of storage objects and stream objects which behave as directories and files, respectively within a single file. Message files contain objects which contain properties and collections of properties. For all intents and purposes, objects are represented by storages and properties are represented and reside in streams.<br><br>MSG specifies five storage elements, each representing one major component of the Message object and a number of streams are contained within those storages, each stream representing a property (or a set of properties) of that component.<br><br>The storages are:<br><br>- Recipient object storage<br>- Attachment object storage<br>- Embedded Message object storage<br>- Custom attachment storage<br>- Named property mapping storage<br><br>The numbers and types of storages and streams present in a MSG file depend on the type of Message object, the number of Recipient objects and Attachment objects it has, and other properties. Properties define attributes of the object like the sender email, whether a read receipt was requested by the sender, whether this message was auto forwarded, an attachment’s filename, etc.<br><br>String properties in MSG must be either Unicode or non-Unicode. The .msg File Format does not allow the presence of both simultaneously.|
|Production phase|MSG files provide a mechanism for the storage of an email message, an appointment, a contact, or a task within a file system.|
|Relationship to other formats|   |
|Defined via|[CFB_3](https://www.loc.gov/preservation/digital/formats/fdd/fdd000380.shtml), Compound File Binary File Format, Version 3|

  

### Local use [![Explanation of format description terms](https://www.loc.gov/preservation/digital/formats/fdd/info.gif "Explanation of format description terms")](https://www.loc.gov/preservation/digital/formats/fdd/fdd_explanation.shtml#local)

|   |   |
|---|---|
|LC experience or existing holdings|The Library of Congress includes MSG files in its collections, especially in the Manuscripts and Music Divisions as well as other personal papers repositories.|
|LC preference|The Library of Congress Recommended Formats Statement (RFS) lists MSG as an acceptable format for [Email: For individual messages](https://www.loc.gov/preservation/resources/rfs/email.html).|

  

### Sustainability factors [![Explanation of format description terms](https://www.loc.gov/preservation/digital/formats/fdd/info.gif "Explanation of format description terms")](https://www.loc.gov/preservation/digital/formats/fdd/fdd_explanation.shtml#sustainability)

|   |   |
|---|---|
|Disclosure|Fully documented. Proprietary file format developed by Microsoft.|
|Documentation|[[MS-OXMSG]: Outlook Item (.msg) File Format](https://docs.microsoft.com/en-us/openspecs/exchange_server_protocols/ms-oxmsg/b046868c-9fbf-41ae-9ffb-8de2bd4eec82) specification available from Microsoft.|
|Adoption|MSG is implemented in the following Microsoft products: Microsoft Exchange Server 2003-2013 and Microsoft Office Outlook 2003-2013.|
|Licensing and patents|The MSG format specification is covered by the Microsoft Interoperability Program. See [Useful references](https://www.loc.gov/preservation/digital/formats/fdd/fdd000379.shtml#useful) below. Microsoft claims no patents in the MSG format. Patents and licenses may apply to some operations and protocols that are used by Microsoft in its electronic mail products and that the MSG format is designed to support. In late 2015, the only patents listed by Microsoft as associated with the related protocol specifications listed in this format description are associated with operational systems for managing messages according to a retention policy: [US 8620869 B2 -- Techniques to manage retention policy tags](http://www.google.com/patents/US8620869); and [US 20140095641 A1 -- Techniques to manage retention policy tags](http://www.google.co.ve/patents/US20140095641).|
|Transparency|A .msg file can be saved in Outlook or compatible email client and then viewed in an hex editor or binary file parser.|
|Self-documentation|See [CFB_3](https://www.loc.gov/preservation/digital/formats/fdd/fdd000380.shtml).<br><br>**Accessibility Features**<br><br>MSG does not have specific features to support digital accessibility but as a text-based format, it does comply with [Section 508](https://www.section508.gov/test/checklist/email-messages/) guidelines for accessible email. These guidelines include information about five areas of focus for email: Structure (which, in part, advocates for plain-text or HTML formats), General Content of messages including color contrast, file attachments and signature blocks, Graphics and Sensory Characteristics including the use of alt text, Data Tables with a focus on structured data and their headings, and Saving Files as a document file. MSG is specifically listed as a preferred option for this, along with [EML](https://www.loc.gov/preservation/digital/formats/fdd/fdd000388.shtml). [Accessible-email.org](https://www.accessible-email.org/) also provides an accessibility evaluation tool "aimed at email marketing professionals and industry developers to give them an overview of their current level and possible improvements" in terms of accessibility and usability.|
|External dependencies|None|
|Technical protection considerations|None|

  

### Quality and functionality factors [![Explanation of format description terms](https://www.loc.gov/preservation/digital/formats/fdd/info.gif "Explanation of format description terms")](https://www.loc.gov/preservation/digital/formats/fdd/fdd_explanation.shtml#factors)

  

### File type signifiers and format identifiers [![Explanation of format description terms](https://www.loc.gov/preservation/digital/formats/fdd/info.gif "Explanation of format description terms")](https://www.loc.gov/preservation/digital/formats/fdd/fdd_explanation.shtml#sign)

|Tag|Value|Note|
|---|---|---|
|Filename extension|msg|From [specification](https://docs.microsoft.com/en-us/openspecs/exchange_server_protocols/ms-oxmsg/b812bc47-4397-4a15-b03d-84aa20be866f)|
|Internet Media Type|application/vnd.ms-outlook|Not registered with IANA but listed on [MIME Types by Content Type](http://webdesign.about.com/od/multimedia/a/mime-types-by-content-type.htm).|
|File signature||See [CFB_3](https://www.loc.gov/preservation/digital/formats/fdd/fdd000380.shtml)|
|Other|NF00280|See [https://www.archives.gov/files/lod/dpframework/id/NF00280.ttl](https://www.archives.gov/files/lod/dpframework/id/NF00280.ttl).|
|Pronom PUID|x-fmt/430|See [http://www.nationalarchives.gov.uk/PRONOM/x-fmt/430](http://www.nationalarchives.gov.uk/PRONOM/x-fmt/430) for Outlook 97-2003.|
|Wikidata Title ID|Q61707607|See [https://www.wikidata.org/wiki/Q61707607](https://www.wikidata.org/wiki/Q61707607) for Outlook 97-2003.|

  

### Notes [![Explanation of format description terms](https://www.loc.gov/preservation/digital/formats/fdd/info.gif "Explanation of format description terms")](https://www.loc.gov/preservation/digital/formats/fdd/fdd_explanation.shtml#notes)

|   |   |
|---|---|
|General|[Microsoft reports](https://msdn.microsoft.com/en-us/library/ee157268.aspx) that there are scenarios for which storing a Message object in the MSG format would not be advisable:<br><br>- Maintaining a large standalone archive. A better option would be a more full-featured format that can render views more efficiently.<br>- Sending information to an unknown receiver. In this scenario, it is possible that the format is not supported by the receiver or that information that is private or irrelevant might be transmitted.<br><br>MSG provides some security mechanisms for ensuring that clients read the correct number of bytes from constituent streams.<br><br>- In the case of multiple-valued variable length properties, the length stream contains the lengths of each value. Clients can compare the lengths obtained from there with the actual length of the value streams. If they are not in sync, it can be assumed that there is data corruption.<br>- In case of the strings, stream entries are stored prefixed with their lengths; and if any inconsistency is detected, clients can assume that there is data corruption.|
|History||

  

### Format specifications [![Explanation of format description terms](https://www.loc.gov/preservation/digital/formats/fdd/info.gif "Explanation of format description terms")](https://www.loc.gov/preservation/digital/formats/fdd/fdd_explanation.shtml#specs)

- [[MS-OXMSG]: Outlook Item (.msg) File Format](https://docs.microsoft.com/en-us/openspecs/exchange_server_protocols/ms-oxmsg/) (https://docs.microsoft.com/en-us/openspecs/exchange_server_protocols/ms-oxmsg/). Format specification from Microsoft. Document covered by Microsoft Interoperability Program. No patents are associated with this specification..
- Property schemas for MSG Message objects are defined by separate documents. These protocol specifications are covered by the Microsoft Interoperability Program. See [Useful References](https://www.loc.gov/preservation/digital/formats/fdd/fdd000379.shtml#useful) below. The only associated patents listed by Microsoft relate to active operation of a mail system that uses tags to manage and expire messages in line with a retention policy.
    - [[MS-OXCMSG]: Message and Attachment Object Protocol](https://docs.microsoft.com/en-us/openspecs/exchange_server_protocols/ms-oxcmsg/7fd7ec40-deec-4c06-9493-1bc06b349682) (https://docs.microsoft.com/en-us/openspecs/exchange_server_protocols/ms-oxcmsg/7fd7ec40-deec-4c06-9493-1bc06b349682). Specifies the basic property schema for a Message object
    - [[MS-OXPROPS]: Exchange Server Protocols Master Property List](https://docs.microsoft.com/en-us/openspecs/exchange_server_protocols/ms-oxprops/f6ab1613-aefe-447d-a49c-18217230b148) (https://docs.microsoft.com/en-us/openspecs/exchange_server_protocols/ms-oxprops/f6ab1613-aefe-447d-a49c-18217230b148). Specifies the basic property schema for a Message object and the default property schema for a Folder object

  

### Useful references

**URLs**  

- Helpful blog series from Microsoft Open Specifications Support Team Blog on MSG format
    - [.MSG File Format (Part 1)](https://docs.microsoft.com//en-us/archive/blogs/openspecification/msg-file-format-part-1) (https://docs.microsoft.com//en-us/archive/blogs/openspecification/msg-file-format-part-1). Overview of the MSG format
    - [.MSG File Format, Rights Managed Email Message (Part 2)](https://docs.microsoft.com//en-us/archive/blogs/openspecification/msg-file-format-rights-managed-email-message-part-2) (https://docs.microsoft.com//en-us/archive/blogs/openspecification/msg-file-format-rights-managed-email-message-part-2). General exploration of rights managed MSG email messages
    - [.MSG File Format, Rights Managed Email Message (Part 3)](https://docs.microsoft.com//en-us/archive/blogs/openspecification/msg-file-format-rights-managed-email-message-part-3) (https://docs.microsoft.com//en-us/archive/blogs/openspecification/msg-file-format-rights-managed-email-message-part-3). More detail about rights managed MSG email messages
- Links related to the Microsoft Interoperability Program, a documentation program designed in connection with the 2009 Interoperability Undertaking between Microsoft and the European Commission. Covers Exchange-Outlook protocols documentation.
    - [Microsoft Interoperability Program.](https://msdn.microsoft.com/en-us/library/gg134029.aspx) (https://msdn.microsoft.com/en-us/library/gg134029.aspx).
    - [Microsoft Statement on European Commission Decision. December 2009.](http://news.microsoft.com/2009/12/16/microsoft-statement-on-european-commission-decision/) (http://news.microsoft.com/2009/12/16/microsoft-statement-on-european-commission-decision/).
    - [Persistent Microsoft link to Microsoft Statement on European Commission Decision. December 2009.](http://go.microsoft.com/fwlink/?LinkId=179741) (http://go.microsoft.com/fwlink/?LinkId=179741).
    - [Microsoft Open Specifications Programs: Patent Promises and Patents](https://docs.microsoft.com/en-us/openspecs/dev_center/ms-devcentlp/13571077-e344-4e6f-a477-369894979798) (https://docs.microsoft.com/en-us/openspecs/dev_center/ms-devcentlp/13571077-e344-4e6f-a477-369894979798). Includes an interactive table that enables identification of any Microsoft patents or patent applications that Microsoft believes to be associated with a published specification.
    - [Microsoft Interoperability Program (MIP): Patent License and Covenant Agreements](https://docs.microsoft.com/en-us/openspecs/dev_center/ms-devcentlp/a83d8d17-0cde-46df-a496-2686bff58d5d) (https://docs.microsoft.com/en-us/openspecs/dev_center/ms-devcentlp/a83d8d17-0cde-46df-a496-2686bff58d5d). See Patent Pledge for Open Source Developers.
- [Section508.gov: Checklist for Accessible Email Messages](https://www.section508.gov/test/checklist/email-messages/) (https://www.section508.gov/test/checklist/email-messages/).
- [accessible-email.org. Includes Accessibility evaluation tool for email](https://www.accessible-email.org/) (https://www.accessible-email.org/).
- [NARA File Format Preservation Plan ID entry for NF00280](https://www.archives.gov/files/lod/dpframework/id/NF00280.ttl) (https://www.archives.gov/files/lod/dpframework/id/NF00280.ttl). Information in NARA File Format Preservation Plan ID about Microsoft Outlook Item.
- [PRONOM entry for x-fmt/430](http://www.nationalarchives.gov.uk/pronom/x-fmt/430) (http://www.nationalarchives.gov.uk/pronom/x-fmt/430). Information in PRONOM from UK National Archives about MSG for Outlook 97-2003. PUID: x-fmt/430.
- [Wikidata entry for Q61707607](https://www.wikidata.org/wiki/Q61707607) (https://www.wikidata.org/wiki/Q61707607). Information in Wikidata about MSG for Outlook 97-2003. Wikidata Title ID: Q61707607.
- See also [CFB_3](https://www.loc.gov/preservation/digital/formats/fdd/fdd000380.shtml)