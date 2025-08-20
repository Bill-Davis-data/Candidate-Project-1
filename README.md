# Candidate-Project-1

**Description:** A candidate project created using provided sales data

## Data Tranformation Process

<details>
<summary>Date Table</summary>
<br/>
 
StartDate and EndDate Parameters are used to limit the size of the table.

Create columns to populate Year, Month, Month Name, etc.

<br/></details>

<details>
<summary>Open and Billed Orders</summary>
</br>

Promoted top row to headers and set proper date types

</br></details>

<details>
<summary>Voided Orders</summary>
</br>

Promoted top row to headers.

Added flag column to indicate Voided status

Set proper date types

Renamed columns to match during append

</br></details>

<details>
<summary>All Orders append</summary>
</br>

Source is an append of tables: Open and Billed Orders + Voided Orders

Removed unecessary columns and unintended future new columns by using "Remove Other Columns"

Shortened several names for clarity

Duplicated all Date/Time columns, then changed types to retain both Date and Time in separate columns

</br></details>

## DAX 

### Calculated Tables

<details>
<summary>Dashboard Target</summary>
</br>

A series of integers 1-100 to use in a slicer for setting a dynamic threshold.

</br></details>

<details>
<summary>StatusFilter</summary>
</br>

A distinct list of statuses taken from the SO Status column of All Orders append.

</br></details>

### Measures

<details>
<summary>All Orders append</summary>
</br>

Count of SO Number by Status: Value used in a matrix to show the count of orders per distributor belonging to a status selected in a slicer.

Percent Total SO Number by Status: Value used in a matrix to show the percent of total orders per distributor belonging to a status selected in a slicer.

IsUnderperforming: Used as a flag to filter a matrix of distributors according to a slicer.  Returns 1 or 0 based on a threshold set by the slicer.

Percent of Status by Year: Value used in a tooltip on a stacked bar chart.  Simply divides the number of sales orders (in context) by the total number of sales orders (with context removed).

Void Reason Rank by Year: Used to filter and return top 5 reasons for a voided order.

Void Reason Count: Value used on a stacked bar chart.  It ensures accurate filtering in context with the ranking of each void reason.

</br></details>

## Visualizations

<table>
 <tr>
  <td>
   The <strong>Sales Performance</strong> page provides two deliverables:<br>
   1. Year over year sales quantity for Sales Order Item ID "1101-0000" using the Sales Order Confirm Date.<br>
   2. Underperforming distributors in the year 2024 again using the "Sales Order Confirm Date" and just for Sales Order Item ID "1101-0000".<br>
   <br>
   "Underperforming" was not defined, so a slicer was created to allow the user to adjust this value, defaulting to the bottom 20%.
  </td>
 </tr>
 <tr>
  <td>
   <img src="https://github.com/Bill-Davis-data/Candidate-Project-1/blob/main/Assets/Sales%20Performance%20Page.png" width="642">
  </td>
 </tr>
</table>

<br/>

<table>
 <tr>
  <td>
   The <strong>Voided Orders</strong> page also provides two deliverables:<br>
   3. Percent of orders that were created in 2024 that ultimately ended up being voided.<br>
   4. Top 5 reasons for voided orders over time 2022, 2023 and 2024.<br>
   <br>
   A Sales Order Item ID was not specified for deliverable #3, so two donut charts were provided to highlight the difference in "1101-0000" alone vs. all items.<br>
   A stacked bar chart was provided to highlight the percentage by year for each status.<br>
   A matrix was provided to show the percent of total orders per distributor belonging to a status selected in a slicer.<br>
   Another slicer was provided to allow the user to filter the data by any Sales Order Item ID of their choice.  It does not interact with either donut chart.
  </td>
 </tr>
 <tr>
  <td>
   <img src="https://github.com/Bill-Davis-data/Candidate-Project-1/blob/main/Assets/Voided%20Orders%20Page.png" width="642">
  </td>
 </tr>
</table>

<br/>

<table>
 <tr>
  <td>
   The <strong>Sales by Region & Type</strong> page provides the last deliverable:<br>
   5. Any other visuals/datapoints that you think may be interesting to sales management.<br>
   <br>
   A pie chart was created to compare the sum of all units sold per region.<br>
   A related line chart was provided to further compare the information by year.<br>
   <br>
   Another pie chart was created to compare the sum of all units sold by type.<br>
   A related line chart was provided to further compare the information by year.
  </td>
 </tr>
 <tr>
  <td>
   <img src="https://github.com/Bill-Davis-data/Candidate-Project-1/blob/main/Assets/Sales%20by%20Region%20%26%20Type%20Page.png" width="642">
  </td>
 </tr>
</table>

<br/>
