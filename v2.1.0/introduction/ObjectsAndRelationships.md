# Objects And Relationships

 - [Overview](#markdown-header-overview)
 - [Visual](#markdown-header-visual)
 - [New Verbiage](#markdown-header-new-verbiage)
    - [Product](#markdown-header-product)
    - [Product Bundle](#markdown-header-product-bundle)
    - [Billing Option](#markdown-header-billing-option)
    - [Product State](#markdown-header-product-state)
 - [Primary Object - The Contact Object](#markdown-header-primary-object-the-contact-object)
    - [Contact Enrollment Journery Example](#markdown-header-contact-enrollment-journery-example)
 - [More Information](#markdown-header-more-information)
 - [Next Section](#markdown-header-next-section)

## Overview
At the highest level, this is the relationship between all the Core Objects operating 
within the system. On the platform level, all Objects will all have the ability to traverse 
this map to find any long distance relationship, such as a License finding it's owner Contact.

## Visual

![Object Relationship Map](../assets/ObjectRelationshipMap.png "Object Relationship Map")

---

## New Verbiage
This new system comes with some new Objects and verbiage that you will want to be familiar with.
Most of the common Objects are the same, but some of the new or changes ones are below.

 - [Product](#markdown-header-product)
 - [Product Bundle](#markdown-header-product-bundle)
 - [Billing Option](#markdown-header-billing-option)
 - [Product State](#markdown-header-product-state)


### Product
This now represents one of our services, such as Experian, AntiVirus, or even ACN. 

These are hard coded into the system and have their own means of registering, enrolling, 
activating (de/reactivating), and any other special need the Product has such as Licenses 
and checking for Authentication status.

### Product Bundle
This is a group of Products that will be offered to end users when they are signing up, such as
Platinum - which is a combination of the Experian and ACN Products.

### Billing Option
A Billing Option belongs to a Product Bundle, and defines the frequency and price of a Subscription.
It is also responsible for the Tax Categories applied to the Transaction, as well as defining the 
enrollment period and available slots if desired.

When a Contact creates a Subscription for a Product Bundle, they are really creating it for the 
Billing Option they selected for that particular Product Bundle. For example, a Subscription for
the Platinum Monthly is really a Subscription for the "Monthly" Billing Option for the "Platinum"
Product Bundle.

### Product State
When a Contact creates a new Subscription, a Product State is created for each Product available 
in the Product Bundle. These Product States manage the current status, licenses, or any other necessary 
data for the Contacts state with the Product.

For example, a Subscription to the "Platinum" Product Bundle would have two Product States.
 1. Product State: Experian
 2. Product State: ACN

Each of these states would hold information on status, activation and authentication, errors, etc.

---

## Primary Object - The Contact Object
The primary Object in Core is the Contact Object. Most all functions are done through or with
a Contact Object in context. This includes Companies, which perform their actions through a 
Point Of Contact (aka POC) Contact Object, which will hold the respective Subscription. 

Even Product Bundles, Products and Billing Options are essentially only utilized in reference
to either a Contact or their Subscription.

The only exception to this is a Batch Object, which is used by the Throttler to run a group of
Throttle Requests.

### Contact Enrollment Journery Example

Take for example the sign up process through the OEP:

 - User submits data to sign up for the "Monthly" BillingOption for the "Platinum" ProductBundle.
 - Contact is created.
 - Contact creates Credit Card.
 - Contact creates Subscription for the "Monthly" BillingOption for the "Platinum" ProductBundle.
    - Subscription creates a ProductState for each Product in ProductBundle.
 - Subscription creates a Transaction with the Contact Credit Card.
    - Transaction creates TaxCharges based on BillingOption TaxCategories and Contact zip.
 - Subscription creates an Invoice.
 - Transaction attempts an Authorization and on success Charges.
 - Subscription activates all ProductStates
    - ProductState creates License if Product requires it.  
    

---

## More Information
If you'd like to learn more about the Objects, you can see the [Core Objects Developer Documentation](../Objects.md).

---

## Next Section

[Products Explained](ProductsExplained.md)

[Back To Introduction](../Introduction.md)