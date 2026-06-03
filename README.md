# Squarespace *CCSQ* Widget
 
**Client-Side** custom query widget, utilizing Squarespace's client-side **front-end** Query API v2.

[![gitlab-license](https://img.shields.io/gitlab/license/sgkens/squarespace-ccsq-widget?style=flat&logo=gitlab)](https://gitlab.com/sgkens/squarespace-ccsq-widget) ![squarespace](https://img.shields.io/badge/SquareSpace-APIv2-green3?style=flat&labelColor=cyan3) ![squarespace](https://img.shields.io/badge/Client_Side-Only-yellow?style=flat&labelColor=cyan3)


## **Query Types**

- Uses **Squarespace's** `Client-Side` Custom Query `APIv2` to fetch products from a Squarespace store.
- Add widgets via the `Add block` > `Code` > `Code` element, with-in a section of your Squarespace site.
- Supports filtering by **category**, **tag**, **keyword**, **type**, **minimum price**, **maximum price**, **added after**, **added before**, **sort order**, **limit**, and **columns**.
- Supports displaying a loading message, empty message, and a grid with configurable columns.
- Supports displaying products in a grid or list format.
- Supports displaying products with or without:
    - **images**.
    - **prices**.
    - **titles**.
    - **descriptions**.
    - **variants**.
    - **pricing**.
    - **categories**.
    - **tags**.
    - **added dates**.

## **Usage**

1. Add the following script to your Squarespace site's `<head>` or `<footer>` perferably in the `footer`:
    - **WebSite** -> **Custom Code** -> **Code Injection** -> *Footer*
2. Use one of the examples below or a combination of the following attributes on any HTML element:
    - `data-sqpq`
    - `data-category`
    - `data-tag`
    - `data-keyword`
    - `data-type`
    - `data-min-price`
    - `data-max-price`
    - `data-added-after`
    - `data-added-before`
    - `data-sort-by`
    - `data-limit`
    - `data-columns`
    - `data-empty-message`

### **Example**

```html
<div 
    data-sqpq data-category="category1,category2" 
    data-tag="tag1,tag2" 
    data-keyword="keyword1,keyword2" 
    data-type="type1,type2" 
    data-min-price="10" 
    data-max-price="20" 
    data-added-after="2022-01-01" 
    data-added-before="2022-12-31" 
    data-sort-by="price-asc" 
    data-limit="12" 
    data-columns="3" 
    data-empty-message="No products found."
    >
</div>
```

## **Options**

| Attribute | Description | Default |
| --- | --- | --- |
| `data-sqpq` | Required. The ID of the HTML element to render the widget into. | |
| `data-category` | Optional. A comma-separated list of categories to filter by. | |
| `data-tag` | Optional. A comma-separated list of tags to filter by. | |
| `data-keyword` | Optional. A comma-separated list of keywords to filter by. | |
| `data-type` | Optional. A comma-separated list of product types to filter by. | |
| `data-min-price` | Optional. The minimum price to filter by. | |
| `data-max-price` | Optional. The maximum price to filter by. | |
| `data-added-after` | Optional. The date to filter by. | |
| `data-added-before` | Optional. The date to filter by. | |
| `data-sort-by` | Optional. The sort order to use. | `price-asc` |
| `data-limit` | Optional. The maximum number of products to display. | `12` |
| `data-columns` | Optional. The number of columns to display. | `3` |
| `data-empty-message` | Optional. The message to display when no products are found. | `No products found.` |

## **Styling**

The widget uses the following CSS classes:

- `sqpq-grid`: The grid container.
- `sqpq-cols-1`: A grid with 1 column.
- `sqpq-cols-2`: A grid with 2 columns.
- `sqpq-cols-3`: A grid with 3 columns.
- `sqpq-cols-4`: A grid with 4 columns.
- `sqpq-card`: The card container.
- `sqpq-img-wrap`: The image wrapper.
- `sqpq-no-img`: The placeholder image.
- `sqpq-info`: The info container.
- `sqpq-title`: The title.
- `sqpq-price`: The price.
- `sqpq-loading`: The loading message.
- `sqpq-empty`: The empty message.


## **All Query Types**

### 1. Basic Filters

#### *Filter by Substring Keyword*

Matches any product containing the specified string within its title.

```html
<div
  data-sqpq
  data-keyword="mug"
  data-limit="4"
  data-columns="4"
></div>
```

#### *Filter by Single Category*

Displays items explicitly assigned to a chosen storefront category.

```html
<div
  data-sqpq
  data-category="apparel"
  data-limit="6"
  data-columns="3"
></div>
```

#### *Filter by Multiple Categories (OR Logic)*

Matches products that belong to _either_ category.

```html
<div
  data-sqpq
  data-category="ceramics, glassware"
  data-limit="8"
  data-columns="4"
></div>
```

#### *Filter by Single Tag*

```html
<div
  data-sqpq
  data-tag="featured"
  data-limit="4"
  data-columns="4"
></div>
```

#### *Filter by Multiple Tags (OR Logic)*

Matches products that carry _either_ tag.

```html
<div
  data-sqpq
  data-tag="handmade, limited-edition"
  data-limit="6"
  data-columns="3"
></div>
```

### 2. Price and Type Constraints

#### *Specific Price Range*

Filters items between a clear floor and ceiling value (inclusive, parsed in dollars).

```html
<div
  data-sqpq
  data-min-price="25"
  data-max-price="100"
  data-sort-by="price-asc"
  data-limit="12"
  data-columns="4"
></div>
```

#### *Under a Fixed Threshold (Max Price Only)*

```html
<div
  data-sqpq
  data-max-price="50"
  data-sort-by="price-desc"
  data-limit="6"
  data-columns="3"
></div>
```

#### *Physical Products Only*

```html
<div
  data-sqpq
  data-type="physical"
  data-limit="8"
  data-columns="4"
></div>
```

#### *Digital Products / Downloads Only*

```html
<div
  data-sqpq
  data-type="digital"
  data-limit="8"
  data-columns="4"
></div>
```

#### *Service Items Only*

```html
<div
  data-sqpq
  data-type="service"
  data-limit="6"
  data-columns="3"
></div>
```

### 3. Date-Bounded Filters

#### *New Releases (Added After Fixed Date)*

```html
<div
  data-sqpq
  data-added-after="2026-01-01"
  data-sort-by="date-desc"
  data-limit="4"
  data-columns="4"
></div>
```

#### *Archive / Legacy Inventory (Added Before Fixed Date)*

```html
<div
  data-sqpq
  data-added-before="2025-06-01"
  data-sort-by="date-asc"
  data-limit="6"
  data-columns="3"
></div>
```

### 4. Advanced Matrix Variations (Strict AND Logic)

#### *Clearance Matrix (Tag + Category + Maximum Price)*

```html
<div
  data-sqpq
  data-category="apparel"
  data-tag="clearance"
  data-max-price="30"
  data-sort-by="price-asc"
  data-limit="8"
  data-columns="4"
  data-empty-message="No clearance apparel available."
></div>
```

#### *Premium New Digital Items (Type + Date + Minimum Price)*

```html
<div
  data-sqpq
  data-type="digital"
  data-added-after="2025-12-31"
  data-min-price="75"
  data-sort-by="date-desc"
  data-limit="3"
  data-columns="3"
  data-empty-message="No new premium digital items found."
></div>
```

### 5. Layout and Structural Configurations

#### *Single Row Spotlight / Banner Layout*

```html
<div
  data-sqpq
  data-limit="4"
  data-columns="4"
  data-sort-by="date-desc"
></div>
```

#### *High-Density Showcase Matrix*

```html
<div
  data-sqpq
  data-limit="24"
  data-columns="4"
  data-sort-by="title-asc"
></div>
```

#### *Single Column Vertical Sidebar*

```html
<div
  data-sqpq
  data-limit="5"
  data-columns="1"
  data-sort-by="price-desc"
></div>
```

#### *Dual Column Split Layout*

```html
<div
  data-sqpq
  data-limit="2"
  data-columns="2"
  data-sort-by="date-desc"
></div>
```

### 6. Alternative Sorting Configurations

#### *Alphabetical Sorting (A to Z)*

```html
<div
  data-sqpq
  data-sort-by="title-asc"
  data-limit="12"
  data-columns="3"
></div>
```

#### *Reverse Alphabetical Sorting (Z to A)*

```html
<div
  data-sqpq
  data-sort-by="title-desc"
  data-limit="12"
  data-columns="3"
></div>
```

#### *Fallback Native Order*

Omitting the `data-sort-by` attribute completely retains the default array positioning returned directly by the Squarespace collection layout.

```html
<div
  data-sqpq
  data-limit="6"
  data-columns="3"
></div>
```

## License

This project is licensed under the terms of the MIT license.

Copyright (c) [MIT LICENSE](LICENSE) 2022 Garvry K. Snow @sgkens
