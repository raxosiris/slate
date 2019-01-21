# Carts
Contains carts for users.
## Path
`/carts/{cart}`

where `{cart}` is the uid of a user who is adding items to the cart.


## Structure

| Name | Type | Description | Notes
--- |---|------|--
uid|string|Unique ID for the user obtained from firebase auth | [required]
totalDishes | number | Total number of dishes (items) in the cart | [required]
totalPriceBeforeDiscount | Total price of the dishes before discount | [required]
totalPriceAfterDiscount | Total price of the dishes after discount | [required]
expectBy | timestamp | Timestamp of when the user can expect this order | [optional]
totalPreparationTime | number | Total estimated preparation time. In case of one dish, it will be simply the current preparation time. In case of multiple dishes / quantities, this has to be calculated on the server side | [optional]
createdAt | timestamp | Timestamp of when the cart was created | [required] generated automatically by a cloud function
specialRequests | string | Any special requests that the user wants conveyed to the restaurant | [optional]
restaurantDetails | map of type [`restaurantDetails`](#dishes-structure-restaurantdetails) | A map containing brief information about the restaurant | [required]
dishes | map of type [`orderDishes`](#orderdishes) | A map containing all the dishes that are added | [required]

### orderDishes
`orderDishes: map with key {dishId}`
<aside class="notice">
This map is slightly different than others. It uses <code>dishId</code> as key. 
</aside>

| Values | Type | Description | Notes
--- |---|------|--
name| string | Display name of the dish | [required]
originalPrice | number | The original price of the dish (includes VAT in the UK) | [required]
currentPreparationTime | number | The current preparation time estimate | [optional]
lockedPrice | number | The price at the time when the item was added to the cart. In case of an item not being dynamic, this is equal to the original price | [required]
addedAt | timestamp | The timestamp of when the product was added to the cart | [required]
lockedUntil | timestamp | The timestamp until the price is locked | [optional]
imageUrl | string | Image associated with the dish | [optional]
totalOptionsPrice | number | Total price of the options if any options were selected | [optional]
selectedOptions | map of type `selectedOptions` |Defines the selected options| [optional]

#### selectedOptions
`selectedOptions: map with key {optionsGroupSlug}`

| Values | Type | Description | Notes
--- |---|------|--
`{optionSlug}`| map of type `selectedOption`| Map containing information about specific option(s) selected from an options group and their price | [required]

#### selectedOption
| Values | Type | Description | Notes
--- |---|------|--
optionText | string | The text of the option to be displayed in the UI | [required]
price | number | If the option carries a price, it is carried here | [optional]