# **Flexbox**

<br>

## **Table of Content**

- [Flexbox]()
  - [Flexbox Terminology]()
  - [Flexbox Properties]()
- [Flex Container]()
  - [justify-content and align-items]()

<br>

## **Flexbox**

CSS Flexbox is a one-dimensional layout tool.

<br>

### **Flexbox Terminology**

- The element on which we use `{ display: flex; }` is called the **Flex Container**.
- All direct children of the flex container are called the **Flex Items**.
- The direction in which Flex Items are displayed is called the **Main Axis**.
- The other perpendicular axis is called **Cross Axis**.

_We can change the direction of the Main Axis._

<br>

### **Flexbox Properties**

<br>

| Container Properties | Item Properties |
| :------------------: | :-------------: |
|   `flex-direction`   |  `align-self`   |
|     `flex-wrap`      |     `order`     |
|  `justify-content`   |     `flex`      |
|    `align-items`     |   `flex-grow`   |
|   `align-content`    |  `flex-shrink`  |
|     `flex-flow`      |  `flex-basis`   |

We use properties on the flex container to position and align the flex items. And then some other properties that we use directly on flex items for individual styles.

The flex item can be at the same time a flex container.

_p.s. CSS Grid for overall page layout and Flexbox for small components._

<br>

## **Flex Container**

For an element to become a flex container:

```CSS
.flex {
    display: flex;
}
```

This will change the behavior of the flex container's direct child elements.

By default, the flex items will be aligned from left to right on the main axis, and if the flex container's width is less than the total width of the flex items, then flex items will shrink to accommodate the flex container's size.

<br>

### **justify-content and align-items**

```CSS
.flex {
    justify-content: center;
    align-items: center;

}
```

`justify-content` align the flex items from left to right along the Main Axis.

`align-items` align the items vertically along Cross Axis from top to bottom.

Most used values:

- `flex-start`, `flex-end` and `center` will position all flex items on the left or top, right or bottom, and in the center (no space between them).

- **Values only for `justify-content`:** `space-around`, `space-between`, `space-evenly` will position the flex items as the property name says.

- **Values only for `align-items`:**
  - `baseline` the bottom of the content of all items will be aligned with each other.
  - `stretch` (default value) the items will stretch from top to bottom of the flex container. Items with specified height will not stretch, only items with a minimum height specified or no height at all.

<br>

## **Flex Items**

<br>

### **flex-grow**

By default, flex items shrink proportionally when the flex container is too small. In case the flex container if bigger, we can use:

`flex-grow` property (declared on flex items) controls how much individual flex items should grow to fill the flex container.

```CSS
.item-one { flex-frow: 1; }
.item-two { flex-frow: 2; }
```

<br>

<!-- ### **flex-shrink** -->
