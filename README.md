# FL401-data-schema

WIP on Data Definition Specification for FL401

See: https://docs.google.com/spreadsheets/d/15GXjMRVlzwRyHNLRxCLbSaNc3dGRcFWUQMqaWytzVVs/edit?usp=sharing
(For access please email developer@electricputty.co.uk)

To test paste schema and test JSON into: https://www.jsonschemavalidator.net/

## Naming convention notes
The intention is to make the element names as transparent and human readable as possible whilst maintaining a consistent pattern and keeping their lengths to a minimum.

1. All element names are based on the [paper verion of the FL401 form](https://github.com/electricputty/FL401-data-schema/blob/main/FL401-Non-mol-and-occ-order.pdf)
2. All element names are expressed in camel case (e.g. lowercase initial letter with capital letters at the start of each subsequent word)
3. In most cases 'short words' have been removed (e.g. &, and, or) except where these help with readibility

## Structure convention notes

1. All values chosen from a set of options are expresses as Enumeration types
2. All addresses are expressed using a sub-schema (#/definitions/ukAddress)
3. All dates are expressed using a sub-schema (#/definitions/standardDate)
4. All 'Select + other' values share a common sub-schema (#/definitions/singleSelectOther OR #/definitions/multiSelectOther) so should be expressed as an object. e.g

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

