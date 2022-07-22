# XML Marshes
### a modification of standard `encoding/xml` lib

Standard GO xml marshaller `xml.Marshal()` generates XML without namespace prefixes:
```
<Message xmlns="urn:tch">
    <AppHdr>
        <Fr xmls="urn:iso:std:iso:20022:tech:xsd:head.001.001.01">
```
The goal of the lib is to give an option to manipulate the output XML during marshalling to include prefixes like:
```
<Message xmlns="urn:tch" xmlns:h="urn:iso:std:iso:20022:tech:xsd:head.001.001.01">
    <AppHdr>
        <h:Fr>
```
Go code structs representing XMLs are being generated from XSD or created from scratch. These structs contain:
- `XMLName xml.Name` helper fields
- `` `xml:"urn:tch Message"` `` helper tags (annotations)

The task is to manipulate both the struct and XML marshaller to include namespace prefix behaviour:
- [ ] All namespaces defined in the root XML element 
- [ ] Correct prefixes for XML elements that are not defined in default namespace
- [ ] Integrate the changes with the new XSD to GO code generator [here](https://github.com/form3tech/investment-time-project/issues/29)
