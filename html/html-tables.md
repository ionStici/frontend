[&larr; Back](./README.md)

# HTML Tables

- `<table>` Create a table, will wrap all table content.

- `<tr>` (table rows) add rows.

- `<th>` (table heading) Add heading.

- `<td>` (table data) add content for each cell.

- `colspan` attribute to span columns.

- `rowspan` attribute to span rows.

- `<thead>` (table head) used to section off the table's column headings.

- `<thead scope="row" >` creates a new row header.

- `<tbody>` (table body) used to wrap large body tables.

- `<tfoot>` (table footer) to wrap the bottom part of a long table.

- We style the table border using CSS `border` property.

<br>

```html
<table>
  <thead>
    <th>Heading</th>
    <th>Heading</th>
    <th>Heading</th>
  </thead>

  <tbody>
    <tr>
      <td colspan="2">1</td>
      <td>2</td>
    </tr>
    <tr>
      <td rowspan="2">3</td>
      <td>4</td>
      <td>5</td>
    </tr>
    <tr>
      <td>
        <td>6</td>
        <td>7</td>
      </td>
    </tr>
  </tbody>

  <tfoot>
    <tr>
      <td>Footer</td>
      <td>Footer</td>
      <td>Footer</td>
    </tr>
  </tfoot>
</table>
```
