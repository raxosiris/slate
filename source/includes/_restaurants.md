# Restaurants
Contains information about restaurants
## Path
`/restaurants/{restaurant}`

where `{restaurant}` is an automatically generated uid for a restaurant


## Structure

| Name | Type | Description | Notes
--- |---|------|--
id|string|Unique ID for the restaurant. Same as the document name | [required]
name| string | The display name of the restaurant | [required]
imageUrl | string | The image associated with the restaurant | [optional]
description | string | A description of the restaurant | [optional]
phone | string | Phone number of the restaurant | [optional]
address | map of type [`address`](#restaurants-structure--address) | Details about location of the restaurant | [required]
categoriesDisplayOrder | arrary of `categorySlug` | Contains information about the displayOrder of the categories. When updating, a new instance has to be created since firestore does not allow order operations | [optional]



### address
`address : map`

| Name | Type | Description | Notes
--- |---|------|--
line1 | string | Line 1 of the address | [required]
line2 | string | Line 2 of the address | [optional]
city | string | City or town of the restaurant | [required]
postcode | string | Postcode or zipcode of the restaurant | [optional]
location | geopoint | Lat-long co-ordinates of the restaurant | [required]