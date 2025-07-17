# Modules

## Store

name
default_currency_code
currency_codes
metadata

## Product

id
date_created
date_updated
name
slug
description
status: active, draft, proposed, rejected
attributes
categories
images: id, caption, url
options
tags
metadata

## Shipping

id
date_created
date_updated
name
price
metadata

## Product Variant

id
product_id
date_created
date_updated
name
description
images: id, caption, url
options
prices: currency_code, price, rules, type(standard, sale, override)
sku
stock_backorder
stock_level
manage_stock
metadata

## Product Category

id
date_created
date_updated
name
sort
top_id
active
slug
description
image: caption, url
metadata

## Attributes

id
date_created
date_updated
name
slug
filterable
default: default value
required
type: short_text - long_text - asset - lookup - boolean - select - number - date - tags - icon - collection - field_group
values: List of the attribute's associated select options used with attribute type of checkbox, radio, or select.

## Carts

id
date_created
date_updated
customer_id
abandoned: if cart was updated in the last 3 hours
shipping
billing
comments
currency
items: id, delivery, description, original_price, price, price_total, price_type, taxes: [{id, amount}], tax_total, tax_each, variant_id
notes: notes by admin
display_id
order_id: nullable
sub_total
total
tax_total
shipment_ttoal
shipment_total
taxes: [
{
id: string, // Unique identifier for the tax rule.
name: string, // Name of the tax rule. For example, "NY Sales Tax".
amount: currency, // Fixed tax amount.
priority: int, // Order in which the tax rule was applied.
rate: float, // Tax percentage used in calculating the fixed amount.
shipping: boolean, // Indicates if the tax applies to shipping.
}
]
payment
metadata

## Tax

## Orders

## Payments

## Customers
