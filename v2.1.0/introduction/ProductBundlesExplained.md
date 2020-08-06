# Objects And Relationships

 - [Visual](#markdown-header-visual)
 - [Overview](#markdown-header-overview)
 - [New Verbiage](#markdown-header-new-verbiage)
    - [Product](#markdown-header-product)
    - [Product Bundle](#markdown-header-product-bundle)
    - [Billing Option](#markdown-header-billing-option)
    - [Product State](#markdown-header-product-state)
 - [More Information](#markdown-header-more-information)
 - [Next Section](#markdown-header-next-section)

## Visual

![Product Bundles Example](../assets/ProductBundlesExample.png "Product Bundles Example")

## Overview
In the old version of Core, Platinum and Platinum Plus were their own Products. This has now
changed slightly - now they are considered Product Bundles.

This is because in the new v2.1.0 system, we now have a more dynamic means of mixing and matching
the various services and purchasable options that we offer.

For this to work though, there is some verbiage changes for the third party services and integrations 
that we connect our customers too, such as Experian, ACN and AntiVirus. These are now called
the Products in our system, and what was Platinum and Platinum Plus are now called the Product
Bundles.

This way we can create a Product Bundle with any number of combinations of Products.

## New Verbiage
This new system comes with some new Objects and verbiage that you will want to be familiar with.
Most of the common Objects are the same, but some of the new or changes ones are below.

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

## Next Section

[Billing Options Explained](BillingOptionsExplained)

[Back To Introduction](../Introduction)