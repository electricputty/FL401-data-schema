# FL401-data-schema

JSON Data Definition Specification for the FL401 form
## General Guidelines

1. Do not add comments
2. Always use double quotes
3. Do not include empty or null values

## Naming convention
The intention is to make the element names as transparent and human readable as possible whilst maintaining a consistent pattern and keeping their lengths to a minimum.

1. All element names are based on the [paper verion of the FL401 form](https://github.com/electricputty/FL401-data-schema/blob/main/FL401-Non-mol-and-occ-order.pdf)
2. All element names are expressed in camel case (e.g. lowercase initial letter with capital letters at the start of each subsequent word)
3. In most cases 'short words' have been removed (e.g. &, and, or) except where these help with readibility

## Structure

1. The data is groupded into objects which correspond to the sections on the paper form
2. Property values must be Unicode booleans, numbers, strings, objects, arrays - do not include nulls or empty strings
3. All addresses are expressed using a sub-schema (#/definitions/ukAddress)
4. All dates are expressed using a sub-schema (#/definitions/standardDate)
5. All 'Select + other' values share a common sub-schema (#/definitions/singleSelectOther OR #/definitions/multiSelectOther) so should be expressed as an object. e.g

````
"currentlyLivesAtAddress": {
    "value": [
        "applicant",
        "respondent",
        "other"
    ],
    "other": "My friend Sue Johnson also lives at the house"
},
````
## Validation

Validation has been kept to a minimum. The following rules are enforced:

1. All values chosen from a set of options are validated aginst Enumeration types
2. To avoid 'falsy' ambiguity all boolean values are required
3. Where the string 'other' is selected as a value from an Enumeration type, the linked 'other' property becomes required
4. Some text values which are linked to booleans become required if the boolean value is set to true

## Testing

To test paste schema schema and sample JSON into: https://www.jsonschemavalidator.net/



