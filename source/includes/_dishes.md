# Dishes
Contains information about a dish
## Path
`/dishes/{dish}`

where `{dish}` is an automatically generated uid for a dish


## Structure

| Name | Type | Description | Notes
--- |---|------|--
id|string|Unique ID for the dish. Same as the document name | [required]
name| string | The display name of the dish | [required]
originalPrice | number | The original price of the dish (includes VAT in the UK) | [required]
maxQuantity | number | Restricts the number of the same item that can be bought at the same time | [optional]
featured | boolean | Whether this item is featured in the restaurant's menu | [optional]
categorySlug | string | A slug of the category to be used in sorting and displaying in the UI | [optional] 
categoryText | string | Name of the category to be shown in UI  | [optional]
averagePreparationTime | number | Time it takes for the dish to be prepared, on average (in seconds) | [optional]
currentPreparationTime | number | The current preparation time estimate | [optional]
description | string | A description of the dish | [optional]
imageUrl | string | Image associated with the dish | [optional]
rating | number | The average rating gathered from the reviews posted about this dish | [optional]
totalRatings | number | The number of ratings that have been published about this dish | [optional]
goesWellWith | arrary[`{dish}`] | An array that contains dish ids of the dishes that pair well with this product | [optional]
ingredients | array[`string` ]| An array containing ingredients of this dish in lowercase formatted strings | [optional]
tags | array[`string`] | Any tags associated with the dish - e.g. vegan, vegetarian, halal | [optional]
restaurantDetails | map of type [`restaurantDetails`](#dishes-structure-restaurantdetails) | A map containing brief information about the restaurant | [required]

### restaurantDetails
`restaurantDetails : map`

| Name | Type | Description | Notes
--- |---|------|--
id | string | Unique ID of the restaurant to which this dish belongs | [required]
firestoreRef | reference | reference to the restaurant object | [required]
name | string | Name of the restaurant | [required]
imageUrl | string | URL to the image of the restaurant | [optional]
address | map of type [`address`](#dishes-structure-restaurantdetails-address) | Details about location of the restaurant | [required]

#### address
`address : map`

| Name | Type | Description | Notes
--- |---|------|--
line1 | string | Line 1 of the address | [required]
line2 | string | Line 2 of the address | [optional]
city | string | City or town of the restaurant | [required]
postcode | string | Postcode or zipcode of the restaurant | [optional]
location | geopoint | Lat-long co-ordinates of the restaurant | [required]

## Subcollection : Options
Some dishes contain options such as size, flavours, condimends, and extras. This information is contained in the options subcollection

### Path
`/dishes/{dish}/options/{option}`

where `{option}` is a unique options group slug

### Structure

| Name | Type | Description | Notes
--- |---|------|--
optionsGroupSlug | string | Options group slug to identify this group of options | [optional]
optionsGroupText | string | The text to show on the UI (formatted) | [required]
displayOrder | number | The display order of this options group in the UI. Starts at 0 | [required]
maximumChoices | number | The maximum number of selections a user is allowed to make. 0 implies no restrictions | [required]
minimumChoices | number | The minimum number of selections required from a user. 0 implies no minimum | [required]
freeChoices | number | The number of options that are free to select. 0 implies no free selections | [required]
options | array[[`option`]](#dishes-subcollection-options-structure-option) | An array of options | [required]

#### option
`option : map`

Map of an option within an option group

| Name | Type | Description | Notes
--- |---|------|--
outOfStock | boolean | Whether an option is out of stock | [optional]
optionSlug | string | A lowercase slug of the option| [required]
optionText | string | The text of the option to be displayed in the UI | [required]
price | number | If the option carries a price, it is carried here | [optional]