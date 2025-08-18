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

A series of integers 1-100 for use in a slicer

</br></details>

<details>
<summary>StatusFilter</summary>
</br>

A distinct list of statuses taken from the SO Status column of All Orders append.

</br></details>

### Measures
