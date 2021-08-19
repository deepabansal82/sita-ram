# CROWE

Customer Portal -Add to Cart

FD\_CMA112401\_CustPortal\_AddToCart

<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <p>Vaibhav Bansal</p>
        <p>Review of Functional Design</p>
      </th>
      <th style="text-align:left">
        <img src=".gitbook/assets/0 (2).png" alt/>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p>This is critical for:</p>
        <p>New functionality within Customer Portal for placing sales order</p>
      </td>
      <td style="text-align:left">
        <img src=".gitbook/assets/1 (2).png" alt/>
      </td>
    </tr>
  </tbody>
</table>

![](.gitbook/assets/2%20%282%29.png)

![](.gitbook/assets/3%20%282%29.png)

## Document Owners

CROWE

**Daniel Chapie**

**Vaibhav Bansal**

## Document Status

| Version | Description | Owner\(s\) | Date |
| :--- | :--- | :--- | :--- |
| 1.0 | Initial Draft | Daniel Chapie | 4/13/2021 |
| 2.0 | Updates following FD Review | Daniel Chapie | 4/25/2021 |

## Table of Contents

[Document Owners 2](https://crowe-my.sharepoint.com/personal/daniel_chapie_crowe_com/Documents/Desktop/MCS%20Internal/CMA%20Product%20Design/Customer%20Portal/FD_CMA112401_CustPortal_AddToCart_.docx#_Toc71523135)

[Document Status 2](https://crowe-my.sharepoint.com/personal/daniel_chapie_crowe_com/Documents/Desktop/MCS%20Internal/CMA%20Product%20Design/Customer%20Portal/FD_CMA112401_CustPortal_AddToCart_.docx#_Toc71523136)

[Table of Contents 3]()

[1. Introduction 4]()

[1.1. Overview of Proposed Solution 4]()

[1.2. Business Requirements 4]()

[2. Justification 5]()

[2.1. Current Functionality 5]()

[2.2. Workarounds Considered 5]()

[2.3. Alternative Enhancements Considered 5]()

[2.4. Enhancement Benefits 5]()

[3. Detailed Design Specifications 6]()

[3.1. Common Data Service \(CDS\) 6]()

[3.2. Parameters 6]()

[3.3. CMA Customer Portal – Create Order 8]()

[3.3.1. Homepage: Create Order 8]()

[3.4. CMA Customer Portal – Create new ‘Cart’ page 9]()

[3.5. ‘Online Inventory’ logic 10]()

[3.6. CMA Customer Portal – ‘Create Order’ Updates 11]()

[3.6.1. ‘Order Information’ page – Updates 11]()

[3.6.2. ‘Items’ page – Updates 13]()

[3.6.3. Review and Submit – Updates 15]()

[3.6.4. ‘Create order’ logic 16]()

[3.7. ‘Cart’ logic 17]()

[3.7.1. Retreive Price 17]()

[3.7.2. ‘Place order’ button 18]()

[3.7.3. ‘Place order’ execution logic 18]()

[4. Security 19]()

[5. Data Migration 20]()

[6. Assumptions 21]()

[6.1. Configuration 21]()

[6.2. Scope 21]()

[6.3. Cross Functional Implications 21]()

[7. Scenarios & Examples 22]()

## Introduction

### Overview of Proposed Solution

Crowe Metals Accelerator clients require the provide their customers the ability to place orders directly into D365 F&O with CMA.

Current Microsoft D365 F&O through the PowerApps suite allows for Power Portals to be created. CMA has already developed and provided an initial release of the CMA Customer Portal. To further extend the functionality provided to client’s customer base, developing functionlality to support order entry will improve e-commerce capabilities.

This enhancement provides an outline to forms and features that are necessary for the CMA Customer Portal’s ‘Create Order’.

### Business Requirements

## Justification

### Current Functionality

### Workarounds Considered

### Alternative Enhancements Considered

### Enhancement Benefits

## Detailed Design Specifications

This enhancement will provide users visibility to D365/CMA’s ‘Available inventory’ for the CMA client’s products. Below are the features documented in this enhancement:

CDS entity updates

CMA Customer Portal – Parameters

CMA Customer Portal – ‘Cart’

‘Create Order’ updates

‘Online Inventory’ updates

### Common Data Service \(CDS\)

Create new CDS entities for:

* * _LogisticsPostalAddress_

### Parameters

Add ‘CMA Customer Portal’ menu item

* * _Sales and marketing &gt; Setup &gt; CMA Customer Portal_ 

![](.gitbook/assets/4%20%282%29.png)

On the ‘General’ tab add below:

* * **Notes**

<table>
  <thead>
    <tr>
      <th style="text-align:left">Field</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Notes</th>
      <th style="text-align:left">Field Textbox</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Create order</td>
      <td style="text-align:left">Label</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">Order type</td>
      <td style="text-align:left">Dropdown</td>
      <td style="text-align:left">
        <p>Enum values:</p>
        <ul>
          <li>Journal</li>
          <li>Sales order</li>
        </ul>
      </td>
      <td style="text-align:left">Select which order type is used when record created from CMA Customer
        Portal</td>
    </tr>
    <tr>
      <td style="text-align:left">Update to sales order?</td>
      <td style="text-align:left">Toggle</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">Enable if sales journal should be updated to sales order by user in CMA
        Customer Portal</td>
    </tr>
    <tr>
      <td style="text-align:left">Note type</td>
      <td style="text-align:left">Dropdown</td>
      <td style="text-align:left"><em>DocuRef_Type</em>
      </td>
      <td style="text-align:left">Select which note type to be landed on record</td>
    </tr>
  </tbody>
</table>

![](.gitbook/assets/5%20%282%29.png)

### CMA Customer Portal – Create Order

#### Homepage: Create Order

 Add bullet to homepage feature list – **“**_**Place sales order with real-time pricing”**_

Add description of _**“Place sales order”**_

![](.gitbook/assets/6%20%282%29.png)

### CMA Customer Portal – Create new ‘Cart’ page

1. Create ‘Cart’ page with direct access from ribbon icon

Add shopping cart icon to ribbon

Create ‘Cart’ header space

* 1. Ship-To Address
  2. Order Reference
  3. Requested Receipt Date
  4. ‘Add note’ attachment icon

Create ‘PRODUCTS’ grid

* 1. Line No.
  2. Product Name
  3. Quantity
  4. Unit
  5. Weight
  6. Total Price
  7. Price Unit
  8. Total Amount
  9. ‘Add note’ dropdown

**Add** ‘Total’ that SUM all ‘Total amount’ of grid lines

**Add** ‘Place Order’ button

![](.gitbook/assets/7%20%282%29.png)

### ‘Online Inventory’ logic

Add ‘Cart’ option

**IF** ‘Add’ button for inventory grid record selected

**THEN** prompt ‘Quantity’ form  


![](.gitbook/assets/8%20%282%29.png)

**AND** select ‘Submit’ to create CMA Customer Portal ‘Cart’ record

![](.gitbook/assets/9%20%282%29.png)

### **CMA Customer Portal – ‘Create Order’ Updates**

#### **‘Order Information’ page – Updates**

![](.gitbook/assets/10%20%282%29.png)

**NAVIGATE: Homepage &gt; Create Order**

1. Remove ‘Company’ search option
   1. **Default** to ‘Company’ tied to user account

Add following fields to display from selected ‘Delivery address’

| Field name | Source | Notes |
| :--- | :--- | :--- |
| Street Name | LogisticsPostalAddress\_Street | Character limit = None; Type = Alphanumeric |
| City | LogisticsPostalAddress\_City | Character limit = None; Type = Alphabetic |
| State | LogisticsPostalAddress\_State | Character limit = None; Type = Alphabetic |
| Country | LogisticsPostalAddress\_CountryRegionId | Character limit = 3; Type = Alphabetic |
| Zip Code | LogisticsPostalAddress\_ZipCode | Character limi = None; Type = Integer |

**Remove** ‘Requested Ship Date’

**Remove** ‘Customer ID’

* 1. Should always default to ‘Customer account’ linked to user account

**Remove** ‘Requisition Number’ field

**Remove** ‘Price List’

* 1. Add D365 parameter to default “Price list” for Customer Portal _Create Order_

**Modify** ‘Delivery address’ to dropdown

* 1. LOOKUP D365’s ‘Customer account’ addresses with ‘Purpose’ = **Delivery**

![](.gitbook/assets/11%20%282%29.png)

#### **‘Items’ page – Updates**

![](.gitbook/assets/12%20%282%29.png)

1. **Remove** ‘Line status’
2. **Remove** ‘Total amount’
3. **Remove** price values
   1. ‘Price per unit’
   2. ‘Total amount’
4. **Add** ‘Notes’
5. **‘Add items’ function changes:**

![](.gitbook/assets/13%20%282%29.png)

* 1. **Lookup records** form changes
     1. **Add** filters for:
        1. ‘Form/Shape’
        2. ‘Commodity’
        3. ‘Grade/Alloy’

           ![](.gitbook/assets/14%20%282%29.png)

#### Review and Submit – Updates

‘Cart’ form is the same as described in Section 3.4

1. Change “Review and Submit” tab and relabel to “**Cart**”
2. Display header values and allow user to edit \(stored from ‘Order Information’ page\)
   1. ‘Ship-To Address’
   2. ‘Order Reference’
   3. ‘Requested Delivery Date’
   4. ‘+Add note’ button
3. **Add** following fields to ‘PRODUCTS’ the grid
   1. ‘Total price’
   2. ‘Price unit’
   3. ‘Total amount’
   4. Details dropdown for ‘Add notes’
4. **Add** footer value for ‘TOTAL’ that SUMS grid lines for ‘Total amount’ values
5. **Add** ‘Place Order’ button
   1. _Disable_ when blank or $0 price is populated

![](.gitbook/assets/15%20%282%29.png)

_NOTE: Unable to provide screenshots due to below error – Update required following resolution of error when selecing ‘Next’ on the ‘Order Information’_

![](.gitbook/assets/16%20%282%29.png)

#### ‘Create order’ logic

**IF** ‘Place order’ button selected in ‘Cart’

**THEN** process ‘Create order’ in D365

**AND** find ‘Order type’ parameter setting \(section 3.2\) to populate ‘Order type’ value on SalesTable

**AND** find ‘Note type’ parameter to assign to new text in ‘Add notes’ button

**ELSE** do not process ‘Create order’ logic

### ‘Cart’ logic

#### Retreive Price

MSFT ‘Create order’ logic when user accesses ‘Review and submit’ page, D365 SalesTable and SalesLine table records are created

**IF** user opens ‘Cart’ page in CMA Customer Portal

**AND** SalesTable and SalesLine records created

**THEN** retrieve following fields in CDS entities and map to the CMA Customer Portal ‘Cart’

* * SalesLine\_cmaSalesPrice
  * SalesLine\_cmaPriceUOM
  * SalesLine\_cmaNetAmount

![](.gitbook/assets/17%20%282%29.png)

#### ‘Place order’ button

**IF** ‘Total price’ and ‘Total amount’ for all lines in ‘Cart’ are &gt; $0.00

**THEN** enable ‘Place order’ button

**ELSE** disable ‘Place order’ button

![](.gitbook/assets/18%20%282%29.png)

####  ‘Place order’ execution logic

**IF** ‘Place order’ button is selected

**AND** SalesTable record has ‘Order type’ = **Journal**

**AND** CMA Customer Portal parameter ‘Update to sales order?’ = **Yes** \(section 3.2\)  


**THEN** update SalesTable\_OrderType = **Sales order**

**AND** ‘Confirm sales order’ \(see below\)  


**ELSE IF** SalesTable record has ‘Order type’ = **Sales order**

**THEN** ‘Confirm sales order’ \(see below\)

## Security

_Does this design create new Forms or Reports?_

Yes ☐

No ☒

_If yes, new security privileges need to be created for Inquire \(read\) and Maintain \(edit\) access._

_Indicate the duties or roles which should have access and the development team will create new Privileges and associate them._

| Form/Report | Access Level | Duty\(s\)/Role\(s\) |
| :--- | :--- | :--- |
|  | Inquire \(read\) |  |
| Maintain \(edit\) |  |  |

## Data Migration

**New fields**

_Does this design add new fields\(s\) to a table which will require data import?_

Yes ☐

No ☒

_If yes, identify the associated data entity\(s\) which should be populated_

| New Field Name | Data Entity Name |
| :--- | :--- |
|  |  |
|  |  |

**New tables**

_Does this design add new table\(s\) which will require data import?_

Yes ☐

No ☒

_If yes, list the tables below and new data entity\(s\) will be created for each_

| New Table Name | New Data Entity Name |
| :--- | :--- |
|  |  |
|  |  |

## Assumptions

### Configuration

1. Parameter settings
2. Data configurations
3. Field values

### Scope

1. This enhancement is limited to xxxxx and does not include yyyyy

### Cross Functional Implications

## Scenarios & Examples

