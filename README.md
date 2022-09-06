# CCD FL401 Case Submission

JSON Data Definition Specification for the API Payload to submit an FL401 case to HMCTS' CCD Platform

Two sechems are provided in this repo:

1. The complete CCD Create Case API payload schema - this is made up of FL401 schema + a metaData property
2. The stand-alone FL401 schema
## General Format Guidelines

1. Do not add comments
2. Always use double quotes
3. Do not include empty or null values

## Property Naming convention
The intention is to make the element names as transparent and human readable as possible whilst maintaining a consistent pattern and keeping their lengths to a minimum.

1. All element names are based on the [paper verion of the FL401 form](/resources/FL401-Non-mol-and-occ-order.pdf)
2. Where the paper version refers to `you` or `your` the schema uses `applicant` - for example `Your date of birth` is referenced as `applicantDateOfBirth`
2. All element names are expressed in camel case (e.g. lowercase initial letter with capital letters at the start of each subsequent word)
3. In most cases 'short words' have been removed (e.g. &, and, or) except where these help with readibility
4. Where a property has an 'other' option, an additonal property exists in the schema to store the 'other' value - this shares the name of the original with the suffix Other. For example: `applicantGender` and `applicantGenderOther`

## Structure

1. The data within the CCD Create Case schema is broken down into two properties:
   - `metaData` : Information about the case which doesn't appear on the FL401 form
   - `fl401` : All the data required to complete the FL401 form (**note** - this is also provided as a [stand-alone schema](schemas/fl401.json))
1. The FL401 data is groupded into objects which correspond to the sections on the paper form - refer to [FL401-Field-names-and-rules.xlsx](/resources/FL401-Field-names-and-rules.xlsx)
1. Property values must be Unicode booleans, numbers, strings, objects, arrays - do not include nulls or empty strings
1. All addresses are expressed using a sub-schema (#/definitions/ukAddress)
1. All dates are expressed using a sub-schema (#/definitions/standardDate)

## Validation

Validation has been kept to a minimum. The following rules are enforced:

1. All values chosen from a set of options are validated aginst Enumeration types
2. To avoid 'falsy' ambiguity all boolean values are required
3. Where the string 'other' is selected as a value from an Enumeration type, the linked 'other' property becomes required
4. Some text values which are linked to booleans become required if the boolean value is set to true

## Testing

To test paste the [ccd-create-case.json](schemas/ccd-create-case.json) schema and [sample JSON](examples/ccd-create-case.json) into: https://www.jsonschemavalidator.net/



